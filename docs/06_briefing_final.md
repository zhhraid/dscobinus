# Briefing Babak Final DSCO 2026 · Kepepet Deadline

Semua yang perlu diketahui tim untuk presentasi final 27 November 2026: proyek, angka kunci, notebook, struktur PPT, naskah, dan bank tanya jawab.

Tim: **Zhahra Idhya Astwoti** dan **Ridho Dwi Syahputra**, Universitas Andalas.
Judul: *Deteksi Dini Mahasiswa Berisiko Dropout dari Empat Minggu Pertama — dari skor risiko ke tindakan tutor yang tepat waktu.*

---

## Daftar isi

1. [Format babak final dan rubrik](#1-format-babak-final-dan-rubrik)
2. [File dan tautan penting](#2-file-dan-tautan-penting)
3. [Kartu contekan: angka yang wajib hafal](#3-kartu-contekan-angka-yang-wajib-hafal)
4. [Proyek dalam satu halaman](#4-proyek-dalam-satu-halaman)
5. [Data dan kualitas data](#5-data-dan-kualitas-data)
6. [Temuan EDA](#6-temuan-eda)
7. [Pemodelan](#7-pemodelan)
8. [Business insight](#8-business-insight)
9. [Notebook dan submission](#9-notebook-dan-submission)
10. [Struktur PPT final (23 slide)](#10-struktur-ppt-final-23-slide)
11. [Naskah presentasi 13 menit](#11-naskah-presentasi-13-menit)
12. [Bank tanya jawab](#12-bank-tanya-jawab)
13. [Asal-usul angka: mana yang wajib dicek ulang](#13-asal-usul-angka-mana-yang-wajib-dicek-ulang)
14. [Checklist hari-H](#14-checklist-hari-h)
15. [Glosarium singkat](#15-glosarium-singkat)

---

## 1. Format babak final dan rubrik

| Item | Ketentuan |
|---|---|
| Tanggal | 27 November 2026 |
| Lokasi | Binus Anggrek (Kemanggisan). Tim luar Jabodetabek boleh online lewat Zoom |
| Waktu | 5 menit persiapan · **15 menit presentasi** · 10 menit tanya jawab |
| Bahasa | PPT boleh Indonesia/Inggris; **penyampaian wajib bahasa Indonesia** |
| Kehadiran | 30 menit sebelum mulai; pakaian rapi (disarankan almamater) |
| Aturan penting | Kode tidak boleh diubah setelah penyisihan: yang dipresentasikan = yang dikumpulkan |

Rubrik penilaian (sumber: `docs/01_aturan_kompetisi.md`, Guidebook):

| Aspek | Bobot | Yang dinilai | Slide yang menjawab |
|---|---|---|---|
| Analisis & Justifikasi Model | **40%** | Kejelasan metode dan alasan pemilihan model | 5, 11–16 |
| Prescriptive Insight | **35%** | Rekomendasi dan tindakan berbasis prediksi, tidak berhenti di prediksi | 17–21 |
| Penyampaian & Visualisasi | **25%** | Kejelasan presentasi dan tampilan visual | Seluruh deck, naskah, cara membawakan |

---

## 2. File dan tautan penting

| Apa | Lokasi |
|---|---|
| PPT final (versi tim, 23 slide) | `Kepepet_Deadline___DSCO_2026_Final_2.pptx` (PDF-nya sudah dibagikan di chat) |
| Naskah presentasi 13 menit (bisa diedit) | https://claude.ai/artifact/Aks8WzzSnbxqaJ2ubbkRHw |
| Deck versi Claude (sumber desain, privat) | https://claude.ai/artifact/AcxPR9fnVBrT329pHBQcNt |
| Aplikasi demo Pelita Belajar | https://pelita-belajar.vercel.app |
| Notebook final di repo | `notebooks/99_final_submission.ipynb` |
| Notebook versi submission lain | `notebooks/98_submission_6.ipynb`, `96_submission_8.ipynb`, `95_submission_9.ipynb` |
| Log semua submission + eksperimen | `submissions/README.md` |
| Aturan, FAQ, timeline, dataset, checklist | `docs/01_…` sampai `docs/05_…` |
| Data | `data/raw/train.csv`, `test.csv`, `sample_submission.csv` |

---

## 3. Kartu contekan: angka yang wajib hafal

| Angka | Artinya |
|---|---|
| **52,7%** | Catatan mahasiswa di data latih yang berakhir gagal atau mundur (13.753 dari 26.086) |
| **94,0%** vs 41,1% | Berisiko bila tugas pertama tidak dikumpulkan sampai batas waktu (n = 5.714, 22%) vs yang mengumpulkan |
| **95,2%** vs 45,6% | Berisiko bila tidak pernah membuka kelas daring (pola angka pengganti, 3.738 baris) vs yang aktif |
| **22 vs 50** | Median klik minggu ke-1: berisiko vs tidak berisiko |
| **85%** vs 38% | Berisiko bila aktivitas terakhir di hari 0–6 vs hari 25–28 |
| **98,8%** | Berisiko bila tugas terlewat **dan** tak pernah membuka kelas daring (3.045 mahasiswa) |
| **25% · 92% · 43%** | Dua aturan sederhana menandai 25% mahasiswa, 92% tepat, menangkap 43% yang berisiko |
| **57%** | Mahasiswa berisiko yang tampak normal (tugas dikumpulkan, aktif) → alasan butuh model |
| **92%** | Catatan pertama mahasiswa yang nanti mengulang ternyata berisiko (rata-rata 53%) |
| **21% → 4%** | Pengulang yang terlewat model, tanpa vs dengan fitur pola mengulang |
| **0,78044** | F1 OOF gabungan 3 GBDT (ambang 0,40) |
| **0,80074** | F1 public leaderboard versi final (lihat catatan di bagian 9) |
| **81,1% / 75,2%** | Recall / precision OOF di ambang 0,40 |
| **0,771 → 0,780** | F1 di ambang 0,50 → 0,40; stabil di 0,36–0,42 |
| **30,1% · 1,7%** | Porsi gain fitur asesmen · fitur demografi |
| **30% · 93% · 52%** | Tingkat tinggi: 30% mahasiswa, 93% benar berisiko, mencakup 52% semua yang berisiko |
| **98%** | Tepat sasaran bila tutor hanya menghubungi 20% skor teratas |
| **300 → 278** | Per 1.000 mahasiswa: hubungi 300, 278 di antaranya memang berisiko |
| **+0,0137** | Total kenaikan F1 public dari 0,78704 ke 0,80074 |

---

## 4. Proyek dalam satu halaman

- **Masalah:** satu dari dua catatan mahasiswa berakhir gagal atau mundur, dan kampus baru tahu saat nilai akhir keluar.
- **Tujuan:** memprediksi `at_risk` hanya dari data empat minggu pertama, lalu mengubah skornya menjadi daftar tindakan tutor.
- **Data:** 32.588 catatan (26.086 latih, 6.502 uji), 62 fitur, 7 modul. Metrik: F1 kelas berisiko.
- **Pendekatan:** bersihkan data → tandai angka pengganti → fitur pola mengulang → validasi silang → gabungan LightGBM, XGBoost, CatBoost → ambang 0,40 → tiga tingkat risiko → aplikasi Pelita Belajar.
- **Hasil:** F1 OOF 0,78044, public 0,80074, recall 81%. Dari 30% teratas, 93% tepat sasaran.
- **Pesan utama:** yang menentukan adalah perilaku di empat minggu pertama, bukan latar belakang, dan perilaku bisa diubah lewat intervensi.

---

## 5. Data dan kualitas data

Satu baris = satu mahasiswa di satu modul-periode. Target `at_risk`: 1 = 13.753 (52,7%), 0 = 12.333 (47,3%), cukup seimbang sehingga tidak perlu oversampling.

| Kelompok fitur | Jumlah | Contoh |
|---|---|---|
| Konteks modul | 3 | `code_module`, `code_presentation`, `module_presentation_length` |
| Demografi | 6 | `gender`, `region`, `highest_education`, `imd_band`, `age_band`, `disability` |
| Riwayat studi | 3 | `num_of_prev_attempts`, `studied_credits`, `registration_days_from_start` |
| Asesmen | 29 | `no_submission_by_cutoff`, `avg_score`, `submission_delay` |
| Aktivitas daring | 21 | `interaction_volume`, `active_days`, `week1–4_interactions` |

Perbaikan kualitas data (semua tanpa mengubah label, tanpa membuang baris, tanpa data eksternal):

| Masalah | Bukti | Tindakan |
|---|---|---|
| Kode modul `GGG` (372 baris uji) tidak ada di latih | Periode dan panjang modul identik dengan M07 (P12/261, P21/241, P22/269 hari); rasio uji/latih M07 0,10 vs modul lain ≈0,25, jadi 0,30 setelah digabung | Dipetakan ke `M07` |
| Kode modul terselip di latih | Menurut urutan `id`, 144 baris `M04_P22` dan 1 baris `M05_P12` berada di tengah blok M07 (total 145) | Dikembalikan ke `M07` |
| Penulisan kategori tidak seragam | `Region 3`, `region2`; `A Level` vs `A level` | Disamakan |
| Kolom konstan | `submitted_Assessment_1/2` hanya satu nilai | Dibuang |
| Angka pengganti aktivitas | 3.738 baris (14,3%) persis 182 klik, 10 hari aktif, 20 situs | Ditandai, lalu dikosongkan |
| Angka pengganti nilai | Saat `has_score = 0`: `avg_score` = 77, `score_Assessment_1` = 70, delay = −1 (38% baris) | Ditandai, lalu dikosongkan |
| Pergeseran distribusi latih–uji? | Model pembeda latih vs uji hanya AUC 0,50 | Tidak ada pergeseran |

---

## 6. Temuan EDA

**Sinyal 1 · Tugas pertama.** Tidak mengumpulkan sampai batas waktu: 94,0% berisiko (n = 5.714) vs mengumpulkan 41,1% (n = 20.372). Tenggat tugas pertama tanggalnya pasti, jadi intervensi bisa dijadwalkan.

**Sinyal 2 · Aktivitas daring.**
- Tidak pernah membuka kelas daring: 95,2% berisiko vs aktif 45,6%.
- Median klik per minggu, tidak berisiko: 50 · 46 · 62 · 43. Berisiko: 22 · 17 · 29 · 14.
- Berisiko menurut hari aktivitas terakhir: 0–6 → 85% · 7–13 → 75% · 14–20 → 62% · 21–24 → 51% · 25–28 → 38%.

**Sinyal 3 · Kelas dan latar belakang.**
- Per kelas modul-periode: 28,1% (M01_P12) sampai 65,4% (M03_P21).
- Per modul: M01 30% · M02 52% · M03 62% · M04 53% · M05 44% · M06 58% · M07 41%.
- Pendidikan terakhir: 32% (pascasarjana) sampai 70% (tidak tercatat). Kemiskinan wilayah: terkaya 42%, termiskin 65%.
- Percobaan sebelumnya: 0 → 51% · 1 → 65% · 2+ → 72%.

**Dua perilaku digabung (matriks 2×2).**

| | Aktif di kelas daring | Tak pernah membuka |
|---|---|---|
| **Tugas pertama terlewat** | 88,5% berisiko · 2.669 mhs | **98,8%** berisiko · 3.045 mhs |
| **Tugas dikumpulkan** | 39,8% berisiko · 19.680 mhs | 79,6% berisiko · 692 mhs |

Dua aturan (tugas terlewat **atau** tak pernah membuka) menandai 24,6% mahasiswa, 92,4% tepat, dan menangkap 43,1% yang berisiko. Sel biru (tampak normal) berisi 56,9% dari semua mahasiswa berisiko, dan itulah alasan model dibutuhkan.

---

## 7. Pemodelan

### Alur kerja 8 langkah
Dataset → pembersihan (GGG → M07, kode terselip, kategori) → penanda angka pengganti → rekayasa fitur (pola mengulang) → validasi (10-fold × 3 seed) → tiga GBDT (rata-rata probabilitas) → ambang 0,40 → tingkat risiko dan rencana aksi.

### Fitur kunci: pola mengulang
- Dataset tidak punya ID mahasiswa, tapi urutan baris di setiap blok modul-periode sama.
- Pasangan catatan dengan profil identik, modul sama, dan jumlah percobaan naik satu membentuk kurva pada plot posisi baris. Pasangan yang hanya kebetulan mirip tersebar acak.
- Proporsi berisiko pendahulu menurut jarak ke kurva: 92% · 74% · 62% · 54% · 50%.
- Dengan fitur ini, pengulang yang terlewat model turun dari 21% ke 4%.
- **Batas yang harus diakui:** sebagian informasinya datang dari periode berikutnya. Skor peringatan dini minggu ke-4 dan segmentasi risiko memakai model **tanpa** fitur tautan.

### Validasi
Stratified 10-fold, diulang dengan seed 42, 7, dan 2026. Setiap baris mendapat prediksi out-of-fold (OOF) dari model yang tidak pernah melihatnya. Metrik: F1 kelas berisiko.

### Proses pencarian model (F1 public)

| Langkah | F1 public | Kenaikan |
|---|---|---|
| Gabungan 3 GBDT + pembersihan kategori (submission 1) | 0,78704 | |
| + tautan mahasiswa mengulang (submission 2) | 0,79227 | +0,0052 |
| + perbaikan modul terselip, tautan per himpunan (submission 4) | 0,80018 | +0,0079 |
| Final: penanda angka pengganti, 10-fold × 3 seed | 0,80074 | +0,0006 |

Dicoba tetapi tidak dipakai (semua hanya bergeser sekitar ±0,001 F1): tuning Optuna, ExtraTrees, RandomForest, HistGradientBoosting, MLP, LightGBM per modul, pseudo-label, stacking lintas modul.

### Pemilihan model (F1 OOF terbaik per kandidat)

| Model | F1 OOF |
|---|---|
| Regresi logistik (baseline) | 0,77315 |
| CatBoost | 0,77967 |
| XGBoost | 0,77961 |
| LightGBM | 0,78000 |
| **Gabungan 3 GBDT** | **0,78044** |

Alasan memilih GBDT: menangani nilai kosong hasil penandaan, menangkap ambang non-linier seperti tenggat terlewat, dan menemukan interaksi antar-fitur secara otomatis. Gabungan tiga model dipilih karena paling tinggi dan paling stabil, walaupun selisihnya dengan LightGBM tunggal kecil (+0,0004).

### Evaluasi (OOF, ambang 0,40)

| | Prediksi aman | Prediksi berisiko |
|---|---|---|
| **Aktual aman** | TN 8.650 (70,1%) | FP 3.683 (29,9%) |
| **Aktual berisiko** | FN 2.595 (18,9%) | TP 11.158 (81,1%) |

Precision 75,2%, recall 81,1%. F1 di ambang 0,50 = 0,77136; di ambang 0,40 = 0,78044. Ambang lebih rendah disengaja: salah mengingatkan cukup berbiaya satu pesan, sedangkan melewatkan mahasiswa bisa berujung mundur.

### Fitur terpenting (LightGBM, porsi gain)
`no_submission_by_cutoff` 18,5% · `last_activity_day` 9,1% · `code_module` 6,2% · `avg_score` 4,1% · `week4_interactions` 3,8% · `late_interactions` 3,6% · `active_days` 3,3%. Total fitur asesmen 30,1%; demografi (`region`, `edu_ord`) masing-masing 1,7%.

Cara menjelaskan selisih dengan EDA: latar belakang berpengaruh di EDA, tetapi pengaruhnya sudah tercermin lewat perilaku. Setelah perilaku diketahui, tambahan dari latar belakang kecil.

---

## 8. Business insight

### Segmentasi risiko (model minggu ke-4, tanpa fitur tautan, OOF data latih)

| Tingkat | Batas skor | Porsi mahasiswa | Benar berisiko | Cakupan dari semua yang berisiko | Tindakan |
|---|---|---|---|---|---|
| Tinggi | ≥ 0,75 | 30% (7.746) | 93% | 52% | Kontak tutor personal minggu ini |
| Sedang | 0,40–0,75 | 28% (7.188) | 54% | 28% | Pengingat otomatis, pantau mingguan |
| Rendah | < 0,40 | 43% (11.152) | 24% | 19% | Tanpa intervensi khusus |

### Kapasitas tutor
- Hubungi 20% skor teratas: 98% tepat sasaran, menjangkau 37% yang berisiko.
- Hubungi 30% skor teratas: 93% tepat, menjangkau 53%.
- Kampus cukup menentukan kapasitasnya, dan urutan skor yang menentukan siapa.

### Rencana aksi

| Pemicu dari data | Tindakan | Kapan | Ukuran keberhasilan |
|---|---|---|---|
| Tidak aktif daring minggu 1–2 (EDA sinyal 2) | Telepon orientasi: cek akses, jadwal, motivasi | Minggu 2 | % yang mulai aktif dalam 7 hari |
| Tugas pertama belum dikumpulkan (EDA sinyal 1) | Pengingat H-3; tutor menghubungi ≤ 48 jam setelah tenggat | Minggu 3–4 | % yang akhirnya mengumpulkan |
| Skor tingkat tinggi (segmentasi) | Pendampingan dan rencana belajar personal | Minggu 4 | % yang turun ke tingkat sedang/rendah |
| Mendaftar ulang modul yang sama (pola mengulang) | Mentor sejak registrasi ulang | Saat registrasi | Tingkat lulus mahasiswa pengulang |
| Modul berisiko tinggi M03, M06 (risiko per modul) | Tinjau beban dan jadwal tugas awal | Tiap semester | Proporsi berisiko per modul |

Prinsip: tindakan murah (pengingat otomatis) untuk banyak mahasiswa, tindakan mahal (tutor personal) hanya untuk tingkat tinggi.

### Dampak dan langkah 90 hari
- Per 1.000 mahasiswa: hubungi 300, dan 278 di antaranya memang berisiko. Itu separuh dari semua yang berisiko, terjangkau di minggu ke-4.
- Tanpa model pun, dua aturan sederhana menangkap 43% dan bisa dimulai besok.

| Fase | Isi |
|---|---|
| Hari 0–30 · Pilot | 1–2 modul berisiko tinggi (misalnya M03); tutor dilatih memakai daftar prioritas |
| Hari 31–60 · Uji | Kelompok intervensi vs pembanding; ukur aktif kembali dan tugas terkumpul |
| Hari 61–90 · Perluas | Evaluasi kelulusan dan pengunduran diri, lalu terapkan di semua modul |
| Berkelanjutan | Skor diperbarui tiap minggu, model dilatih ulang tiap periode |

### Pelita Belajar
Aplikasi web (https://pelita-belajar.vercel.app) yang mengubah skor risiko menjadi daftar mahasiswa yang perlu dibantu lebih dulu. Menu: Ringkasan · Data Belajar · Analisis CSV · Panduan Tutor. Di PPT ada kode QR menuju situsnya.

### Batasan yang disampaikan terbuka
- 19% mahasiswa berisiko masih berskor rendah di minggu ke-4 (masalahnya baru muncul belakangan).
- M07 paling sulit diprediksi (AUC 0,70).
- Fitur tautan membutuhkan data periode berikutnya, jadi tidak dipakai untuk peringatan dini.

---

## 9. Notebook dan submission

### Notebook di repo

| Notebook | Isi |
|---|---|
| `99_final_submission.ipynb` | Notebook utama (60 sel): 1 Setup · 2 EDA · 3 Preprocessing (pembersihan, fitur tautan) · 4 Pemilihan Model · 5 Evaluasi (threshold, kestabilan antar-fold, matriks kebingungan, performa per modul, fitur terpenting, ablasi fitur tautan) · 6 Prediksi & submission · 7 Insight preskriptif. Saat ini menghasilkan `submission_7.csv` |
| `98_submission_6.ipynb` | Menghasilkan `submission_6.csv` (tautan lintas modul + fitur kohort + ensemble dua pipeline) |
| `96_submission_8.ipynb` | Menghasilkan `submission_8.csv` (threshold plug-in 0,39) |
| `95_submission_9.ipynb` | Menghasilkan `submission_9.csv` (+ LightGBM per modul) |

Cara menjalankan: `pip install -r requirements.txt`, taruh `train.csv` dan `test.csv` di folder yang sama dengan notebook, lalu Restart & Run All (±8 menit di 4 core). Nama file keluaran diatur lewat `SUBMISSION_NO`.

### Riwayat submission

| No | Perubahan utama | F1 CV | F1 public |
|---|---|---|---|
| 1 | Blend LGB + XGB + CAT, pembersihan kategori, ambang 0,37 | 0,7761 | 0,78704 |
| 2 | + fitur tautan mahasiswa mengulang, ambang 0,40 | 0,7797* | 0,79227 |
| 3 | Perbaikan perlakuan tautan latih vs uji (tidak disubmit) | 0,7779 | — |
| 4 | + 145 kode terselip, tautan per himpunan, `order_pos`, ambang 0,38 | 0,7790 | **0,80018** |
| 5 | Tautan lintas modul, fitur kohort, Optuna, LGB + XGB | 0,7818 | 0,79012 |
| 6 | Ensemble pipeline 4 dan 5 | 0,7810 | 0,79357 |
| 7 | Pipeline 4, rata-rata 5 pembagian fold | 0,7787 | 0,79981 |
| 8 | Seperti 7, ambang plug-in 0,39 | 0,7790 | 0,79… |
| 9 | 7 + LightGBM per modul | 0,7798 | 0,79540 |

\* CV no. 2 terlalu optimis karena fitur latih lebih tajam daripada uji.

Final yang dipilih di log repo: `submission_7.csv` (paling stabil, public setara terbaik) dan `submission_6.csv` (CV tertinggi).

Audit kebocoran (semua negatif): urutan baris uji tidak membawa informasi label (korelasi prediksi antar-tetangga uji 0,06–0,09, setara latih 0,06–0,08); tidak ada imputasi yang bergantung label; tidak ada tautan nyata antara mahasiswa uji dan latih, jadi data memang dibagi per mahasiswa.

### Penting: cocokkan angka PPT dengan notebook yang dikumpulkan

Angka model di PPT (OOF 0,78044, public 0,80074, 10-fold × 3 seed 42/7/2026) berasal dari PPTX/notebook tim. Notebook final di repo ini adalah submission 7: 5 pembagian fold (seed 42, 7, 123, 2024, 99), CV 0,7787, public 0,79981. Aturan lomba menyatakan "yang dipresentasikan = yang dikumpulkan", jadi:

- [ ] Pastikan notebook yang dikumpulkan lewat form 1 November adalah notebook yang menghasilkan 0,78044 / 0,80074.
- [ ] Kalau yang dikumpulkan ternyata versi repo (submission 7), sesuaikan angka di slide 2, 5, 12–15, dan 22 sebelum tampil.
- [ ] Siapkan notebook yang dikumpulkan dalam keadaan terbuka di laptop, kalau juri minta melihat.

---

## 10. Struktur PPT final (23 slide)

| No | Judul slide | Bagian | Waktu | Pembicara | Pesan kunci |
|---|---|---|---|---|---|
| 1 | Cover | — | 0:00–0:50 | Zhahra | Salam, perkenalan, cerita tutor di minggu ke-4 |
| 2 | Ringkasan Eksekutif | Pemahaman Masalah | 0:50–1:30 | Zhahra | 52,7% · 94% · 93%; F1 0,78 / 0,80 |
| 3 | Latar Belakang & Tujuan | Pemahaman Masalah | 1:30–2:00 | Zhahra | Kampus tahu saat sudah terlambat |
| 4 | Tinjau Kilas Dataset | Pemahaman Masalah | 2:00–2:20 | Zhahra | 32.588 catatan, 62 fitur, target seimbang |
| 5 | Alur Kerja | Pemahaman Masalah | 2:20–2:45 | Zhahra | Delapan langkah, data sampai aksi |
| 6 | Kualitas Data | EDA | 2:45–3:15 | Zhahra | Data dibuat jujur tanpa ubah label |
| 7 | Sinyal 1: Tugas Pertama | EDA | 3:15–3:45 | Zhahra | 94% vs 41% |
| 8 | Sinyal 2: Aktivitas Daring | EDA | 3:45–4:15 | Zhahra | 95%, 22 vs 50 klik, 85% |
| 9 | Sinyal 3: Kelas & Latar Belakang | EDA | 4:15–4:40 | Zhahra | Konteks perlu, tapi belum menjelaskan kenapa |
| 10 | Dua Perilaku | EDA | 4:40–5:15 | Zhahra | 98,8%; 57% tampak normal → butuh model |
| 11 | Siklus Mengulang | Pemodelan | 5:15–5:55 | Ridho | 92%; 21% → 4%; batas fitur tautan |
| 12 | Skema Validasi | Pemodelan | 5:55–6:15 | Ridho | 10-fold × 3 seed, OOF |
| 13 | Proses Pencarian Model | Pemodelan | 6:15–6:50 | Ridho | Lompatan dari temuan data, bukan tuning |
| 14 | Pemilihan Model | Pemodelan | 6:50–7:15 | Ridho | Gabungan 3 GBDT 0,78044 |
| 15 | Evaluasi Model | Pemodelan | 7:15–7:50 | Ridho | Recall 81%, ambang 0,40 |
| 16 | Fitur Terpenting | Pemodelan | 7:50–8:15 | Ridho | Perilaku > latar belakang |
| 17 | Segmentasi Risiko | Business Insight | 8:15–8:45 | Ridho | 30% teratas, 93% tepat |
| 18 | Kapasitas Tutor | Business Insight | 8:45–9:10 | Ridho | 98% bila kapasitas 20% |
| 19 | Rencana Aksi | Business Insight | 9:10–9:45 | Ridho | Pemicu → tindakan → waktu → ukuran |
| 20 | Dampak & Langkah 90 Hari | Business Insight | 9:45–10:20 | Ridho | 300 → 278; pilot, uji, perluas |
| 21 | Demo: Pelita Belajar | Business Insight | 10:20–11:50 | Ridho | Tutor tinggal buka daftar |
| 22 | Kesimpulan | Kesimpulan | 11:50–12:30 | Zhahra | Masalah, akar masalah, model, tindakan, batas |
| 23 | Terima Kasih | — | 12:30–13:00 | Zhahra | Kembali ke cerita tutor, salam penutup |

Hal kecil di PPT yang sebaiknya diperbaiki sebelum tampil:
- [ ] Slide 15: label "Precision" dan "Recall" tidak terlihat di atas angka 75,2% dan 81,1%.
- [ ] Slide 21: tab footer menyorot "Kesimpulan", padahal demo masih bagian Business Insight.
- [ ] Slide 6/naskah: "145 baris M04" sebenarnya 144 baris `M04_P22` + 1 baris `M05_P12`. Tidak perlu diubah di slide, cukup tahu kalau ditanya.

---

## 11. Naskah presentasi 13 menit

Versi yang bisa diedit bersama ada di https://claude.ai/artifact/Aks8WzzSnbxqaJ2ubbkRHw. Salinan di bawah adalah versi 27 November 2026.

Total 13:00: sekitar 10:20 bicara, 1:30 demo, dan sekitar 1:10 untuk jeda dan perpindahan slide. Tempo sekitar 125 kata per menit. Teks dalam kurung siku adalah petunjuk gerakan, tidak dibacakan.

### Pembukaan

**Slide 1 · Cover · 0:00–0:50 · Zhahra**

Assalamu'alaikum warahmatullahi wabarakatuh. Selamat [pagi/siang], salam sejahtera bagi kita semua. Shalom. Om swastiastu. Namo buddhaya. Salam kebajikan.

Yang terhormat Bapak dan Ibu dewan juri DSCO 2026, serta rekan-rekan finalis. Kami tim Kepepet Deadline dari Universitas Andalas. Saya Zhahra Idhya Astwoti, bersama rekan saya, Ridho Dwi Syahputra.

Bayangkan seorang tutor di minggu keempat semester. Di kelasnya ada ratusan mahasiswa, dan separuh dari mereka nanti akan gagal atau mundur. Pertanyaannya: siapa yang harus ia hubungi lebih dulu? Hari ini kami tunjukkan bahwa jawabannya sudah ada di data empat minggu pertama. [klik]

### Pemahaman Masalah

**Slide 2 · Ringkasan Eksekutif · 0:50–1:30 · Zhahra**

Kalau Bapak Ibu hanya mengingat satu slide, inilah slide-nya. [tunjuk kartu kiri] Apa yang terjadi: 52,7 persen mahasiswa berakhir gagal atau mundur, satu dari dua. [tunjuk kartu tengah] Kenapa terjadi: tandanya muncul sangat awal. Bila tugas pertama terlewat, 94 persen berisiko. [tunjuk kartu kanan] Apa yang kami lakukan: kami bagi mahasiswa ke tiga tingkat risiko. Kalau tutor fokus ke 30 persen teratas, 93 persen yang dihubungi memang butuh bantuan. Model kami mencapai F1 0,78 di validasi dan 0,80 di public leaderboard, dengan recall 81 persen. Mari kami tunjukkan bagaimana kami sampai ke angka-angka ini.

**Slide 3 · Latar Belakang & Tujuan · 1:30–2:00 · Zhahra**

Tanpa sistem, kampus baru tahu ada yang gagal saat nilai akhir keluar, dan saat itu sudah terlambat. Yang terdampak bukan hanya mahasiswa, tapi juga tutor yang waktunya terbatas. Karena itu tujuan kami dua: memprediksi at_risk hanya dari data empat minggu pertama, lalu mengubah skornya menjadi daftar tindakan tutor.

**Slide 4 · Tinjau Kilas Dataset · 2:00–2:20 · Zhahra**

Datanya 32.588 catatan: 26.086 untuk latih dan 6.502 untuk uji. Ada 62 fitur dalam lima kelompok, terbanyak dari asesmen dan aktivitas daring. Targetnya cukup seimbang, 52,7 persen berisiko, jadi kami tidak perlu oversampling.

**Slide 5 · Alur Kerja · 2:20–2:45 · Zhahra**

Ini peta kerja kami dalam delapan langkah. Mulai dari pembersihan data dan fitur pola mengulang, lalu validasi dan tiga model GBDT, sampai skor yang diterjemahkan menjadi tingkat risiko dan rencana aksi. [klik]

### EDA

**Slide 6 · Kualitas Data · 2:45–3:15 · Zhahra**

Masuk ke EDA. Sebelum memodelkan, kami pastikan datanya jujur. Ada 372 baris uji berkode GGG yang tidak ada di data latih. Periode dan panjang modulnya identik dengan M07, jadi kami petakan ke M07. Lalu 145 baris bertuliskan M04 ternyata terselip di blok M07. Penulisan wilayah dan pendidikan kami samakan, dan dua kolom konstan dibuang. Semua tanpa mengubah label, tanpa membuang baris, dan tanpa data eksternal.

**Slide 7 · Sinyal 1: Tugas Pertama · 3:15–3:45 · Zhahra**

Sinyal pertama: tugas. Mahasiswa yang tidak mengumpulkan tugas sampai batas waktu, 94 persennya berakhir berisiko. Yang mengumpulkan, hanya 41 persen. Kelompok ini besar: 5.714 mahasiswa, sekitar satu dari lima. Artinya, tenggat tugas pertama adalah titik intervensi yang tanggalnya sudah pasti, jadi bantuan bisa dijadwalkan.

**Slide 8 · Sinyal 2: Aktivitas Daring · 3:45–4:15 · Zhahra**

Sinyal kedua: aktivitas daring. Mahasiswa yang tidak pernah membuka kelas daring, 95 persennya berisiko. Di antara yang aktif pun polanya jelas. [tunjuk grafik kiri] Di minggu pertama, mahasiswa berisiko hanya 22 klik, kurang dari separuh mahasiswa yang aman. [tunjuk grafik kanan] Yang terakhir aktif di minggu pertama, 85 persennya berisiko. Artinya, login dan klik bisa dipantau otomatis setiap minggu, tanpa menunggu nilai.

**Slide 9 · Sinyal 3: Kelas & Latar Belakang · 4:15–4:40 · Zhahra**

Sinyal ketiga: konteks. Risiko antar-kelas berbeda jauh, dari 28 persen di M01 sampai 65 persen di M03. Latar belakang juga berpengaruh: lulusan pascasarjana 32 persen berisiko, yang pendidikannya tidak tercatat 70 persen. Konteks ini perlu dihitung, tapi belum menjelaskan kenapa mereka berisiko.

**Slide 10 · Dua Perilaku · 4:40–5:15 · Zhahra**

Untuk menjawab kenapa, kami silangkan dua sinyal pertama. [tunjuk sel oranye tua] Mahasiswa yang melewatkan tugas pertama dan tidak pernah membuka kelas daring: 98,8 persen berisiko, hampir pasti. Jadi akar masalahnya adalah keterlibatan di awal semester. Dua aturan sederhana ini menandai seperempat mahasiswa dengan ketepatan 92 persen. [tunjuk sel biru] Tapi 57 persen mahasiswa berisiko justru tampak normal. Untuk menemukan mereka, dibutuhkan model, dan bagian ini akan dilanjutkan oleh Ridho. [serah ke Ridho, klik]

### Pemodelan

**Slide 11 · Siklus Mengulang · 5:15–5:55 · Ridho**

Terima kasih, Zhahra. Fitur kunci kami lahir dari pola mahasiswa yang mengulang. Dataset tidak punya ID mahasiswa, tapi kami menemukan bahwa urutan baris di setiap blok modul dan periode ternyata sama. [tunjuk grafik kiri] Pasangan catatan dengan profil identik, modul sama, dan jumlah percobaan naik satu membentuk kurva. Yang kebetulan mirip tersebar acak. [tunjuk grafik tengah] Makin dekat ke kurva, makin pasti catatan pertamanya berisiko, sampai 92 persen. Dengan fitur ini, pengulang yang terlewat model turun dari 21 persen ke 4 persen. Kami juga jujur soal batasnya: sebagian informasi ini baru ada di periode berikutnya, jadi skor peringatan dini minggu ke-4 memakai model tanpa fitur ini.

**Slide 12 · Skema Validasi · 5:55–6:15 · Ridho**

Supaya penilaiannya jujur, kami pakai stratified 10-fold yang diulang dengan tiga seed. Jadi setiap baris diprediksi oleh model yang tidak pernah melihatnya. Metriknya F1 untuk kelas berisiko, gabungan precision dan recall.

**Slide 13 · Proses Pencarian Model · 6:15–6:50 · Ridho**

Ini proses pencarian model terbaik kami, dilihat dari skor public di setiap langkah. Kami mulai dari 0,787. Dua lompatan terbesar datang dari temuan data: tautan mahasiswa mengulang, plus 0,005, dan perbaikan modul terselip, plus 0,008, sampai versi final 0,80074. Tuning Optuna, model tambahan, dan pseudo-label juga kami coba, tapi hanya menggeser F1 sekitar seperseribu. Jadi lompatan terbesar datang dari memahami data, dan kami memilih model yang sederhana dan stabil.

**Slide 14 · Pemilihan Model · 6:50–7:15 · Ridho**

Kami membandingkan regresi logistik sebagai baseline dengan tiga GBDT. Ketiga GBDT unggul, dan rata-rata ketiganya memberi F1 tertinggi, 0,78044. GBDT cocok karena menangani nilai kosong hasil penandaan, menangkap ambang seperti tenggat terlewat, dan menemukan interaksi antar-fitur secara otomatis.

**Slide 15 · Evaluasi Model · 7:15–7:50 · Ridho**

Hasilnya: dari 13.753 mahasiswa berisiko, model menangkap 11.158. Recall 81 persen, precision 75 persen, jadi empat dari lima sudah tertangkap di minggu keempat. Kami memilih ambang 0,40, bukan 0,50, karena F1 naik dari 0,771 ke 0,780 dan stabil di rentang 0,36 sampai 0,42. Ini disengaja: lebih baik salah mengingatkan, yang biayanya satu pesan, daripada melewatkan mahasiswa yang akhirnya mundur. Biaya salah sasaran itu nanti kami tekan lewat tingkat risiko.

**Slide 16 · Fitur Terpenting · 7:50–8:15 · Ridho**

Apa yang dipakai model untuk memutuskan? Fitur asesmen menyumbang 30 persen, dipimpin tugas yang tidak dikumpulkan, lalu kapan terakhir aktif. Menariknya, latar belakang yang tadi terlihat di EDA hanya menyumbang 1,7 persen. Artinya pengaruh latar belakang sudah tercermin lewat perilaku, dan perilakulah yang menentukan. Kabar baiknya, perilaku bisa diubah lewat intervensi. [klik]

### Business Insight

**Slide 17 · Segmentasi Risiko · 8:15–8:45 · Ridho**

Sekarang bagian terpenting: apa yang harus dilakukan. Skor model kami ubah menjadi tiga tingkat. Tingkat tinggi berisi 30 persen mahasiswa, 93 persen benar berisiko, dan sudah mencakup separuh dari semua yang berisiko. Mereka dihubungi tutor minggu ini. Tingkat sedang cukup diberi pengingat otomatis, dan tingkat rendah tanpa intervensi khusus. Skor ini dari model versi minggu keempat, jadi benar-benar bisa dijalankan tepat waktu.

**Slide 18 · Kapasitas Tutor · 8:45–9:10 · Ridho**

Bagaimana kalau tutor terbatas? Kalau tutor hanya sanggup menghubungi satu dari lima mahasiswa berskor tertinggi, 98 persen yang dihubungi memang berisiko. Naik ke 30 persen, ketepatannya masih 93 persen. Jadi kampus cukup menentukan kapasitasnya, dan urutan skor yang menentukan siapa.

**Slide 19 · Rencana Aksi · 9:10–9:45 · Ridho**

Setiap tindakan berawal dari temuan tadi. Mahasiswa yang tidak aktif di minggu satu dan dua ditelepon untuk orientasi. Untuk tugas pertama, ada pengingat tiga hari sebelum tenggat, dan tutor menghubungi dalam 48 jam bila terlewat. Tingkat tinggi mendapat pendampingan personal, pengulang mendapat mentor sejak registrasi, dan modul M03 serta M06 meninjau beban tugas awalnya. Prinsipnya: tindakan murah untuk banyak mahasiswa, tindakan mahal hanya untuk yang paling berisiko.

**Slide 20 · Dampak & Langkah 90 Hari · 9:45–10:20 · Ridho**

Dampaknya bagi kampus, per 1.000 mahasiswa: tutor cukup menghubungi 300 orang, dan 278 di antaranya memang berisiko. Itu separuh dari semua yang berisiko, terjangkau di minggu keempat. Tanpa model pun, dua aturan sederhana menangkap 43 persen, jadi kampus bisa mulai besok. Langkah 90 hari kami: bulan pertama pilot di modul berisiko tinggi seperti M03, bulan kedua uji dengan kelompok pembanding supaya terbukti intervensinya yang mengubah hasil, dan bulan ketiga evaluasi lalu perluas ke semua modul. Setelah itu, skor diperbarui setiap minggu.

**Slide 21 · Demo: Pelita Belajar · 10:20–11:50 · Ridho**

Supaya rekomendasi ini benar-benar dipakai, kami membangun Pelita Belajar. Bapak Ibu bisa mencobanya langsung lewat kode QR ini. [putar video atau buka situs]

Halaman pertama bertanya: modelnya sudah ada, lalu apa? [halaman Ringkasan] Di Ringkasan, tutor melihat gambaran risiko mahasiswanya. [halaman Data Belajar] Di Data Belajar, tutor melihat catatan belajar tiap mahasiswa. [halaman Analisis CSV] Di Analisis CSV, kampus cukup mengunggah data baru untuk langsung dianalisis. [halaman Panduan Tutor] Dan Panduan Tutor menjelaskan tindakan untuk setiap tingkat, sama dengan rencana aksi tadi.

Jadi tutor tidak perlu membaca model. Cukup buka daftarnya, dan ia tahu siapa yang dihubungi lebih dulu. Untuk kesimpulan, kembali ke Zhahra. [serah ke Zhahra, klik]

*(Sesuaikan urutan halaman dengan yang muncul di video kalian.)*

### Kesimpulan dan Penutup

**Slide 22 · Kesimpulan · 11:50–12:30 · Zhahra**

Terima kasih, Ridho. Sebagai kesimpulan, kembali ke pertanyaan awal kami. Masalahnya: satu dari dua mahasiswa berisiko, dan datanya harus dibaca dengan jujur. Akar masalahnya: perilaku di awal semester dan siklus mengulang, bukan latar belakang. Modelnya: gabungan tiga GBDT dengan F1 0,78 di validasi dan 0,80 di leaderboard. Tindakannya: tiga tingkat risiko dan Pelita Belajar. Kami juga sadar batasnya: sebagian mahasiswa baru bermasalah setelah minggu keempat, dan modul M07 paling sulit diprediksi.

**Slide 23 · Terima Kasih · 12:30–13:00 · Zhahra**

Jadi, kembali ke tutor di minggu keempat tadi. Ia tidak perlu menunggu nilai akhir: data empat minggu sudah cukup untuk menolong mahasiswa lebih dulu. Terima kasih atas perhatian Bapak dan Ibu dewan juri. Kami siap menerima pertanyaan.

Wassalamu'alaikum warahmatullahi wabarakatuh. Salam sejahtera bagi kita semua. Shalom. Om shanti shanti shanti om. Namo buddhaya. Salam kebajikan.

*(Kalau sesi tanya jawab langsung menyusul, salam penutup boleh dipindah ke akhir tanya jawab.)*

### Kalau waktu mepet
Cek jam di 5:15 (serah ke Ridho), 8:15 (masuk Business Insight), dan 11:50 (demo selesai). Kalau terlambat lebih dari 30 detik:
- Slide 4: "32 ribu catatan, 62 fitur, target cukup seimbang." (hemat 10 detik)
- Slide 5: "Delapan langkah ini akan kami bahas satu per satu." (hemat 10 detik)
- Slide 9: kalimat pertama dan terakhir saja. (hemat 10 detik)
- Slide 12: "10-fold tiga seed, metrik F1." (hemat 10 detik)

### Cara membawakan
1. Beri jeda satu detik setelah angka kunci: 52,7%, 94%, 98,8%, 0,80074, 93%.
2. Tatap juri, bukan layar, setiap mengucapkan "Artinya". Layar hanya ditunjuk di bagian bertanda [tunjuk].
3. Sebut nama rekan saat serah terima.
4. Ucapkan kalimat batas ("Kami juga jujur soal batasnya") dengan tenang. Juri menghargai tim yang menyebut kelemahannya sebelum ditanya.
5. Latihan penuh dengan stopwatch minimal tiga kali, dan rekam sekali untuk mengecek kata pengisi.

---

## 12. Bank tanya jawab

Pembagian penjawab: **Zhahra** untuk data, EDA, dan business insight. **Ridho** untuk model, validasi, fitur tautan, dan aplikasi. Kalau satu orang ragu, yang lain menambahkan satu kalimat saja, jangan saling menimpa.

Pola menjawab: jawab langsung dalam satu kalimat → beri satu angka bukti → tutup dengan dampaknya. Kalau tidak tahu, katakan jujur dan tawarkan cara mengeceknya.

### Data dan EDA

| Pertanyaan | Jawaban singkat |
|---|---|
| Kenapa GGG dipetakan ke M07, bukan dibuang? | 372 baris uji; periode dan panjang modulnya persis M07 (261, 241, 269 hari), dan rasio uji/latih M07 baru wajar (0,30) setelah digabung. Membuang berarti tidak bisa memprediksi 372 baris itu. |
| Apa itu "angka pengganti"? | Nilai isian otomatis, bukan perilaku: 3.738 baris punya aktivitas persis 182 klik, 10 hari, 20 situs; nilai kosong terisi 77. Kami tandai lalu kosongkan, dan penandanya justru sinyal kuat (95,2% berisiko). |
| Benarkah 145 baris semuanya M04? | 144 baris `M04_P22` dan 1 baris `M05_P12`, semuanya berada di tengah blok M07 menurut urutan `id`. |
| Apakah data tidak seimbang? | Cukup seimbang: 52,7% berisiko, 47,3% tidak. Karena itu tidak perlu oversampling. |
| Apakah distribusi latih dan uji berbeda? | Tidak. Model pembeda latih vs uji hanya mencapai AUC 0,50, setara tebakan acak. |
| Kenapa EDA menunjukkan latar belakang berpengaruh, tapi model bilang demografi hanya 1,7%? | Pengaruh latar belakang sudah tercermin lewat perilaku. Setelah tugas dan aktivitas diketahui, tambahan informasi dari latar belakang kecil. |
| Apakah ini kausal? Tugas terlewat menyebabkan gagal? | Belum tentu, ini asosiasi yang sangat kuat. Karena itu rencana 90 hari memakai kelompok pembanding untuk membuktikan bahwa intervensinya yang mengubah hasil. |

### Model dan validasi

| Pertanyaan | Jawaban singkat |
|---|---|
| Kenapa GBDT, bukan neural network? | Data tabular dengan nilai kosong dan ambang non-linier; GBDT unggul di sini. MLP sudah dicoba dan hanya bergeser sekitar 0,001 F1. |
| Kenapa gabungan tiga model, padahal selisihnya kecil? | Kenaikan F1-nya memang kecil (+0,0004 dari LightGBM), tetapi prediksi gabungan lebih stabil karena kesalahan tiap model saling menutupi. |
| Validasinya seperti apa? | Stratified 10-fold diulang dengan tiga seed (42, 7, 2026). Setiap baris dinilai model yang tidak pernah melihatnya (prediksi out-of-fold). |
| Kenapa metriknya F1? | Itu metrik resmi lomba, dan cocok karena menyeimbangkan precision dan recall untuk kelas berisiko. |
| Kenapa ambang 0,40? | F1 OOF naik dari 0,771 (ambang 0,50) ke 0,780 dan stabil di 0,36–0,42. Melewatkan mahasiswa berisiko lebih mahal daripada satu pesan yang salah sasaran. |
| Bagaimana memastikan tidak overfit ke leaderboard? | Keputusan diambil dari validasi silang, bukan leaderboard. Public leaderboard hanya sekitar 1.950 baris, jadi selisih ±0,01 masih derau. |
| Hyperparameter tuning? | Optuna sudah dicoba (45 percobaan); kenaikannya masuk derau, jadi kami pilih konfigurasi yang lebih sederhana. |
| Performa per modul? | Tidak merata; M07 paling sulit (AUC 0,70). Itu kami sebut sebagai batas. |

### Fitur pola mengulang dan kebocoran data

| Pertanyaan | Jawaban singkat |
|---|---|
| Apakah fitur tautan termasuk kebocoran data? | Di kompetisi sah: hanya kolom dari panitia, tanpa label dan tanpa data luar. Tapi sebagian informasinya datang dari periode berikutnya, jadi skor peringatan dini minggu ke-4 dan segmentasi risiko memakai model tanpa fitur tautan, dan tetap 93% tepat di tingkat tinggi. |
| Apakah urutan baris uji membocorkan label? | Sudah diaudit: korelasi prediksi antar-tetangga di uji (0,06–0,09) setara dengan latih (0,06–0,08), jadi urutan tidak membawa informasi label. |
| Bagaimana tahu pasangan itu benar orang yang sama? | Pasangan dengan profil identik dan percobaan naik satu membentuk kurva urutan baris; pasangan kebetulan tersebar acak. Semakin dekat ke kurva, semakin tinggi proporsi berisikonya (92% vs rata-rata 53%). |
| Kalau di kampus nyata ada ID mahasiswa? | Lebih mudah: riwayat mengulang langsung diketahui saat registrasi ulang, dan itu yang kami jadikan pemicu mentor. |

### Business insight dan aplikasi

| Pertanyaan | Jawaban singkat |
|---|---|
| Dari mana angka 93% dan 98%? | Dari prediksi out-of-fold model minggu ke-4, diurutkan dari skor tertinggi: 30% teratas 92,6% tepat, 20% teratas 97,9% tepat. |
| Kenapa batas tingkat 0,40 dan 0,75? | 0,40 adalah ambang F1 terbaik. 0,75 memberi kelompok sekitar 30% mahasiswa dengan ketepatan sekitar 93%, sesuai kapasitas kontak personal. |
| Bagaimana kalau kapasitas tutor kampus berbeda? | Kampus cukup memilih berapa persen yang sanggup dihubungi; kurva kapasitas menunjukkan ketepatan dan cakupannya untuk setiap pilihan. |
| Berapa biayanya? | Tindakan mahal (tutor personal) hanya untuk 30% mahasiswa; 28% berikutnya cukup pengingat otomatis yang hampir tanpa biaya. |
| Bagaimana mengukur keberhasilan? | Uji kelompok pembanding di hari 31–60. Ukurannya: persentase yang aktif kembali, tugas yang terkumpul, dan tingkat kelulusan. |
| Bagaimana soal etika dan stigma label "berisiko"? | Skor hanya untuk tutor, dipakai untuk menawarkan bantuan, bukan sanksi. Kontribusi demografi kecil (1,7%), dan keputusan akhir tetap di tangan tutor. |
| Data apa yang dibutuhkan setiap minggu? | Data yang sama dengan lomba: aktivitas kelas daring dan status asesmen. Di Pelita Belajar, kampus cukup mengunggah CSV-nya. |
| Bagaimana model tetap relevan di semester berikutnya? | Skor diperbarui setiap minggu dan model dilatih ulang setiap periode dengan data terbaru. |
| Pelita Belajar dibuat dengan apa? | *(Jawab sesuai teknologi yang kalian pakai, jangan menebak.)* |

### Pertanyaan menjebak

| Pertanyaan | Cara menjawab |
|---|---|
| "Tim lain skornya jauh lebih tinggi, kenapa skor kalian 0,80?" | Jangan defensif. Fokus kami model yang tervalidasi dan tetap bisa dipakai di minggu ke-4; informasi yang tidak tersedia saat peringatan dini sengaja tidak dipakai untuk rekomendasi. Lalu arahkan ke nilai praktisnya: 93% tepat sasaran. |
| "Kalau precision 75%, berarti 1 dari 4 kontak sia-sia?" | Di ambang 0,40 iya, karena itu ada tingkat risiko: kontak personal hanya untuk tingkat tinggi yang 93% tepat; sisanya pengingat otomatis yang murah. |
| "Apakah model ini bisa dipakai di kampus lain?" | Polanya (tugas dan aktivitas awal) umum, tetapi model perlu dilatih ulang dengan data kampus tersebut, dimulai dari pilot. |

---

## 13. Asal-usul angka: mana yang wajib dicek ulang

| Angka | Sumber | Status |
|---|---|---|
| Statistik EDA (94,0%, 95,2%, 22 vs 50, 85%, kelas, pendidikan, wilayah, percobaan) | Dihitung langsung dari `train.csv` | Aman |
| Matriks 2×2 (98,8 / 88,5 / 79,6 / 39,8%) dan dua aturan (24,6% · 92,4% · 43,1%) | Dihitung langsung dari `train.csv` | Aman |
| F1 OOF 0,78044, perbandingan model, matriks kebingungan, ambang 0,50 vs 0,40 | PPTX/notebook tim | **Cocokkan dengan notebook yang dikumpulkan** |
| F1 public 0,80074 | PPTX tim (tidak ada di log repo) | **Cocokkan dengan skor resmi Kaggle** |
| F1 public 0,78704 · 0,79227 · 0,80018 | Log `submissions/README.md` (submission 1, 2, 4) | Aman |
| Fitur terpenting (18,5%, 9,1%, 30,1%, 1,7%) | Analisis ulang Claude (LightGBM gain) | Cek dengan notebook tim |
| Tingkat risiko, kapasitas 98%/93%, 300 → 278, 19% berskor rendah | Analisis ulang Claude (OOF model tanpa fitur tautan) | **Cek dengan notebook tim** |
| Kurva 92% dan 21% → 4% | Analisis ulang Claude | **Cek dengan notebook tim** |
| M07 AUC 0,70 | Notebook final, bagian 5.3 | Cek angka persisnya |

---

## 14. Checklist hari-H

Sebelum berangkat:
- [ ] PPT (`.pptx` dan PDF) tersimpan di dua tempat: laptop dan flashdisk/Drive.
- [ ] Video demo tersimpan offline; QR code dan situs Pelita Belajar dicek berfungsi.
- [ ] Notebook yang dikumpulkan siap dibuka, sudah dijalankan dengan output tersimpan.
- [ ] Angka PPT sudah dicocokkan (bagian 9 dan 13).
- [ ] Perbaikan kecil PPT (bagian 10) sudah dikerjakan.
- [ ] Latihan penuh dengan stopwatch minimal tiga kali; total di bawah 13:30.

Kalau tampil online lewat Zoom:
- [ ] Tes berbagi layar dan suara video sebelum giliran.
- [ ] Koneksi cadangan (hotspot) siap.
- [ ] Kamera menyala, latar rapi, almamater.

Saat tampil:
- [ ] Hadir 30 menit lebih awal.
- [ ] Satu orang memegang timer dan memberi kode kalau terlambat.
- [ ] Siapkan kertas kecil berisi kartu contekan (bagian 3).

---

## 15. Glosarium singkat

| Istilah | Arti |
|---|---|
| `at_risk` | Target: 1 bila mahasiswa berakhir gagal atau mundur |
| F1 | Rata-rata harmonik precision dan recall: 2·P·R / (P + R) |
| Precision | Dari yang diprediksi berisiko, berapa yang benar berisiko: TP / (TP + FP) |
| Recall | Dari yang benar berisiko, berapa yang tertangkap: TP / (TP + FN) |
| OOF (out-of-fold) | Prediksi untuk setiap baris dari model yang tidak dilatih dengan baris itu |
| Stratified k-fold | Data dibagi k bagian dengan proporsi label yang sama di setiap bagian |
| GBDT | Gradient boosted decision trees: LightGBM, XGBoost, CatBoost |
| Ambang (threshold) | Batas skor untuk menyatakan berisiko; kami pakai 0,40 |
| Gain | Ukuran seberapa besar sebuah fitur membantu model memisahkan kelas |
| Angka pengganti | Nilai isian otomatis di data untuk mahasiswa tanpa catatan, bukan perilaku asli |
| Fitur tautan / pola mengulang | Fitur yang menghubungkan catatan mahasiswa yang sama antar-periode tanpa ID |
