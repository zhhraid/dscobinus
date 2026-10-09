# Aturan Kompetisi — DSCO 2026

Sumber: `Guidebook DSCO 2026.pdf` (folder ini) + halaman Rules di Kaggle.
Tema: **Beyond the Data Horizon: Decoding the Future of Education**.
Penyelenggara: Data Science Club (DSC) Binus University.

## Ringkasan 1 menit

| Hal | Ketentuan |
|---|---|
| Tugas | Klasifikasi biner: prediksi `at_risk` (0/1) per mahasiswa |
| Metrik | **F1 score** |
| Limit submission | **3 per hari** per tim |
| Leaderboard | Public 30% / **Private 70%** dari data test |
| Penentu finalis | **100% private leaderboard**, top 10 lolos |
| Seri (skor sama) | Dilihat **jumlah submission paling sedikit** + kualitas notebook |
| Bahasa | Python saja |
| Dilarang | Data eksternal, AutoML, model pre-trained, ubah label manual |

## Yang DILARANG

1. **Dataset eksternal** — di semua tahap, termasuk untuk feature engineering.
2. **AutoML** (mis. AutoGluon, H2O AutoML, PyCaret, auto-sklearn, FLAML, TPOT).
3. **Model pre-trained apa pun** — model harus dilatih sendiri dari dataset panitia.
4. **Mengubah label secara manual** pada dataset.
5. Bahasa selain Python.
6. Submit dari lebih dari satu akun — hanya **akun ketua** yang boleh submit.
7. Kerja sama dengan tim lain / pihak luar; plagiarisme antar tim.
8. Mengirim notebook `.ipynb` yang masih error.

## Yang BOLEH

- Library Python apa saja selama bukan AutoML (sklearn, LightGBM, XGBoost, CatBoost, PyTorch, Optuna, dll.).
- **Augmentasi data** dari dataset panitia sendiri.
- **Pseudo-labelling** pada data test.
- Memakai referensi dari luar (paper, artikel, kode contoh) — asal bukan *data* luar.

## Tim & akun Kaggle

- Nama tim di Kaggle **harus sama** dengan nama tim saat registrasi, tanpa unsur SARA.
- **Seluruh anggota** wajib tergabung (merge) dalam 1 tim di Kaggle.
- Hanya **1 akun (ketua)** yang melakukan submission.
- Anggota tim tidak boleh diganti selama kompetisi.

## Format submission (Kaggle)

- File `.csv`, 2 kolom: ID dan prediksi. Ikuti persis `sample_submission.csv`: **`id,at_risk`**.
- Penamaan file: `[Nama Tim]_submission 1.csv`, `[Nama Tim]_submission 2.csv`, dst.

## Kewajiban top 15 private leaderboard

Peringkat 1–10 = finalis, 11–15 = cadangan (stand by, menggantikan jika ada finalis yang gugur).

Semua 15 tim wajib mengumpulkan **link Google Drive** lewat Google Form panitia, berisi:

1. Notebook final `.ipynb` yang **sudah dijalankan** (output tersimpan).
2. File `.csv` yang dipakai untuk penentuan leaderboard.

Syarat notebook:

- Minimal memuat **EDA, Preprocessing, Pemilihan Model, Evaluasi Model**. Urutan bebas.
- **Harus bisa Run All tanpa error.**
- Path data: baca CSV **tanpa direktori**, seolah file ada di folder yang sama dengan notebook → `pd.read_csv("train.csv")`.
- Panitia akan **melihat log run sebelumnya dan me-run ulang**. Skor notebook yang jauh berbeda dari skor submission = indikasi kecurangan → pastikan **reproducible** (set semua seed).
- Kode **tidak boleh diubah** setelah babak penyisihan; yang dipresentasikan = yang dikumpulkan.

Deadline form: **1 November 2026, 23:59 WIB**. Terlambat = gugur.

## Babak final (27 November 2026)

- 10 finalis presentasi di depan juri. Jabodetabek **wajib onsite** (Binus Anggrek, Kemanggisan); luar Jabodetabek boleh **online via Zoom**.
- Waktu: 5 menit persiapan, **15 menit presentasi**, 10 menit tanya jawab.
- PPT boleh bahasa Indonesia/Inggris; **penyampaian wajib bahasa Indonesia**. Tidak ada template PPT.
- Hadir 30 menit sebelum mulai; pakaian rapi (disarankan almamater).
- Finalis wajib registrasi ulang + unggah pas foto (latar polos, setengah badan, wajah di tengah).

### Rubrik penilaian presentasi

| Aspek | Bobot | Isi |
|---|---|---|
| Analisis & Justifikasi Model | 40% | Kejelasan metode dan alasan pemilihan model |
| Prescriptive Insight | 35% | Rekomendasi / tindakan berbasis hasil prediksi — tidak berhenti di prediksi |
| Penyampaian & Visualisasi | 25% | Kejelasan presentasi dan tampilan visual |

## Hadiah

Juara 1 Rp 1.800.000 · Juara 2 Rp 1.000.000 · Juara 3 Rp 700.000

## Narahubung

- Floren: 0812-7127-2583
- Ghiza: 0822-4680-1302
- Instagram: @dscolympiads, @dsclub.binus
- Pertanyaan baru: lewat grup WhatsApp resmi atau contact person.
