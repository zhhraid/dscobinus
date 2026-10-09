# FAQ Technical Meeting — DSCO 2026

Tanya jawab peserta dengan panitia saat technical meeting (2 Oktober 2026), dikelompokkan per topik.
Jawaban panitia ditulis apa adanya; baris **Implikasi** adalah catatan tim kita sendiri.

## Model & data

| Pertanyaan | Jawaban panitia |
|---|---|
| Boleh augmentasi data dari dataset (bukan data eksternal)? | Selagi bukan data eksternal, boleh. |
| Model pre-trained yang dilarang itu seperti ImageNet, ResNet, dll.? | Iya, **semua** pre-trained model dilarang karena data harus di-train sendiri berdasarkan dataset panitia. |
| Boleh pakai pseudo-labelling? | Boleh. |
| Boleh mengubah label pada dataset? | **Tidak boleh** melakukan perubahan label manual. |
| Boleh pakai library eksternal? | Library Python bebas selagi bukan AutoML dan model dilatih sendiri dengan data panitia. |
| Boleh pakai referensi dari luar selama pembuatan? | Boleh, selama tidak memakai data eksternal; pelatihan model tetap hanya dengan data panitia. |
| Metrik evaluasinya apa? | **F1 score**. |

**Implikasi:**

- Optimalkan **threshold** keputusan untuk F1, jangan hanya pakai 0.5.
- Baris train yang terlihat salah label tidak boleh dikoreksi manual. (Catatan kami: membuang baris atau memberi bobot sampel tidak dibahas panitia — tanyakan dulu ke grup sebelum dipakai.)
- Pseudo-labelling legal, tapi harus tetap reproducible di notebook final.

## Submission & notebook

| Pertanyaan | Jawaban panitia |
|---|---|
| Setelah merge akun Kaggle, tetap hanya ketua yang boleh submit? | Iya, betul. |
| Format nama file submission `[Nama Tim]_submission 1.csv`? | Iya, benar. |
| Tiap submission harus melampirkan ipynb? | Hanya CSV. Tapi 15 peringkat teratas private leaderboard wajib mengumpulkan notebook dan CSV. |
| Skor ipynb dan skor submit beda jauh = indikasi kecurangan? Panitia run ulang atau lihat log? | Benar, bisa dicurigai. Panitia **melihat run sebelumnya dan me-run ulang** notebooknya. |
| Kalau run ulang error karena path data beda? | Langsung `read_csv` **tanpa direktori**, seperti membaca CSV dari folder yang sama dengan notebook. |
| Ada urutan wajib untuk ipynb? | Tidak ada format urutan, tapi wajib minimal memuat EDA, Preprocessing, pemilihan model, evaluasi model. |

**Implikasi:**

- Notebook final harus **deterministik**: seed tetap untuk numpy, model, dan CV split.
- Notebook final memakai `pd.read_csv("train.csv")`, bukan `data/raw/train.csv`.
- Simpan CSV yang persis dihasilkan notebook final — itulah yang dikumpulkan.

## Final & presentasi

| Pertanyaan | Jawaban panitia |
|---|---|
| Finalis di luar Jabodetabek boleh online? | Iya, boleh. |
| Final diadakan bersamaan dengan 2 metode (Zoom + onsite)? | Iya. |
| Tim peringkat 11–15 hanya stand by atau tetap presentasi? | Diinfokan di WA sebelum hari H; stand by dulu saja. |
| Jadi 5 tim itu harus siap-siap kalau ada 10 besar yang out? | Iya, betul. |
| Elaborasi "Prescriptive insight — tindakan berbasis hasil prediksi"? | Bukan hanya menjelaskan sampai prediksi, tapi juga **memberikan rekomendasi**. |
| Ada format/template PPT? | Tidak ada; sesuaikan dengan rubrik penilaian presentasi di guidebook. |
| PPT technical meeting dipublikasikan? | Iya. |

**Implikasi:** sejak tahap EDA, catat temuan yang bisa jadi rekomendasi (mis. faktor apa yang paling mendorong risiko, intervensi apa untuk kelompok mana) — bobotnya 35%.

## Administrasi

| Pertanyaan | Jawaban panitia |
|---|---|
| Link Kaggle di-share kapan? | 3 Oktober 2026, jam 08.00. |
| Kalau ada pertanyaan baru setelah lihat data, hubungi siapa? | Grup atau contact person. |
