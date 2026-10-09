# Log Submission

Maks. **3 submission/hari**. Saat skor seri, tim dengan submission **paling sedikit** menang — submit seperlunya.

Nama file: `submission_N.csv`. Kolom: `id,at_risk`.

| No | Tanggal | File | Notebook / eksperimen | Model & perubahan utama | F1 CV lokal | F1 Public LB | Catatan |
|---|---|---|---|---|---|---|---|
| 1 | 3 Okt 2026 (disubmit) | `submission_1.csv` | `notebooks/99_final_submission.ipynb` (versi awal, sudah ditimpa versi 2) | Blend LightGBM + XGBoost + CatBoost, 5-fold, fitur asli + pembersihan kategori (`GGG`→`M07`), threshold 0,37 | 0,7761 (AUC 0,8469) | 0,78704 | F1 @0,50 = 0,7632 |
| 2 | 3 Okt 2026 (disubmit) | `submission_2.csv` | `notebooks/99_final_submission.ipynb` (versi 2, sudah ditimpa versi 3) | Sama seperti no. 1 + 4 fitur tautan mahasiswa mengulang modul (profil sama + urutan baris), threshold 0,40 | 0,7797 (AUC 0,8533) — terlalu optimis, lihat catatan | 0,79227 | CV dihitung dengan fitur train yang lebih tajam daripada test, jadi angkanya tidak sebanding dengan no. 3. Fitur memakai urutan `id` dan data presentasi berikutnya |
| 3 | 3 Okt 2026 (dibuat, **belum disubmit**) | `submission_3.csv` | `notebooks/99_final_submission.ipynb` | Sama seperti no. 2, dengan dua perbaikan: test dikenali sebagai dua potongan terurut (id 26092–29347 dan 29348–32593), dan fitur tautan train dihitung dalam kondisi yang sama dengan test. Threshold 0,36 | 0,7779 (AUC 0,8504) — sebanding dengan kondisi test | | 402 prediksi berubah dari no. 2 (373 jadi berisiko), sebagian besar karena threshold turun |

## Final submission terpilih

| File | Alasan dipilih |
|---|---|
| | |
