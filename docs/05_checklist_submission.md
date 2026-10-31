# Checklist

## Sebelum setiap submission ke Kaggle

- [ ] Skor CV lokal (F1) lebih baik / ada hipotesis jelas yang mau diuji
- [ ] Kolom persis `id,at_risk`, 6.502 baris, `id` 26092–32593, tanpa duplikat
- [ ] `at_risk` berisi 0/1 (bukan probabilitas)
- [ ] Nama file `submission_N.csv` (pilihan tim; format dari panitia saat TM: `[Nama Tim]_submission N.csv`)
- [ ] Disubmit dari **akun ketua**
- [ ] Belum melewati 3 submission hari ini
- [ ] Dicatat di `submissions/README.md` (CV, public LB, commit/notebook asal)

## Kepatuhan aturan

- [ ] Tidak ada data eksternal
- [ ] Tidak ada AutoML
- [ ] Tidak ada model pre-trained
- [ ] Tidak ada perubahan label manual
- [ ] Semua kode Python

## Notebook final (wajib jika masuk top 15)

- [ ] Memuat: EDA → Preprocessing → Pemilihan Model → Evaluasi Model
- [ ] `pd.read_csv("train.csv")` / `"test.csv"` / `"sample_submission.csv"` **tanpa direktori**
- [ ] Tidak meng-import dari `src/` — semua kode ada di dalam notebook (panitia hanya menerima `.ipynb` + `.csv`)
- [ ] Seed tetap di semua tempat (numpy, CV split, model)
- [ ] **Restart kernel → Run All** sukses tanpa error, di folder bersih berisi hanya notebook + 3 CSV
- [ ] CSV hasil Run All **identik** dengan CSV yang dipilih di Kaggle
- [ ] Output sel tersimpan di file `.ipynb`
- [ ] Lama run masuk akal untuk di-run ulang panitia

## Pengumpulan (deadline 1 Nov 2026, 23:59 WIB)

- [ ] Satu folder Google Drive berisi notebook final + CSV
- [ ] Akses link: siapa saja yang punya link bisa melihat
- [ ] Link diisi ke Google Form panitia
- [ ] **Satu** final submission sudah dipilih di Kaggle sebelum babak penyisihan ditutup (31 Okt) — pilihan tim: no. 6
- [ ] Nama CSV di folder Drive sama dengan file yang di-upload ke Kaggle (isinya identik dengan keluaran notebook)

## Persiapan final (jika lolos)

- [ ] Registrasi ulang + pas foto (latar polos, setengah badan)
- [ ] PPT mengikuti rubrik: Analisis & Justifikasi Model 40%, Prescriptive Insight 35%, Penyampaian & Visualisasi 25%
- [ ] Ada bagian rekomendasi/tindakan konkret, bukan hanya hasil prediksi
- [ ] Latihan: 15 menit presentasi + 10 menit tanya jawab, bahasa Indonesia
