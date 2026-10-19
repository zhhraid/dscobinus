# Notebooks

Penamaan: `NN_topik.ipynb`, berurutan sesuai alur kerja.

| Notebook | Tujuan |
|---|---|
| `99_final_submission.ipynb` | **Sudah ada.** Notebook yang dikumpulkan ke panitia: EDA → Preprocessing → Pemilihan Model → Evaluasi → Submission |
| `97_submission_7.ipynb` | Versi notebook yang menghasilkan `submission_7.csv` (threshold OOF 0,38) |
| `98_submission_6.ipynb` | Versi notebook yang menghasilkan `submission_6.csv` (tautan lintas modul + fitur kohort + ensemble). Disimpan agar submission 6 tetap bisa direproduksi bila dipilih sebagai final |
| `01_eda.ipynb` dst. | Belum ada. Tempat eksperimen lanjutan sebelum dipindahkan ke notebook final |

File keluaran bernama `submission_<nomor>.csv`; nomornya diatur lewat `SUBMISSION_NO` di sel setup. Lama Run All ≈ 8 menit (4 core).

## Aturan untuk `99_final_submission.ipynb`

- Berdiri sendiri: memuat EDA, Preprocessing, Pemilihan Model, Evaluasi Model dalam satu file, tanpa import dari `src/`.
- Baca data tanpa direktori: `pd.read_csv("train.csv")`.
- Seed tetap; **Restart & Run All** harus sukses dan menghasilkan CSV yang sama dengan yang disubmit.

Notebook eksplorasi (01–04) boleh membaca dari `../data/raw/`.
