# Dataset

Lokasi: `data/raw/`. Satu baris = satu mahasiswa pada satu modul-presentasi (struktur mirip data learning analytics universitas terbuka).

| File | Baris | Kolom | Isi |
|---|---|---|---|
| `train.csv` | 26.086 | 64 | 62 fitur + `id` + target `at_risk` |
| `test.csv` | 6.502 | 63 | Sama, tanpa `at_risk` |
| `sample_submission.csv` | 6.502 | 2 | `id,at_risk` |

- `id` train: 1–26091, test: 26092–32593.
- Target `at_risk`: 1 = 13.753 (52,7%), 0 = 12.333 (47,3%) → **cukup seimbang**.
- Tidak ada `NaN`, tapi ada missing tersamar (lihat bawah).
- 4 baris train duplikat penuh (selain `id`).

## Kelompok fitur

| Kelompok | Kolom |
|---|---|
| Identitas modul | `code_module`, `code_presentation`, `module_presentation_length` |
| Demografi | `gender`, `region`, `highest_education`, `imd_band`, `age_band`, `disability` |
| Riwayat studi | `num_of_prev_attempts`, `studied_credits`, `registration_days_from_start` |
| Asesmen — jumlah | `assessments_due_total`, `assessments_due_Assessment_1/2`, `submitted_count`, `late_submission_count`, `submitted_Assessment_1/2`, `assessment_completion_rate`, `assessment_completion_rate_Assessment_1/2`, `no_submission_by_cutoff`, `has_score` |
| Asesmen — nilai | `avg_score`, `median_score`, `max_score`, `min_score`, `score_std`, `score_trend`, `score_Assessment_1/2`, `weighted_score_total`, `weighted_score_Assessment_1/2` |
| Asesmen — keterlambatan | `avg/median/max/min_submission_delay`, `submission_delay_Assessment_1/2` |
| Aktivitas VLE — volume | `interaction_volume`, `active_days`, `active_weeks`, `unique_sites`, `unique_activity_types`, `avg_daily_interactions`, `max_daily_interactions`, `interaction_variability`, `avg_interactions_per_active_day`, `avg_interactions_per_active_week` |
| Aktivitas VLE — waktu | `first_activity_day`, `last_activity_day`, `activity_span_days`, `week1..4_interactions`, `early_interactions`, `late_interactions`, `late_to_early_interactions_ratio`, `interaction_trend` |

## Temuan kualitas data (hasil profiling awal)

1. **Kategori tidak konsisten penulisannya**
   - `region`: `Region1`, `region2`, `Region 3`, `Region 10` (campur huruf besar/kecil dan spasi) → normalisasi sebelum encoding.
   - `highest_education`: train berisi `A Level`; **test berisi juga `A level`** yang tidak ada di train → samakan kapitalisasi.
2. **Missing tersamar**
   - `imd_band`: nilai `-` dan `?`. Band `10-20%` tidak muncul sama sekali — cek apakah itu yang tertulis sebagai `-`/`?`.
   - `highest_education`: nilai `-`.
3. **Kategori hanya ada di test**: `code_module = GGG` (372 baris) muncul di test, tidak ada di train (train: `M01`–`M07`). Ini adalah **`M07` yang belum disandikan**, buktinya:
   - Kombinasi presentasi dan panjang modulnya persis sama dengan `M07` (`P12`/261, `P21`/241, `P22`/269).
   - Rasio baris test/train `M07` hanya 0,10 (modul lain ≈0,25); setelah `GGG` digabung menjadi 0,30.
   - Di test, baris `M07` seluruhnya `A level` dan baris `GGG` tidak ada yang `A level`; jika digabung, proporsinya (≈33%) cocok dengan `M07` di train (≈35%).

   Di preprocessing `GGG` dipetakan ke `M07`.
4. **Kolom konstan** di train: `submitted_Assessment_1`, `submitted_Assessment_2` (1 nilai unik) → tidak informatif.
5. **Nilai hasil imputasi**: saat `has_score = 0`, kolom nilai dan delay terisi satu angka yang sama (`avg_score` = 77, `score_Assessment_1` = 70, delay = -1). Jadi angka itu bukan nilai asli; `has_score` dan `no_submission_by_cutoff` adalah penandanya.
6. **Fitur redundan**: banyak kolom skor/delay identik saat hanya ada 1 asesmen (`avg = median = max = min`).

7. **Kode modul terselip di train** (ditemukan 9 Okt): menurut urutan `id`, 144 baris bertuliskan `M04_P22` (id 25937–26080) berada di tengah blok `M07_P22`, dan 1 baris `M05_P12` (id 24112) di dalam blok `M07_P12`. Cirinya cocok dengan `M07` (SKS ≈33, belum ada nilai, sedikit aktivitas), jadi di preprocessing dikembalikan ke `M07`. Test tidak punya sisipan seperti ini.
8. **Data dibagi per mahasiswa** (ditemukan 9 Okt): test terdiri dari dua potongan terurut (A: id 26092–29347, B: 29348–32593). Baris yang merupakan mahasiswa yang sama (mis. mengulang modul) hampir selalu berada di himpunan yang sama — train dengan train, A dengan A, B dengan B. Akibatnya: (a) tautan antarbaris cukup dicari di dalam himpunan yang sama; (b) label train **tidak pernah** tersedia untuk "pasangan" sebuah baris test, jadi gagasan memakai label pasangan sebagai fitur tidak bisa dipakai (di train terlihat menaikkan skor, tetapi itu tidak berlaku untuk test).
9. **Tidak ada pergeseran distribusi train–test** pada fitur asli: model pembeda train-vs-test hanya mencapai AUC 0,50.

10. **Baris VLE hasil imputasi** (ditemukan 30 Okt): 14,3% baris train (3.737) dan 14,6% baris test punya kolom aktivitas VLE yang tidak konsisten secara aritmetika (mis. `week1..4_interactions` tidak berjumlah `interaction_volume`, `activity_span_days` ≠ `last - first`). Semuanya berisi **satu set angka yang sama persis** (volume 182, 10 hari aktif, 20 situs, …) — isian panitia untuk mahasiswa tanpa aktivitas VLE. 95,2% baris ini berisiko (M07: 64–77%). Model sudah menangkapnya (99,6% diprediksi berisiko), jadi tidak ada tambahan skor, tetapi temuan ini layak dipresentasikan.
11. **Pengecekan kebocoran lain (30 Okt), hasilnya negatif:** nilai isian VLE dan nilai asesmen tidak berbeda per label; label baris yang bersebelahan menurut `id` hampir tidak berkorelasi (±0,03, hanya efek per modul); data di zip Kaggle identik dengan `data/raw/` (hanya beda akhir baris CRLF). Pseudo-labelling dan tautan mahasiswa di modul lain tidak menaikkan CV secara berarti.

Poin 1–3 jika dibiarkan akan membuat distribusi train dan test tampak berbeda padahal tidak, jadi kerjakan di tahap preprocessing paling awal.
