# Latihan Tanya Jawab Babak Final · Kepepet Deadline

60 pertanyaan latihan untuk sesi tanya jawab 10 menit, disusun mengikuti rubrik juri: Analisis & Justifikasi Model 40%, Prescriptive Insight 35%, Penyampaian & Visualisasi 25%.

- **Bagian A** berisi daftar pertanyaan saja, untuk latihan tanpa melihat jawaban.
- **Bagian B** berisi kunci jawaban.
- **Bagian C** berisi rantai pertanyaan lanjutan untuk topik yang paling mungkin dikejar juri.
- **Bagian D** berisi cara latihan.

Tanda kemungkinan muncul: ★★★ hampir pasti · ★★ mungkin · ★ jarang.
Penjawab utama: **Z** = Zhahra (data, EDA, business insight) · **R** = Ridho (fitur, model, aplikasi).
Tanda **⚠** = angka dari analisis ulang Claude, cocokkan dulu dengan notebook tim. Tanda **[isi sendiri]** = hanya tim yang tahu jawabannya.

---

## Bagian A · Daftar pertanyaan

### 1. Pemahaman masalah dan data

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 1 | Apa definisi "berisiko" di data ini, dan kenapa penting bagi kampus? | ★★ | Z |
| 2 | Satu baris data itu satu mahasiswa? Bagaimana kalau mahasiswa yang sama muncul lebih dari sekali? | ★★ | Z |
| 3 | Kenapa hanya memakai data empat minggu pertama? | ★★ | Z |
| 4 | Apakah datanya seimbang? Apakah kalian melakukan oversampling? | ★★ | Z |
| 5 | Kenapa memakai F1, bukan akurasi? | ★★★ | Z |
| 6 | Siapa pengguna akhir solusi kalian? | ★★ | Z |

### 2. EDA dan kualitas data

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 7 | Masalah kualitas data apa yang paling berpengaruh ke model? | ★★★ | Z |
| 8 | Bagaimana kalian yakin kode GGG itu M07? | ★★ | Z |
| 9 | Apa itu "angka pengganti", dan bagaimana kalian menemukannya? | ★★★ | Z |
| 10 | Bagaimana kalian menangani nilai kosong dan kategori yang tidak tercatat? | ★★ | Z |
| 11 | Apakah distribusi data latih dan uji berbeda? | ★ | Z |
| 12 | Temuan EDA apa yang paling mengejutkan? | ★★ | Z |
| 13 | Di EDA latar belakang terlihat berpengaruh, tapi di model hampir tidak. Kenapa? | ★★★ | Z |
| 14 | Apakah tugas terlewat menyebabkan mahasiswa gagal, atau hanya berkorelasi? | ★★ | Z |

### 3. Rekayasa fitur dan kebocoran data

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 15 | Jelaskan fitur pola mengulang dengan bahasa sederhana. | ★★★ | R |
| 16 | Apakah fitur pola mengulang termasuk data leakage? | ★★★ | R |
| 17 | Bagaimana kalian yakin pasangan itu orang yang sama, bukan kebetulan? | ★★ | R |
| 18 | Apakah urutan baris di data uji membocorkan label? | ★★ | R |
| 19 | Berapa sumbangan fitur pola mengulang ke skor? | ★★ | R |
| 20 | Fitur apa saja yang kalian buat sendiri? | ★★ | R |
| 21 | Apakah kalian mencoba fitur lain yang akhirnya tidak dipakai? | ★ | R |

### 4. Pemilihan model dan validasi (bobot 40%)

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 22 | Kenapa memilih GBDT? | ★★★ | R |
| 23 | Kenapa menggabungkan tiga model, padahal selisihnya dengan LightGBM sangat kecil? | ★★★ | R |
| 24 | Apa baseline kalian, dan seberapa jauh model kalian mengunggulinya? | ★★ | R |
| 25 | Kenapa tidak memakai deep learning? | ★★ | R |
| 26 | Bagaimana skema validasinya, dan kenapa diulang dengan beberapa seed? | ★★★ | R |
| 27 | Bagaimana memastikan model tidak overfit ke leaderboard? | ★★★ | R |
| 28 | Bagaimana hyperparameter ditentukan? | ★★ | R |
| 29 | Bagaimana menangani variabel kategorikal? | ★ | R |
| 30 | Kenapa skor public (0,80) lebih tinggi daripada OOF (0,78)? | ★★ | R |
| 31 | Apa saja yang sudah dicoba tapi gagal? | ★★ | R |
| 32 | Model mana yang dipakai untuk kompetisi, dan mana yang dipakai kampus? | ★★★ | R |

### 5. Evaluasi dan ambang

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 33 | Kenapa ambangnya 0,40, bukan 0,50? | ★★★ | R |
| 34 | Precision 75% berarti satu dari empat kontak salah sasaran. Apakah itu bisa diterima? | ★★★ | R |
| 35 | Jelaskan matriks kebingungan kalian. | ★★ | R |
| 36 | Modul mana yang paling sulit diprediksi, dan kenapa? | ★★ | R |
| 37 | Apakah skor probabilitasnya sudah terkalibrasi? | ★ | R |
| 38 | Seberapa stabil hasil antar-fold? | ★ | R |

### 6. Insight preskriptif dan implementasi (bobot 35%)

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 39 | Dari prediksi ini, tindakan konkret apa yang harus dilakukan kampus? | ★★★ | Z |
| 40 | Kenapa batas tingkat risikonya 0,40 dan 0,75? | ★★ | Z |
| 41 | Dari mana angka 93% dan 98%? | ★★★ | Z |
| 42 | Bagaimana kalau kapasitas tutor kampus berbeda? | ★★ | Z |
| 43 | Berapa biaya intervensinya? | ★★ | Z |
| 44 | Bagaimana mengukur keberhasilan intervensi? | ★★★ | Z |
| 45 | Siapa yang menjalankan setiap tindakan? | ★★ | Z |
| 46 | Data apa yang dibutuhkan setiap minggu, dan bagaimana alurnya? | ★★ | Z |
| 47 | Kalau kampus ingin mulai besok tanpa model, apa yang bisa dilakukan? | ★★ | Z |
| 48 | Bagaimana dengan mahasiswa berisiko yang skornya rendah? | ★★ | Z |

### 7. Aplikasi Pelita Belajar

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 49 | Apa saja fitur Pelita Belajar? | ★★ | R |
| 50 | Apakah model sudah berjalan di aplikasi, atau aplikasinya masih menampilkan hasil yang sudah dihitung? | ★★★ | R |
| 51 | Teknologi apa yang dipakai untuk membangun aplikasinya? | ★ | R |
| 52 | Bagaimana keamanan data mahasiswa di aplikasi? | ★★ | R |

### 8. Etika, batasan, dan pengembangan

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 53 | Bagaimana menghindari stigma dan bias terhadap mahasiswa yang diberi label berisiko? | ★★ | Z |
| 54 | Apa batasan terbesar solusi kalian? | ★★★ | Z |
| 55 | Kalau punya waktu lebih, apa yang akan kalian kembangkan? | ★★ | R |
| 56 | Apakah model ini bisa dipakai di kampus lain? | ★★ | R |
| 57 | Bagaimana model tetap akurat di semester berikutnya? | ★★ | R |

### 9. Umum dan menjebak

| No | Pertanyaan | Kemungkinan | Penjawab |
|---|---|---|---|
| 58 | Tim lain skornya lebih tinggi. Apa keunggulan solusi kalian? | ★★★ | Z |
| 59 | Apa tantangan terbesar selama lomba? | ★★ | R |
| 60 | Bagaimana pembagian tugas di tim kalian? | ★★ | Z |

---

## Bagian B · Kunci jawaban

Pola menjawab: **jawaban langsung** dalam satu kalimat → **satu angka bukti** → **dampaknya**. Maksimal 30–45 detik per jawaban.

### 1. Pemahaman masalah dan data

**1. Definisi berisiko.** `at_risk` = 1 bila mahasiswa berakhir gagal atau mundur di modul itu. Di data latih proporsinya 52,7%, satu dari dua. Penting karena tanpa sistem, kampus baru tahu saat nilai akhir keluar.

**2. Satu baris = apa?** Satu mahasiswa di satu modul-periode. Mahasiswa yang sama bisa muncul lagi kalau mengulang atau mengambil modul lain, dan itulah dasar fitur pola mengulang. Data latih dan uji dibagi per mahasiswa: data uji terdiri dari dua potongan terurut, dan tidak ada tautan nyata antara mahasiswa uji dan latih.

**3. Kenapa empat minggu?** Karena tujuannya peringatan dini. Setelah minggu ke-4 peluang menolong makin kecil, dan data lomba memang hanya mencakup empat minggu pertama.

**4. Seimbang?** Cukup seimbang: 52,7% berisiko, 47,3% tidak. Jadi kami tidak melakukan oversampling; yang kami setel adalah ambang keputusannya.

**5. Kenapa F1?** F1 adalah metrik resmi lomba, dan cocok karena menyeimbangkan precision dan recall pada kelas berisiko. Akurasi bisa terlihat tinggi walaupun banyak mahasiswa berisiko terlewat.

**6. Pengguna akhir.** Tutor atau dosen wali yang memilih siapa dihubungi lebih dulu, dan pengelola modul yang memantau risiko per modul. Mahasiswa adalah penerima bantuannya.

### 2. EDA dan kualitas data

**7. Masalah paling berpengaruh.** Angka pengganti. Sebanyak 3.738 baris (14,3%) punya aktivitas persis sama, 182 klik, 10 hari, 20 situs, dan nilai kosong terisi 77. Kalau tidak ditandai, model belajar dari angka palsu, padahal 95,2% kelompok ini berisiko.

**8. GGG = M07.** Ada tiga bukti:
- Kombinasi periode dan panjang modulnya persis M07: P12 261 hari, P21 241 hari, P22 269 hari.
- Rasio baris uji/latih M07 hanya 0,10, padahal modul lain sekitar 0,25. Setelah GGG digabung, rasionya menjadi 0,30.
- Proporsi pendidikan "A level" cocok dengan M07 di data latih (sekitar 33% vs 35%).

**9. Angka pengganti.** Saat profiling, ada nilai yang muncul jauh terlalu sering dalam kombinasi yang persis sama: 182 klik, 10 hari, 20 situs. Pola serupa ada di nilai: saat belum ada nilai, `avg_score` terisi 77, `score_Assessment_1` 70, dan keterlambatan −1 (38% baris). Itu isian otomatis untuk mahasiswa tanpa catatan, bukan perilaku asli.

**10. Nilai kosong.** Angka pengganti ditandai lalu dikosongkan, dan GBDT menangani nilai kosong secara bawaan. Kategori yang tidak tercatat, seperti "-" dan "?", diperlakukan sebagai kategori sendiri karena justru informatif: pendidikan tidak tercatat 70% berisiko. ⚠ Cocokkan dengan cara di notebook tim.

**11. Latih vs uji.** Tidak berbeda. Model yang dilatih untuk membedakan baris latih dari uji hanya mencapai AUC 0,50, setara tebakan acak.

**12. Temuan paling mengejutkan.** Mahasiswa yang mengulang ternyata bisa dilacak tanpa ID dari urutan baris, dan catatan pertamanya 92% berisiko. Yang kedua: angka yang terlihat normal (182 klik) ternyata angka pengganti dengan 95,2% berisiko.

**13. Latar belakang vs model.** Latar belakang berkorelasi dengan perilaku. Setelah tugas dan aktivitas diketahui, tambahan informasi dari latar belakang kecil, jadi demografi hanya 1,7% gain. Artinya pengaruh latar belakang sudah tercermin lewat perilaku.

**14. Sebab-akibat?** Belum tentu; yang kami temukan adalah asosiasi yang sangat kuat (94% vs 41%). Karena itu rencana 90 hari memakai kelompok pembanding di hari 31–60 untuk membuktikan bahwa intervensinya yang mengubah hasil.

### 3. Rekayasa fitur dan kebocoran data

**15. Fitur pola mengulang.** Data tidak punya ID mahasiswa, tapi urutan baris di setiap blok modul-periode ternyata sama.
- Kalau dua catatan punya profil identik, modulnya sama, periodenya berurutan, dan jumlah percobaannya naik satu, posisi barisnya membentuk kurva. Itu orang yang sama.
- Catatan pertama orang yang nanti mengulang 92% berisiko, karena orang mengulang biasanya karena gagal.

**16. Leakage?** Di kompetisi fitur ini sah: hanya memakai kolom dari panitia, tanpa label dan tanpa data luar. Tapi kami sadar sebagian informasinya datang dari periode berikutnya. Karena itu skor peringatan dini minggu ke-4 dan segmentasi risiko memakai model tanpa fitur tautan, dan tetap 93% tepat di tingkat tinggi.

**17. Bukan kebetulan?** Pasangan yang hanya kebetulan mirip tersebar acak di plot posisi baris, sedangkan orang yang sama membentuk kurva. Bukti tambahannya, proporsi berisiko turun mulus dengan jarak ke kurva: 92%, 74%, 62%, 54%, 50%. Kalau tautannya acak, polanya tidak akan seperti itu.

**18. Urutan baris uji.** Sudah diaudit. Korelasi prediksi antar-baris yang bertetangga di data uji (0,06–0,09) setara dengan data latih (0,06–0,08), jadi urutan baris tidak membawa informasi label.

**19. Sumbangan fitur tautan.**
- Di public leaderboard, dari 0,78704 menjadi 0,79227 (+0,005). Itu perubahan utama antara submission 1 dan 2; selain itu hanya ambangnya yang digeser dari 0,37 ke 0,40.
- Pengulang yang terlewat model turun dari 21% ke 4%.
- Tanpa fitur ini, F1 OOF sekitar 0,775 vs 0,779 dan AUC 0,847 vs 0,853 ⚠. Jadi model peringatan dini tanpa tautan hanya sedikit lebih lemah.

**20. Fitur buatan sendiri.** Ada tiga kelompok:
- Penanda angka pengganti, lalu nilainya dikosongkan.
- Fitur tautan: jumlah kandidat pasangan, jumlah kandidat yang dekat kurva, dan posisi relatif baris dalam bloknya.
- Pembersihan kategori: GGG, kode terselip, penulisan wilayah dan pendidikan.

**21. Fitur yang tidak dipakai.** Tautan lintas modul (mahasiswa yang sama di modul lain; hanya 19 pasangan blok yang lolos uji) dan 15 fitur relatif kohort sudah dicoba di submission 5. CV naik tipis (0,7818), tapi public turun (0,79012), dan selisihnya masih di dalam derau, jadi kami pilih pipeline yang lebih sederhana.

### 4. Pemilihan model dan validasi

**22. Kenapa GBDT?** Data tabular dengan nilai kosong (hasil penandaan), ambang non-linier seperti tenggat terlewat, dan banyak interaksi antar-fitur. GBDT menangani ketiganya secara bawaan, dan ketiga GBDT mengalahkan regresi logistik.

**23. Kenapa gabungan tiga model?** Kenaikan F1-nya memang kecil, +0,0004 dari LightGBM (0,78044 vs 0,78000). Alasan utamanya kestabilan: kesalahan tiap model saling menutupi, sehingga prediksi tidak bergantung pada satu algoritma. Biaya tambahannya kecil.

**24. Baseline.** Regresi logistik, F1 OOF 0,77315. Gabungan tiga GBDT 0,78044, naik sekitar 0,007. Kenaikan terbesar justru datang dari fitur dan pembersihan data, bukan dari pilihan algoritma.

**25. Deep learning?** Datanya tabular dan hanya 26 ribu baris, kondisi di mana GBDT biasanya unggul. MLP sudah kami coba sebagai tambahan ensemble, dan hasilnya hanya bergeser sekitar 0,001 F1. GBDT juga lebih mudah dijelaskan ke kampus.

**26. Skema validasi.** Stratified 10-fold: setiap putaran, sembilan bagian untuk melatih dan satu bagian diuji, dengan proporsi label yang sama. Diulang dengan tiga seed (42, 7, 2026) karena hasil satu pembagian bisa kebetulan. Dengan satu pembagian saja, sekitar 100 prediksi uji bisa berganti label tergantung pembagiannya.

**27. Overfit ke leaderboard?** Semua keputusan diambil dari validasi silang, bukan dari leaderboard. Public leaderboard hanya sebagian kecil data uji (sekitar 1.950 baris), jadi selisih ±0,01 masih derau. Contohnya, submission 5 naik di CV tapi turun 0,010 di public.

**28. Hyperparameter.** Di notebook repo: learning rate kecil (0,02–0,05), pohon dangkal (LightGBM 15 daun, XGBoost kedalaman 5, CatBoost kedalaman 6), dan early stopping 150 ronde di setiap fold ⚠. Tuning Optuna 45 percobaan juga dicoba, tapi kenaikannya masuk derau, jadi kami pakai konfigurasi yang lebih sederhana.

**29. Variabel kategorikal.** Di notebook repo, LightGBM memakai tipe kategori bawaannya, sedangkan XGBoost dan CatBoost memakai kode ordinal ⚠. Sebelumnya, penulisan kategori disamakan dulu.

**30. Public lebih tinggi dari OOF.** Wajar, karena public leaderboard hanya sekitar 1.950 baris, jadi skornya bergoyang ±0,01. Pegangan kami adalah OOF di 26.086 baris, yang jauh lebih stabil.

**31. Yang dicoba tapi gagal.** Semuanya hanya bergeser sekitar ±0,001 F1, sehingga model dianggap sudah jenuh pada informasi empat minggu pertama:
- tuning Optuna;
- ExtraTrees, RandomForest, HistGradientBoosting, MLP;
- LightGBM per modul;
- pseudo-label dan stacking lintas modul;
- latih ulang di 100% data.

**32. Model kompetisi vs kampus.** Model kompetisi memakai fitur tautan (F1 OOF 0,78044). Untuk kampus di minggu ke-4, kami pakai model tanpa fitur tautan karena informasinya baru tersedia di periode berikutnya. Model inilah yang dipakai di segmentasi risiko: 30% teratas 93% tepat.

### 5. Evaluasi dan ambang

**33. Ambang 0,40.** F1 OOF naik dari 0,771 (ambang 0,50) ke 0,780, dan relatif datar di rentang 0,36–0,42, jadi pilihannya tidak rapuh. Secara bisnis juga masuk akal: melewatkan mahasiswa berisiko lebih mahal daripada satu pesan yang salah sasaran.

**34. Precision 75%.** Di ambang 0,40 memang satu dari empat salah sasaran. Karena itu kami pakai tingkat risiko: kontak personal yang mahal hanya untuk tingkat tinggi, yang 93% tepat; tingkat sedang cukup pengingat otomatis yang hampir tanpa biaya.

**35. Matriks kebingungan.** Dari 13.753 mahasiswa berisiko, 11.158 tertangkap (recall 81,1%) dan 2.595 terlewat. Dari 12.333 yang aman, 3.683 ikut ditandai. Dari semua yang ditandai berisiko, 75,2% memang berisiko.

**36. Modul tersulit.** M07, AUC sekitar 0,70 ⚠. Dugaan kami, sinyal awal di M07 lebih lemah dan sebagian datanya bermasalah (GGG, kode terselip). Itu kami sebut sebagai batas dan prioritas pengembangan.

**37. Kalibrasi.** Skor kami pakai untuk mengurutkan dan menentukan tingkat, dan proporsi berisiko aktual per tingkat (24%, 54%, 93%) naik sesuai skor. Kalibrasi formal, misalnya isotonic, bisa ditambahkan kalau kampus butuh probabilitas absolut.

**38. Kestabilan.** Prediksi akhir adalah rata-rata dari banyak model (10 fold × 3 seed × 3 algoritma), dan F1 stabil di rentang ambang 0,36–0,42. Rentang F1 per fold: [isi dari notebook].

### 6. Insight preskriptif dan implementasi

**39. Tindakan konkret.** Ada lima pemicu, masing-masing dengan tindakan, waktu, dan ukuran:

| Pemicu | Tindakan | Waktu |
|---|---|---|
| Tidak aktif daring minggu 1–2 | Telepon orientasi | Minggu 2 |
| Tugas pertama terlewat | Pengingat H-3, tutor menghubungi ≤ 48 jam setelah tenggat | Minggu 3–4 |
| Skor tingkat tinggi | Pendampingan personal | Minggu 4 |
| Mendaftar ulang modul yang sama | Mentor sejak registrasi ulang | Saat registrasi |
| Modul berisiko tinggi M03, M06 | Tinjau beban tugas awal | Tiap semester |

**40. Batas 0,40 dan 0,75.** 0,40 adalah ambang F1 terbaik, jadi di bawahnya mahasiswa dianggap aman. 0,75 memberi kelompok sekitar 30% mahasiswa dengan ketepatan sekitar 93%, ukuran yang masuk akal untuk kontak personal tutor ⚠.

**41. Angka 93% dan 98%.** Dari prediksi out-of-fold model minggu ke-4, yaitu prediksi untuk data yang tidak dilihat model, diurutkan dari skor tertinggi. Hasilnya: 30% teratas 92,6% tepat, 20% teratas 97,9% tepat ⚠. Tetap perlu dibuktikan lewat pilot.

**42. Kapasitas berbeda.** Kampus cukup memilih berapa persen mahasiswa yang sanggup dihubungi, dan kurva kapasitas langsung menunjukkan ketepatan dan cakupannya. Misalnya 20%: 98% tepat, 37% terjangkau; 30%: 93% tepat, 53% terjangkau ⚠.

**43. Biaya.** Tindakan mahal (kontak tutor personal) hanya untuk tingkat tinggi, sekitar 30% mahasiswa. Tingkat sedang (28%) cukup pengingat otomatis yang hampir tanpa biaya, dan tingkat rendah (43%) tanpa intervensi khusus.

**44. Mengukur keberhasilan.** Uji dengan kelompok pembanding di hari 31–60: sebagian mahasiswa tingkat tinggi diintervensi, sebagian lagi dijadikan pembanding. Ukurannya persentase yang aktif kembali, tugas yang terkumpul, dan akhirnya tingkat kelulusan.

**45. Siapa menjalankan.** Usulan kami:
- tutor atau dosen wali untuk kontak personal;
- bagian akademik atau pengelola LMS untuk pengingat otomatis;
- koordinator modul untuk meninjau beban tugas M03 dan M06;
- tim data untuk memperbarui skor setiap minggu.

**46. Alur data mingguan.** Data aktivitas kelas daring dan status asesmen, sama dengan kolom di data lomba, diekspor setiap minggu. File CSV-nya diunggah ke Pelita Belajar, skor dihitung, dan tutor menerima daftar prioritas. [Sesuaikan dengan cara kerja aplikasi kalian.]

**47. Mulai besok tanpa model.** Pakai dua aturan sederhana: tugas pertama terlewat atau tidak pernah membuka kelas daring. Aturan ini menandai 25% mahasiswa dengan ketepatan 92% dan menangkap 43% yang berisiko.

**48. Berisiko tapi skornya rendah.** Sekitar 19% mahasiswa berisiko masih berskor rendah di minggu ke-4, karena masalahnya baru muncul belakangan ⚠. Solusinya, skor diperbarui setiap minggu (minggu 5–8) sehingga mereka tertangkap begitu perilakunya berubah.

### 7. Aplikasi Pelita Belajar

**49. Fitur aplikasi.** Empat menu: Ringkasan (gambaran risiko), Data Belajar (catatan belajar tiap mahasiswa), Analisis CSV (unggah data baru), dan Panduan Tutor (tindakan per tingkat risiko). Bisa diakses di pelita-belajar.vercel.app atau lewat QR di slide.

**50. Model sudah berjalan di aplikasi?** [isi sendiri] Jawab jujur: apakah skor dihitung langsung di aplikasi, atau hasil model diunggah lalu ditampilkan. Kalau masih prototipe, sebut "prototipe yang menunjukkan alur kerja tutor", lalu jelaskan langkah integrasinya.

**51. Teknologi.** [isi sendiri] Sebut framework dan tempat hosting yang benar-benar kalian pakai.

**52. Keamanan data.** Prinsip yang kami pegang: data minimal, akses hanya untuk tutor yang berwenang, tanpa menampilkan data sensitif yang tidak diperlukan untuk tindakan. [Sesuaikan dengan yang sudah diterapkan di aplikasi.]

### 8. Etika, batasan, dan pengembangan

**53. Stigma dan bias.** Skor hanya terlihat oleh tutor, dan dipakai untuk menawarkan bantuan, bukan sanksi. Mahasiswa tidak diberi label. Kontribusi demografi kecil (1,7%), dan keputusan akhir tetap di tangan tutor; ke depan kami usulkan audit performa per kelompok.

**54. Batasan terbesar.** Ada tiga:
- 19% mahasiswa berisiko belum terlihat di minggu ke-4.
- M07 paling sulit diprediksi (AUC sekitar 0,70).
- Fitur tautan butuh data periode berikutnya, jadi tidak dipakai untuk peringatan dini.

Kami juga belum membuktikan dampak intervensinya; itu tujuan pilot.

**55. Pengembangan.** Ada empat arah:
- Skor yang diperbarui setiap minggu sampai minggu ke-8.
- Uplift modeling: memilih mahasiswa yang paling terbantu oleh intervensi, bukan hanya yang paling berisiko.
- Kalibrasi skor dan audit keadilan per kelompok.
- Integrasi otomatis dengan LMS supaya tidak perlu unggah CSV.

**56. Kampus lain.** Polanya umum, karena tugas dan keterlibatan awal adalah sinyal di mana pun. Tapi model perlu dilatih ulang dengan data kampus tersebut dan dimulai dari pilot, karena modul, jadwal, dan pola aktivitasnya berbeda.

**57. Semester berikutnya.** Model dilatih ulang setiap periode dengan data terbaru, dan performanya dipantau setiap minggu. Kalau ketepatan tingkat tinggi turun jauh di bawah 90%, itu tanda model perlu diperbarui.

### 9. Umum dan menjebak

**58. Skor tim lain lebih tinggi.** Jangan defensif. Fokus kami model yang tervalidasi dan tetap bisa dipakai di minggu ke-4: informasi yang belum tersedia saat peringatan dini sengaja tidak dipakai untuk rekomendasi. Arahkan ke nilai praktisnya: 93% tepat sasaran dan rencana aksi yang siap dijalankan.

**59. Tantangan terbesar.** Ada dua:
- Data tanpa ID yang penuh angka pengganti. Kami harus membuktikan dulu bahwa angka itu palsu dan bahwa pasangan mengulang itu nyata.
- Menahan diri tidak mengejar leaderboard yang penuh derau, dan tetap berpegang pada validasi silang.

**60. Pembagian tugas.** [isi sendiri] Contoh bentuk jawaban: "Zhahra memegang EDA, kualitas data, dan insight bisnis; Ridho memegang rekayasa fitur, pemodelan, dan aplikasi. Keputusan model kami ambil berdua."

---

## Bagian C · Rantai pertanyaan lanjutan

Juri sering mengejar satu topik dengan dua atau tiga pertanyaan beruntun. Latih empat rantai ini sampai lancar.

### Rantai 1 · Kebocoran data (paling berbahaya)

1. "Fitur pola mengulang itu bukan leakage?" → Jawaban no. 16.
2. "Kalau begitu, kenapa tetap dipakai di submission?" → Aturan lomba membolehkan semua kolom dari panitia tanpa data luar, dan fitur ini tidak memakai label. Untuk dipakai kampus, kami pisahkan model tanpa fitur ini.
3. "Seberapa turun skornya tanpa fitur itu?" → F1 OOF sekitar 0,775 vs 0,779 dan AUC 0,847 vs 0,853 ⚠. Turunnya kecil, jadi model peringatan dini tetap layak.

### Rantai 2 · Ambang dan salah sasaran

1. "Kenapa 0,40?" → Jawaban no. 33.
2. "Berarti banyak salah sasaran?" → Jawaban no. 34.
3. "Bagaimana kalau kampus maunya hanya yang pasti berisiko?" → Naikkan kapasitas ke 20% teratas: 98% tepat. Kurva kapasitas membuat pilihan ini transparan.

### Rantai 3 · Bukti dampak bisnis

1. "93% itu dari data latih. Bagaimana di dunia nyata?" → Itu prediksi out-of-fold, jadi untuk data yang tidak dilihat model. Tetap perlu dibuktikan lewat pilot.
2. "Bagaimana membuktikan intervensinya berhasil?" → Jawaban no. 44.
3. "Kalau ternyata tidak berhasil?" → Pilot dibuat kecil (1–2 modul) supaya murah dihentikan. Tindakannya diganti, misalnya bentuk kontak atau waktunya, lalu diuji lagi.

### Rantai 4 · Akar masalah

1. "Benarkah akar masalahnya keterlibatan?" → Jawaban no. 14.
2. "Kenapa demografi hampir tidak berpengaruh?" → Jawaban no. 13.
3. "Lalu kenapa M03 dan M06 berisiko tinggi?" → Itu konteks modul (62% dan 58% berisiko). Karena itu salah satu tindakannya meninjau beban dan jadwal tugas awal di modul tersebut.

---

## Bagian D · Cara latihan

1. **Simulasi 10 menit.** Satu orang (atau teman) menjadi juri dan memilih acak 6–8 pertanyaan dari Bagian A, utamakan yang ★★★. Sepuluh menit biasanya cukup untuk 6–8 pertanyaan.
2. **Batasi waktu jawaban.** Maksimal 45 detik per jawaban, pakai stopwatch. Jawaban yang terlalu panjang mengurangi jumlah pertanyaan yang sempat dijawab.
3. **Satu penjawab utama.** Rekan hanya menambah satu kalimat kalau perlu, jangan saling menimpa.
4. **Kalau tidak tahu,** katakan jujur: "Kami belum menguji itu, tapi cara mengujinya adalah …". Itu lebih dihargai daripada menebak.
5. **Ulangi pertanyaan juri secara singkat** sebelum menjawab ("Pertanyaannya soal kenapa ambang 0,40, ya?"). Ini memberi waktu berpikir dan memastikan maksudnya tepat.
6. **Isi semua [isi sendiri] dan cek semua ⚠** sebelum hari-H. Jawaban yang angkanya tidak cocok dengan notebook adalah risiko terbesar.
