# Log Submission

Maks. **3 submission/hari**. Saat skor seri, tim dengan submission **paling sedikit** menang — submit seperlunya.

Nama file: `submission_N.csv`. Kolom: `id,at_risk`.

| No | Tanggal | File | Notebook / eksperimen | Model & perubahan utama | F1 CV lokal | F1 Public LB | Catatan |
|---|---|---|---|---|---|---|---|
| 1 | 3 Okt 2026 (disubmit) | `submission_1.csv` | `notebooks/99_final_submission.ipynb` (versi awal, sudah ditimpa versi 2) | Blend LightGBM + XGBoost + CatBoost, 5-fold, fitur asli + pembersihan kategori (`GGG`→`M07`), threshold 0,37 | 0,7761 (AUC 0,8469) | 0,78704 | F1 @0,50 = 0,7632 |
| 2 | 3 Okt 2026 (disubmit) | `submission_2.csv` | `notebooks/99_final_submission.ipynb` (versi 2, sudah ditimpa versi 3) | Sama seperti no. 1 + 4 fitur tautan mahasiswa mengulang modul (profil sama + urutan baris), threshold 0,40 | 0,7797 (AUC 0,8533) — terlalu optimis, lihat catatan | 0,79227 | CV dihitung dengan fitur train yang lebih tajam daripada test, jadi angkanya tidak sebanding dengan no. 3. Fitur memakai urutan `id` dan data presentasi berikutnya |
| 3 | 3 Okt 2026 (dibuat, **belum disubmit**) | `submission_3.csv` | `notebooks/99_final_submission.ipynb` (versi 3, sudah ditimpa versi 4; masih ada di commit `b4fd3bf`) | Sama seperti no. 2, dengan dua perbaikan: test dikenali sebagai dua potongan terurut (id 26092–29347 dan 29348–32593), dan fitur tautan train dihitung dalam kondisi yang sama dengan test. Threshold 0,36 | 0,7779 (AUC 0,8504) — sebanding dengan kondisi test | | 402 prediksi berubah dari no. 2 (373 jadi berisiko), sebagian besar karena threshold turun |
| 4 | 9 Okt 2026 (disubmit) | `submission_4.csv` | `notebooks/99_final_submission.ipynb` | Model sama (blend LightGBM + XGBoost + CatBoost). Tiga perubahan: (1) 145 baris train yang kode modulnya terselip dikembalikan ke `M07`; (2) kandidat tautan hanya dicari di dalam himpunan yang sama (train / test A / test B) karena data dibagi per mahasiswa, dan train diberi perlakuan setara lewat potongan semu per gugus mahasiswa; (3) fitur `order_pos`. Threshold 0,38 dari kurva F1 yang dihaluskan | 0,7790 (AUC 0,8529); maksimum mentah 0,7797 @0,40 — sebanding dengan no. 3 | 0,80018 | 232 prediksi berubah dari no. 3 (198 jadi tidak berisiko, sebagian besar karena threshold naik) dan 268 dari no. 2. Dari 226 baris test yang punya penerus dalam potongannya, 99,6% diprediksi berisiko (no. 2: 80%, no. 3: 93%); di train kelompok seperti ini ±84–92% berisiko. Selisih CV terhadap no. 3 kecil (+0,001), jadi kenaikan di LB tidak dijamin. Hasil: LB naik +0,0079 dari no. 2 |
| 5 | 16 Okt 2026 (disubmit) | `submission_5.csv` | `notebooks/99_final_submission.ipynb` | (1) Tautan **lintas modul**: mahasiswa yang sama di modul lain (bersamaan atau berurutan, terutama `M03` dengan `M04`/`M05`/`M06`), hanya pada 19 pasangan blok yang lolos uji rantai-vs-acak (z ≥ 4); gugus & potongan semu ikut memakai tautan ini. (2) 15 fitur relatif kohort (peringkat persentil dalam modul-presentasi, `vle_imputed`, rasio aktivitas akhir). (3) Validasi Stratified**Group** 5-fold per gugus mahasiswa. (4) LightGBM dengan hyperparameter Optuna (45 percobaan, di luar notebook). (5) Blend LightGBM + XGBoost (CatBoost dibuang), masing-masing 3 seed. Threshold 0,38 | 0,7818 (AUC 0,8544, log loss 0,4623); maksimum mentah 0,7821 @0,37 | 0,79012 | Pembanding adil (skema fold yang sama, fold seed 123 & 2024 yang tidak dipakai tuning): pipeline no. 4 F1 0,7794 / 0,7791, AUC 0,8526 / 0,8527 → pipeline no. 5 F1 0,7819 / 0,7811, AUC 0,8549 / 0,8549. Kenaikan ±0,002–0,0025 F1, lebih kecil dari derau public LB (±0,01 untuk ±1.950 baris), jadi LB bisa naik atau turun sedikit. 235 prediksi berubah dari no. 4 (121 jadi berisiko) |
| 6 | 19 Okt 2026 (disubmit) | `submission_6.csv` | `notebooks/99_final_submission.ipynb` | Ensemble rata-rata dua pipeline: A = pipeline no. 5 (LGB+XGB, semua fitur), B = konfigurasi no. 4 (tanpa fitur lintas modul & kohort, LGB+XGB+CAT). Threshold 0,38 | 0,7810 (AUC 0,8545); fold seed 123 / 2024: AUC 0,8551 / 0,8551 (A 0,8549 / 0,8547, B 0,8526 / 0,8527) | 0,79357 | Prediksi berada di antara no. 4 dan no. 5 (127 beda dari no. 4, 118 dari no. 5). Semua varian berbeda < 0,001 F1 di CV, jadi selisih LB 4 vs 5 (−0,010) adalah derau public LB (±70 baris berubah di ±1.950 baris public). Pseudo-labelling (ambang 0,1/0,9 dan 0,2/0,8) juga dicoba: ±0,001, tidak konsisten antar-fold, tidak dipakai |
| 7 | 20 Okt 2026 (disubmit) | `submission_7.csv` | `notebooks/99_final_submission.ipynb` | Pipeline no. 4 (skor public tertinggi) tanpa perubahan fitur/model; validasi silang diulang pada 5 pembagian fold (seed 42, 7, 123, 2024, 99) → prediksi test rata-rata 25 model per algoritma; threshold 0,38 dari rata-rata kurva F1 kelima pembagian | 0,7787 (rata-rata 5 pembagian; AUC 0,8526) | 0,79981 | Hanya 31 prediksi berubah dari no. 4. Dengan 1 pembagian fold, 102 baris test berganti label tergantung pembagiannya; no. 7 memakai suara rata-rata. Tujuan: versi no. 4 yang lebih stabil, bukan model baru |
| 8 | 21 Okt 2026 (disubmit) | `submission_8.csv` | `notebooks/96_submission_8.ipynb` | Sama dengan no. 7, tetapi threshold dipilih dengan aturan plug-in F1 harapan pada probabilitas test (tanpa label): 0,39 | 0,7790 @0,39 (rata-rata 5 pembagian); F1 harapan test 0,7815 vs 0,7814 @0,38 | 0,79… (dilaporkan "masih 0,79") | 63 baris paling meragukan berubah dari berisiko → tidak berisiko dibanding no. 7 (64 dari no. 4). Secara teori setara dengan no. 7; peluang naik/turun di public sama |
| 9 | 29 Okt 2026 (disubmit) | `submission_9.csv` | `notebooks/95_submission_9.ipynb` | No. 7 + **LightGBM per modul** (satu model per `code_module`), digabung 0,7 × blend + 0,3 × per modul. Threshold 0,38 | 0,7798 (rata-rata 5 pembagian; AUC 0,8533) vs no. 7 0,7787 / 0,8526 | 0,79540 | Perbaikan pertama yang konsisten pada pipeline no. 4: naik di **kelima** pembagian fold (AUC +0,0005 s.d. +0,0010, F1 +0,0007 s.d. +0,0013). 104 prediksi berubah dari no. 7, 109 dari no. 4. Tetap kecil dibanding derau public (±0,01) |

## Eksperimen yang tidak dipakai (19 Okt, CV fold seed 123, grup per mahasiswa)

Pembanding: blend LightGBM + XGBoost pipeline no. 5 → AUC 0,8549, F1 0,7815.

| Percobaan | AUC | F1 | Kesimpulan |
|---|---|---|---|
| + ExtraTrees (bobot 0,15) | 0,8550 | 0,7817 | derau |
| + RandomForest (0,15) | 0,8548 | 0,7816 | derau |
| + HistGradientBoosting (0,15) | 0,8549 | 0,7811 | derau |
| + MLP 3 seed (0,15) | 0,8550 | 0,7809 | derau |
| Pseudo-label test (0,1/0,9 dan 0,2/0,8) | 0,8550–0,8556 | 0,7808–0,7826 | tidak konsisten antar-fold |
| Probabilitas pasangan lintas modul (stacking) | +0,0003 | ±0 | tidak sebanding dengan kerumitannya |

Semua varian berada dalam ±0,001 F1: model sudah jenuh pada informasi yang tersedia di data 4 minggu pertama.

Audit kebocoran (20 Okt), semuanya negatif:
- Urutan baris test tidak membawa informasi label: korelasi prediksi antar-tetangga di test (0,06–0,09) setara dengan train (0,06–0,08).
- Tidak ada imputasi yang bergantung label (nilai imputasi sama untuk kedua kelas).
- Tautan mahasiswa test ↔ train (yang labelnya diketahui) tidak nyata: rasio pasangan dekat/jauh kurva untuk test–train (0,30 mengulang; 0,08 lintas modul) setara dengan test A–test B (0,27; 0,07), yang merupakan tabrakan acak. Jadi data benar-benar dibagi per mahasiswa.

Audit lanjutan (21 Okt), juga negatif:
- Tautan mengulang dengan lompatan percobaan selain +1: +0 tidak nyata (rasio dekat/jauh 0,028 ≈ acak); +2 nyata (0,178; 53 pasangan di train, pendahulu 83% berisiko), tetapi **0 baris test** punya tautan +2 di dalam potongannya.
- Latih ulang pada 100% train (iterasi = rata-rata early stopping × 1,2, 3 seed) dibanding rata-rata model fold, diuji pada 5 holdout 20%: AUC +0,0002, F1@0,38 −0,0005. Tidak dipakai.

## Final submission terpilih

| File | Notebook | Alasan dipilih |
|---|---|---|
| `submission_7.csv` | `notebooks/99_final_submission.ipynb` | Public setara terbaik (0,79981 vs 0,80018 no. 4), prediksi paling stabil (rata-rata 5 pembagian fold), notebook terbukti menghasilkan CSV identik |
| `submission_6.csv` | `notebooks/98_submission_6.ipynb` | CV tertinggi (F1 0,7810–0,7818, AUC 0,8545); isinya berbeda dari no. 7 sehingga menutup kemungkinan private berbeda arah |
