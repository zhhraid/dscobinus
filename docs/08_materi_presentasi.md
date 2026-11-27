# Materi Presentasi Final DSCO 2026 · Versi Bacaan

Tim **Kepepet Deadline** (Universitas Andalas) · Zhahra Idhya Astwoti · Ridho Dwi Syahputra
Judul: **Deteksi Dini Mahasiswa Berisiko Dropout dari Empat Minggu Pertama**, *dari skor risiko ke tindakan tutor yang tepat waktu.*

Dokumen ini menjelaskan isi ke-23 slide PPT final dalam bentuk bacaan. Tujuannya supaya kalian paham **apa** yang ditampilkan, **kenapa** keputusan itu diambil, dan **pesan apa** yang harus sampai ke juri, sehingga bisa menjelaskan dengan kata-kata sendiri, tidak sekadar menghafal.

Dokumen pendamping:
- naskah 13 menit: https://claude.ai/artifact/Aks8WzzSnbxqaJ2ubbkRHw;
- angka kunci dan checklist: `docs/06_briefing_final.md`;
- 60 pertanyaan latihan: `docs/07_latihan_tanya_jawab.md`.

---

## Cerita besar dalam satu paragraf

Satu dari dua mahasiswa di data ini berakhir gagal atau mundur, dan kampus baru tahu saat nilai akhir keluar. Kami menunjukkan bahwa tandanya sudah terlihat di empat minggu pertama. Mahasiswa yang melewatkan tugas pertama dan tidak membuka kelas daring hampir pasti berisiko, tetapi lebih dari separuh mahasiswa berisiko justru tampak normal, sehingga dibutuhkan model. Setelah datanya dibersihkan dengan jujur, gabungan tiga model gradient boosting mencapai F1 0,78 di validasi dan 0,80 di public leaderboard. Model itu menunjukkan bahwa perilaku, bukan latar belakang, yang paling menentukan. Skor model kemudian diubah menjadi tiga tingkat risiko, lengkap dengan tindakan, waktu, ukuran keberhasilan, dan aplikasi Pelita Belajar. Hasilnya, tutor cukup menghubungi 30% mahasiswa dan 93% di antaranya memang membutuhkan bantuan.

## Peta presentasi dan rubrik juri

| Bagian | Slide | Melayani aspek rubrik | Durasi |
|---|---|---|---|
| Pemahaman Masalah | 1–5 | Fondasi semua aspek | 2:45 |
| EDA | 6–10 | **Justifikasi model (40%)**: dasar pemilihan fitur | 2:30 |
| Pemodelan | 11–16 | **Analisis & Justifikasi Model (40%)** | 3:00 |
| Business Insight | 17–21 | **Prescriptive Insight (35%)** | 3:35 |
| Kesimpulan | 22–23 | **Penyampaian (25%)**: menutup cerita | 1:10 |

Penyampaian & Visualisasi (25%) dinilai sepanjang presentasi: desain konsisten, satu pesan per slide, grafik yang langsung terbaca, dan waktu yang terjaga.

---

## Bagian 1 · Pemahaman Masalah

### Slide 1 · Cover

**Isi slide.** Judul, subjudul "Dari skor risiko ke tindakan tutor yang tepat waktu", nama tim, universitas, dan foto anggota.

**Penjelasan.** Pembukaan dimulai dengan salam lintas agama, perkenalan, lalu satu cerita pendek: seorang tutor di minggu keempat dengan ratusan mahasiswa, separuhnya nanti gagal atau mundur. Siapa yang harus ia hubungi lebih dulu? Pertanyaan ini menjadi benang merah presentasi dan dijawab di slide terakhir.

**Pesan untuk juri.** Presentasi ini bukan tentang model, tetapi tentang menjawab keputusan nyata seorang tutor.

### Slide 2 · Ringkasan Eksekutif

**Isi slide.** Tiga kartu: *Apa yang terjadi?* 52,7% · *Kenapa terjadi?* 94% · *Apa yang dilakukan?* 93%. Di bawahnya empat angka: F1 OOF 0,78044, public leaderboard 0,80074, recall 81%, precision 75%.

**Penjelasan.** Slide ini memberi jawaban lebih dulu, sebelum detailnya:
- **52,7%** adalah besarnya masalah: lebih dari separuh catatan mahasiswa berakhir gagal atau mundur.
- **94%** adalah tanda paling awal: mahasiswa yang tidak mengumpulkan tugas pertama sampai batas waktu, 94%-nya berisiko.
- **93%** adalah hasil tindakannya: kalau tutor fokus ke 30% mahasiswa dengan skor tertinggi, 93% yang dihubungi memang berisiko.

Empat angka di bawah adalah bukti kualitas model. Recall 81% berarti empat dari lima mahasiswa berisiko tertangkap. Precision 75% berarti tiga dari empat yang ditandai memang berisiko.

**Pesan untuk juri.** Kalau juri hanya mengingat satu slide, mereka sudah tahu masalah, penyebab, solusi, dan kualitas modelnya.

### Slide 3 · Latar Belakang & Tujuan

**Isi slide.** Angka 52,7% (26.086 catatan; 1 catatan = 1 mahasiswa di 1 modul-periode), tiga pertanyaan (siapa terdampak, kenapa penting sekarang, apa tujuan), dan ringkasan data.

**Penjelasan.**
- **Siapa yang terdampak:** bukan hanya mahasiswa, tetapi juga tutor yang waktunya terbatas dan harus memilih siapa dibantu lebih dulu.
- **Kenapa penting sekarang:** setelah minggu keempat, peluang menolong makin kecil.
- **Tujuan, ada dua:** (1) memprediksi `at_risk` hanya dari data empat minggu pertama, dan (2) mengubah skor itu menjadi daftar tindakan.

Tujuan kedua yang membedakan kami. Prediksi saja belum menolong siapa pun.

**Pesan untuk juri.** Kami memahami masalah bisnisnya, bukan hanya target kolomnya.

### Slide 4 · Tinjau Kilas Dataset

**Isi slide.** Diagram donat 32.588 baris (80% latih = 26.086, 20% uji = 6.502), tabel lima kelompok fitur, target `at_risk`, metrik F1 kelas positif, 62 kolom dari empat minggu pertama.

**Penjelasan.** Kelompok fitur terbesar adalah asesmen (29 kolom) dan aktivitas daring (21 kolom); sisanya konteks modul (3), demografi (6), dan riwayat studi (3). Target cukup seimbang, 52,7% berisiko dan 47,3% tidak. Karena itu tidak perlu oversampling seperti SMOTE; yang perlu disetel adalah ambang keputusannya (dibahas di slide 15).

Kenapa F1? Karena yang penting adalah kelas berisiko. F1 menyeimbangkan dua pertanyaan: dari yang kami tandai, berapa yang benar (precision), dan dari yang benar-benar berisiko, berapa yang tertangkap (recall).

**Pesan untuk juri.** Kami tahu persis data apa yang dipakai dan kenapa metriknya F1.

### Slide 5 · Alur Kerja

**Isi slide.** Delapan kotak berurutan: Dataset → Pembersihan → Penanda data → Rekayasa fitur → Validasi → Tiga GBDT → Ambang 0,40 → Insight.

**Penjelasan.** Ini peta seluruh pekerjaan. Langkah 2 dan 3 (membersihkan data dan menandai angka pengganti) dibahas di EDA. Langkah 4 sampai 7 (fitur, validasi, model, ambang) dibahas di Pemodelan. Langkah 8 (tingkat risiko, rencana aksi, Pelita Belajar) dibahas di Business Insight. Slide ini membantu juri tahu ke mana presentasi bergerak.

**Pesan untuk juri.** Pekerjaan kami sistematis, dari data mentah sampai keputusan.

---

## Bagian 2 · EDA

Bagian ini bukan sekadar menampilkan grafik. Setiap temuan EDA menjadi **dasar pemilihan fitur dan model**, dan itulah yang membuatnya ikut dinilai di aspek justifikasi model (40%).

### Slide 6 · Kualitas Data

**Isi slide.** Tabel sebelum → sesudah: kode modul uji `GGG` (372 baris) → `M07`; `M04` di blok M07 (145 baris) → `M07`; `Region 3`/`region2` → `Region3`/`Region2`; `A Level`/`A level` → `A Level`; kolom konstan `submitted_Assessment_1/2` → dibuang. Kotak bawah: GGG terbukti M07, label tidak diubah, tidak ada baris dibuang, tanpa data eksternal.

**Penjelasan.**
- **GGG.** Kode modul GGG hanya ada di data uji. Bukti bahwa itu M07:
  - kombinasi periode dan panjang modulnya persis M07 (261, 241, 269 hari);
  - rasio jumlah baris uji/latih M07 baru wajar setelah GGG digabung.

  Kalau tidak diperbaiki, model memperlakukan 372 baris ini sebagai modul asing.
- **Kode terselip.** Menurut urutan `id`, 145 baris latih bertuliskan modul lain berada di tengah blok M07 (rinciannya: 144 baris `M04_P22` dan 1 baris `M05_P12`).
- **Kategori dan kolom konstan.** Penulisan kategori disamakan supaya satu kategori tidak terpecah dua. Kolom konstan dibuang karena tidak membawa informasi.

Semua perbaikan ini tidak menyentuh label, tidak membuang baris, dan tidak memakai data luar, sesuai aturan lomba.

Di naskah juga disebut temuan yang paling berpengaruh: **angka pengganti**. Sebanyak 3.738 baris punya aktivitas persis sama, yaitu 182 klik, 10 hari aktif, dan 20 situs. Saat nilai asesmen belum ada, kolom nilainya terisi 77. Ini isian otomatis untuk mahasiswa tanpa catatan, bukan perilaku asli. Angka ini ditandai lalu dikosongkan, sehingga model belajar dari fakta "tidak ada aktivitas", bukan dari angka 182.

**Pesan untuk juri.** Sebelum memodelkan, kami memastikan data jujur, dengan bukti untuk setiap perbaikan.

### Slide 7 · Sinyal 1: Tugas Pertama

**Isi slide.** Grafik batang: 94,0% berisiko bila tidak mengumpulkan tugas sampai batas waktu (n = 5.714) vs 41,1% bila mengumpulkan (n = 20.372). Angka besar 94,0%. Kotak "Artinya": tenggat tugas pertama adalah titik intervensi yang tanggalnya sudah pasti.

**Penjelasan.** Ini sinyal paling tegas di seluruh data. Bedanya lebih dari dua kali lipat (94% vs 41%), dan kelompoknya besar: 5.714 mahasiswa, sekitar satu dari lima. Sinyal ini juga menjadi **fitur terpenting model** (`no_submission_by_cutoff`, 18,5% gain), jadi EDA dan model saling mengonfirmasi.

Untuk bisnis, nilainya ada pada waktu: tanggal tenggat sudah diketahui sejak awal semester, jadi kampus bisa menjadwalkan pengingat sebelum tenggat dan tindak lanjut sesudahnya.

**Pesan untuk juri.** Sinyal terkuat muncul di tanggal yang bisa direncanakan.

### Slide 8 · Sinyal 2: Aktivitas Daring

**Isi slide.** Kiri: median klik per minggu, mahasiswa tidak berisiko 50 · 46 · 62 · 43, mahasiswa berisiko 22 · 17 · 29 · 14. Kanan: proporsi berisiko menurut hari aktivitas terakhir, 85% (hari 0–6), 75%, 62%, 51%, sampai 38% (hari 25–28). Tiga kartu: 95,2% · 22 vs 50 · 85%. Kotak "Artinya": login dan klik bisa dipantau otomatis setiap minggu.

**Penjelasan.** Ada tiga lapis temuan:
1. Mahasiswa yang **tidak pernah** membuka kelas daring (kelompok angka pengganti tadi): 95,2% berisiko, vs 45,6% yang aktif.
2. Di antara yang aktif pun, mahasiswa berisiko hanya membuka kelas sekitar setengahnya (22 vs 50 klik di minggu 1), dan jaraknya bertahan sampai minggu ke-4.
3. **Kapan terakhir aktif** sangat informatif. Yang menghilang di minggu pertama, 85%-nya berisiko. Fitur ini (`last_activity_day`) menjadi **fitur terpenting kedua** di model (9,1%).

**Pesan untuk juri.** Perilaku daring adalah sinyal mingguan yang bisa dipantau otomatis, tanpa menunggu nilai.

### Slide 9 · Sinyal 3: Kelas & Latar Belakang

**Isi slide.** Grafik proporsi berisiko di 22 kelas modul-periode, dari 28% (M01_P12) sampai 65% (M03_P21), dengan garis rata-rata 52,7%. Tiga kartu: kelas 28%–65%, pendidikan 32% (pascasarjana) vs 70% (tidak tercatat), kemiskinan wilayah 42% (terkaya) vs 65% (termiskin). Kotak "Artinya": konteks perlu dihitung, tetapi belum menjelaskan kenapa.

**Penjelasan.** Risiko tidak merata. Modul tertentu (M03, M06) jauh di atas rata-rata, dan latar belakang juga terlihat berpengaruh. Karena itu `code_module` tetap dipakai, dan menjadi fitur terpenting ketiga (6,2%). Namun konteks hanya menjawab *siapa* yang lebih berisiko, belum *kenapa*. Pertanyaan "kenapa" dijawab di slide berikutnya.

**Pesan untuk juri.** Kami tidak berhenti di korelasi demografis. Kami mencari penyebab yang bisa ditindaklanjuti.

### Slide 10 · Dua Perilaku

**Isi slide.** Matriks 2×2 (tugas pertama terlewat/dikumpulkan × aktif/tak pernah membuka kelas daring): 98,8% (3.045 mhs) · 88,5% (2.669) · 79,6% (692) · 39,8% (19.680). Di kanan: dua aturan sederhana menandai 25% mahasiswa, 92% tepat sasaran, menangkap 43% yang berisiko. Kotak: 57% yang berisiko ada di sel biru, tampak normal, sehingga dibutuhkan model.

**Penjelasan.** Ketika dua sinyal disilangkan, polanya jelas. Yang melewatkan tugas **dan** tidak membuka kelas daring hampir pasti berisiko (98,8%). Masalah utamanya adalah **keterlibatan di awal semester**.

Dua aturan sederhana ("tugas terlewat **atau** tak pernah membuka kelas") sudah sangat tepat (92%) dan bisa dipakai kampus besok tanpa model. Tetapi aturan ini hanya menangkap 43% mahasiswa berisiko. Sisanya, 57%, berada di sel biru: mereka mengumpulkan tugas dan aktif, tetapi tetap berisiko. Untuk menemukan mereka dibutuhkan kombinasi puluhan sinyal yang lebih halus, dan itulah tugas model.

Catatan kejujuran: ini asosiasi yang sangat kuat, belum tentu sebab-akibat. Karena itu rencana 90 hari memakai kelompok pembanding (slide 20).

**Pesan untuk juri.** EDA tidak hanya menemukan pola; EDA membuktikan kenapa model dibutuhkan. Ini jembatan ke bagian Pemodelan.

---

## Bagian 3 · Pemodelan

Bagian ini menjawab aspek dengan bobot terbesar, **Analisis & Justifikasi Model (40%)**. Kuncinya: setiap pilihan punya alasan dan pembanding.

### Slide 11 · Siklus Mengulang

**Isi slide.** Kiri: sebaran pasangan kandidat antara M02 P12 dan M02 P22. Titik oranye (orang yang sama) membentuk kurva; titik abu-abu (profil sama secara kebetulan) tersebar acak. Tengah: proporsi berisiko catatan pertama menurut jarak ke kurva, 92% · 74% · 62% · 54% · 50%. Kanan: 92%, dan "tanpa fitur ini model melewatkan 21% pengulang; dengan fitur ini 4%". Bawah: tiga ciri, yaitu profil identik dengan percobaan naik satu, urutan baris membentuk kurva, dan hanya memakai kolom yang ada.

**Penjelasan.** Ini fitur kunci kami dan temuan paling orisinal.
- Data tidak punya ID mahasiswa, tetapi urutan baris di setiap blok modul-periode ternyata konsisten.
- Ambil dua catatan dengan profil identik (gender, wilayah, pendidikan, usia, dan seterusnya), modul sama, periode berurutan, dan `num_of_prev_attempts` naik satu. Kalau keduanya orang yang sama, posisi barisnya di blok masing-masing sejalan dan membentuk kurva.
- Pasangan yang hanya kebetulan mirip tidak membentuk pola. Itu bukti bahwa tautannya nyata.

Kenapa penting? Orang mengulang biasanya karena gagal. Jadi catatan pertama dari mahasiswa yang nanti mengulang 92% berisiko, jauh di atas rata-rata 53%, dan semakin dekat ke kurva semakin pasti. Dengan fitur ini, pengulang yang terlewat model turun dari 21% ke 4%.

**Batas yang harus diakui sendiri.** Sebagian informasi ini baru ada di periode berikutnya (fakta bahwa mahasiswa mendaftar ulang). Fitur ini sah dalam kompetisi karena hanya memakai kolom dari panitia, tanpa label dan tanpa data luar. Tetapi untuk peringatan dini di kampus, skor minggu ke-4 memakai **model tanpa fitur ini**. Model itulah yang dipakai di segmentasi risiko (slide 17).

**Pesan untuk juri.** Kami menemukan informasi tersembunyi secara kreatif, dan jujur soal batas pemakaiannya.

### Slide 12 · Skema Validasi

**Isi slide.** Ilustrasi 10 bagian data: di setiap fold, 9 bagian untuk latih (biru) dan 1 untuk validasi (oranye), sampai fold 10 menghasilkan prediksi out-of-fold (OOF). Stratified 10-fold, diulang dengan seed 42, 7, dan 2026. Rumus precision, recall, dan F1.

**Penjelasan.** Validasi ini menjawab pertanyaan "seberapa bagus model untuk data yang belum pernah dilihat?"
- **Stratified** berarti proporsi berisiko di setiap bagian sama dengan keseluruhan data.
- Setiap baris mendapat prediksi dari model yang tidak dilatih dengan baris itu, yang disebut prediksi **OOF**. Jadi skor validasi adalah skor jujur di 26.086 baris.
- Diulang dengan tiga seed karena hasil satu pembagian bisa kebetulan; rata-rata beberapa pembagian lebih stabil.

Semua keputusan (fitur, model, ambang) diambil dari skor OOF ini, bukan dari leaderboard.

**Pesan untuk juri.** Angka kami bisa dipercaya karena diuji dengan cara yang ketat.

### Slide 13 · Proses Pencarian Model

**Isi slide.** Grafik F1 public di setiap langkah:

| Langkah | F1 public | Kenaikan |
|---|---|---|
| Gabungan 3 GBDT + pembersihan kategori | 0,78704 | |
| + tautan mahasiswa mengulang | 0,79227 | +0,0052 |
| + perbaikan modul terselip, tautan per himpunan | 0,80018 | +0,0079 |
| Final: penanda angka pengganti, 10-fold × 3 seed | 0,80074 | +0,0006 |

Total kenaikan +0,0137. Kotak "Dicoba, tidak dipakai": tuning Optuna, ExtraTrees, RandomForest, HistGB, MLP, dan pseudo-label, semuanya hanya bergeser ±0,001 F1. Kesimpulan: kami pilih model yang sederhana dan stabil.

**Penjelasan.** Slide ini menunjukkan *proses* pencarian model terbaik, yang diminta panduan lomba. Dua lompatan terbesar datang dari **memahami data**: tautan mengulang dan perbaikan kode modul. Lompatannya tidak datang dari algoritma yang lebih rumit.

Sebaliknya, semua upaya teknis (tuning, model tambahan, pseudo-label) hanya menggeser skor sekitar seperseribu, setara derau. Itu tanda model sudah jenuh dengan informasi empat minggu pertama. Karena itu kami memilih model yang sederhana: lebih mudah dijelaskan, direproduksi, dan dipelihara kampus.

**Pesan untuk juri.** Kami tahu dari mana kenaikan skor berasal, dan tahu kapan harus berhenti mengejar angka.

### Slide 14 · Pemilihan Model

**Isi slide.** Grafik F1 OOF terbaik per kandidat:

| Model | F1 OOF |
|---|---|
| Regresi logistik (baseline) | 0,77315 |
| CatBoost | 0,77967 |
| XGBoost | 0,77961 |
| LightGBM | 0,78000 |
| **Gabungan 3 model** | **0,78044** |

Kotak "Kenapa GBDT?": menangani nilai kosong hasil penandaan, menangkap ambang non-linier seperti tenggat terlewat, dan menemukan interaksi antar-fitur secara otomatis.

**Penjelasan.**
- **Baseline** regresi logistik dipakai sebagai pembanding yang sederhana dan mudah dijelaskan. Ketiga GBDT (gradient boosted decision trees) mengalahkannya.
- **Kenapa GBDT cocok untuk data ini:**
  - nilai kosong dari angka pengganti yang dikosongkan bisa ditangani langsung;
  - hubungan yang berupa ambang, seperti "lewat tenggat atau tidak", mudah ditangkap pohon keputusan;
  - interaksi antar-fitur, seperti tugas terlewat dan tidak aktif sekaligus, ditemukan otomatis.
- **Gabungan tiga model** dibuat dengan merata-ratakan probabilitasnya. Kenaikannya dari LightGBM memang kecil (+0,0004). Alasan utamanya kestabilan: setiap algoritma membuat kesalahan yang sedikit berbeda, dan rata-ratanya saling menutupi.

**Pesan untuk juri.** Pilihan model kami beralasan, dibandingkan dengan baseline, dan tidak dilebih-lebihkan.

### Slide 15 · Evaluasi Model

**Isi slide.** Matriks kebingungan (OOF, ambang 0,40): TN 8.650 (70,1%) · FP 3.683 (29,9%) · FN 2.595 (18,9%) · TP 11.158 (81,1%). Precision 75,2%, recall 81,1%. Ambang 0,50 → F1 0,77136; ambang 0,40 (dipilih) → F1 0,78044; F1 hampir sama di ambang 0,36–0,42. Public leaderboard 0,80074. Dua kotak: 4 dari 5 mahasiswa berisiko sudah tertangkap di minggu ke-4, dan lebih baik salah mengingatkan (FP) daripada melewatkan (FN).

**Penjelasan.**
- **Cara membaca matriksnya.** Dari 13.753 mahasiswa yang benar-benar berisiko, 11.158 tertangkap (recall 81,1%) dan 2.595 terlewat. Dari 12.333 yang aman, 3.683 ikut ditandai.
- **Kenapa ambang 0,40, bukan 0,50.** Model menghasilkan skor 0–1, dan ambang menentukan kapan skor dianggap "berisiko". Ambang 0,50 bukan aturan wajib. Di ambang 0,40, F1 naik dari 0,771 ke 0,780.
- **Pilihan ini tidak rapuh.** F1 hampir sama di seluruh rentang 0,36–0,42, jadi ambangnya tidak dipilih secara kebetulan.
- **Pilihan ini masuk akal secara bisnis.** Salah mengingatkan mahasiswa yang ternyata aman hanya berbiaya satu pesan, sedangkan melewatkan mahasiswa berisiko bisa berujung mundur.
- **Biaya salah sasaran ditekan lewat tingkat risiko.** Precision 75% berarti satu dari empat yang ditandai sebenarnya aman. Biaya itu dikelola di bagian berikutnya: kontak mahal hanya untuk tingkat tinggi.

**Pesan untuk juri.** Kami memilih ambang berdasarkan data dan biaya kesalahan, bukan kebiasaan.

### Slide 16 · Fitur Terpenting

**Isi slide.** 15 fitur terpenting LightGBM (porsi gain), dengan fitur asesmen berwarna oranye dan aktivitas & konteks berwarna biru:

| Fitur | Porsi gain |
|---|---|
| `no_submission_by_cutoff` | 18,5% |
| `last_activity_day` | 9,1% |
| `code_module` | 6,2% |
| `avg_score` | 4,1% |
| `week4_interactions` | 3,8% |
| … | … |
| `region`, `edu_ord` | 1,7% masing-masing |

Angka besar 30,1%: gain model berasal dari fitur asesmen, lalu aktivitas. Kotak: demografi hanya 1,7%; kabar baiknya, perilaku bisa diubah lewat intervensi.

**Penjelasan.** Slide ini menutup lingkaran EDA → model. Dua sinyal terkuat di EDA (tugas pertama dan hari aktif terakhir) memang menjadi dua fitur terpenting model.

Yang menarik: latar belakang yang di EDA terlihat berpengaruh (pendidikan 32% vs 70%) hampir tidak dipakai model. Ini bukan kontradiksi. Latar belakang berkorelasi dengan perilaku, jadi setelah perilaku diketahui, tambahan informasi dari latar belakang kecil.

Implikasinya penting untuk bisnis: yang menentukan adalah **apa yang dilakukan mahasiswa**, dan itu bisa diubah lewat intervensi. Latar belakang tidak bisa diubah.

**Pesan untuk juri.** Model kami bisa dijelaskan, dan penjelasannya mengarah langsung ke tindakan.

---

## Bagian 4 · Business Insight

Bagian ini menjawab **Prescriptive Insight (35%)**: rekomendasi dan tindakan berbasis hasil prediksi.

### Slide 17 · Segmentasi Risiko

**Isi slide.** Grafik proporsi berisiko aktual per tingkat: rendah 24% (n = 11.152), sedang 54% (n = 7.188), tinggi 93% (n = 7.746). Tabel tingkat, porsi, berisiko, dan tindakan. Kotak: tingkat tinggi saja sudah mencakup 52% dari semua mahasiswa berisiko. Catatan: skor dari model versi minggu ke-4 (tanpa fitur tautan), prediksi out-of-fold data latih.

**Penjelasan.** Skor 0–1 sulit dipakai tutor, jadi kami ubah menjadi tiga tingkat:

| Tingkat | Batas skor | Porsi mahasiswa | Benar berisiko | Tindakan |
|---|---|---|---|---|
| Tinggi | ≥ 0,75 | 30% | 93% | Kontak tutor personal minggu ini |
| Sedang | 0,40–0,75 | 28% | 54% | Pengingat otomatis, pantau mingguan |
| Rendah | < 0,40 | 43% | 24% | Tanpa intervensi khusus |

Batas 0,40 berasal dari ambang F1 terbaik. Batas 0,75 memberi kelompok sekitar 30% mahasiswa yang hampir semuanya memang berisiko, ukuran yang realistis untuk kontak personal.

Angka-angkanya dari model tanpa fitur tautan, jadi bisa dijalankan tepat di minggu keempat. Tindakannya sengaja dibedakan per tingkat: yang mahal untuk yang paling membutuhkan, yang murah untuk yang masih abu-abu.

**Pesan untuk juri.** Prediksi kami langsung bisa dipakai, dan setiap tingkat punya tindakan yang sesuai biaya.

### Slide 18 · Kapasitas Tutor

**Isi slide.** Kurva kapasitas: sumbu bawah adalah persentase mahasiswa yang dihubungi (urut skor tertinggi). Garis oranye: yang dihubungi memang berisiko (98% di 20%, 93% di 30%). Garis biru: mahasiswa berisiko yang terjangkau (37% di 20%, 53% di 30%). Angka besar 98%. Kotak: kampus cukup memilih berapa banyak yang sanggup dihubungi; urutan skor menentukan siapa.

**Penjelasan.** Pertanyaan paling realistis dari kampus: tutor kami terbatas, lalu bagaimana? Kurva ini menjawab untuk kapasitas berapa pun.
- Kalau tutor hanya sanggup menghubungi 1 dari 5 mahasiswa, 98% yang dihubungi memang berisiko, jadi hampir tidak ada waktu terbuang.
- Kalau sanggup 30%, ketepatan masih 93% dan lebih dari separuh mahasiswa berisiko terjangkau.

Dua garis itu menunjukkan tarik-menarik yang jujur: makin banyak yang dihubungi, makin banyak yang terjangkau, tetapi ketepatannya turun.

**Pesan untuk juri.** Rekomendasi kami fleksibel terhadap sumber daya nyata kampus.

### Slide 19 · Rencana Aksi

**Isi slide.** Tabel pemicu → tindakan → kapan → ukuran keberhasilan:

| Pemicu dari data | Tindakan | Kapan | Ukuran keberhasilan |
|---|---|---|---|
| Tidak aktif daring minggu 1–2 (EDA sinyal 2) | Telepon orientasi: cek akses, jadwal, motivasi | Minggu 2 | % yang mulai aktif dalam 7 hari |
| Tugas pertama belum dikumpulkan (EDA sinyal 1) | Pengingat H-3; tutor menghubungi ≤ 48 jam setelah tenggat | Minggu 3–4 | % yang akhirnya mengumpulkan |
| Skor tingkat tinggi (segmentasi risiko) | Pendampingan dan rencana belajar personal | Minggu 4 | % yang turun ke tingkat sedang atau rendah |
| Mendaftar ulang modul yang sama (fitur pola mengulang) | Mentor sejak registrasi ulang | Saat registrasi | Tingkat lulus mahasiswa pengulang |
| Modul berisiko tinggi M03, M06 (risiko per modul) | Tinjau beban dan jadwal tugas awal | Tiap semester | Proporsi berisiko per modul |

Bawah: tindakan murah (pengingat otomatis) untuk banyak mahasiswa → tindakan mahal (tutor personal) hanya untuk tingkat tinggi.

**Penjelasan.** Setiap baris punya empat unsur yang membuat rekomendasi bisa dijalankan dan dinilai: pemicu dari data, tindakan spesifik, waktu, dan ukuran keberhasilan. Setiap pemicu juga ditelusuri balik ke temuan sebelumnya, jadi tidak ada rekomendasi yang muncul tanpa dasar.

Tindakannya tidak hanya untuk mahasiswa. Ada juga tindakan di tingkat modul (M03, M06), karena sebagian risiko berasal dari desain mata kuliahnya. Satu hal yang bisa ditambahkan secara lisan bila ditanya: siapa pelaksananya.
- Tutor atau dosen wali untuk kontak personal.
- Bagian akademik atau pengelola LMS untuk pengingat otomatis.
- Koordinator modul untuk peninjauan beban tugas.

**Pesan untuk juri.** Rekomendasi kami spesifik, terjadwal, dan terukur, bukan saran umum.

### Slide 20 · Dampak & Langkah 90 Hari

**Isi slide.** Tiga angka: 52% mahasiswa berisiko terjangkau dengan menghubungi 30% teratas · 98% waktu tutor tepat sasaran bila kapasitas hanya 20% · 43% tertangkap dengan 2 aturan, bisa dimulai besok tanpa model. Langkah 90 hari: Pilot (hari 0–30) → Uji (31–60) → Perluas (61–90) → Berkelanjutan.

**Penjelasan.**
- **Dampaknya lebih mudah dibayangkan per 1.000 mahasiswa.** Tutor cukup menghubungi 300 orang, dan 278 di antaranya memang berisiko. Itu separuh dari semua yang berisiko, terjangkau di minggu keempat, saat bantuan masih bisa mengubah hasil.
- **Langkah 90 hari sengaja dimulai kecil.** Pilot di satu atau dua modul berisiko tinggi (misalnya M03), dengan tutor dilatih memakai daftar prioritas.
- **Bulan kedua adalah bagian terpenting.** Mahasiswa yang diintervensi dibandingkan dengan kelompok pembanding. Hanya dengan cara ini kampus tahu bahwa intervensinya yang mengubah hasil, bukan kebetulan. Ini juga menjawab keterbatasan bahwa temuan EDA adalah asosiasi.
- **Bulan ketiga dan seterusnya.** Evaluasi kelulusan dan pengunduran diri, lalu perluasan ke semua modul. Setelah itu skor diperbarui tiap minggu dan model dilatih ulang tiap periode.

**Pesan untuk juri.** Kami tidak hanya menjanjikan dampak; kami punya cara membuktikannya.

### Slide 21 · Demo: Pelita Belajar

**Isi slide.** Nama aplikasi, tagline "dari skor risiko ke daftar mahasiswa yang perlu dibantu lebih dulu", kode QR, tautan pelita-belajar.vercel.app, dan tampilan aplikasi ("Modelnya sudah ada. Lalu apa?").

**Penjelasan.** Pelita Belajar adalah jembatan dari model ke tutor. Menunya ada empat:
- **Ringkasan:** gambaran risiko mahasiswa.
- **Data Belajar:** catatan belajar tiap mahasiswa.
- **Analisis CSV:** kampus mengunggah data baru.
- **Panduan Tutor:** tindakan untuk setiap tingkat, sama dengan rencana aksi.

Dengan aplikasi ini tutor tidak perlu memahami model. Ia cukup membuka daftar dan tahu siapa dihubungi lebih dulu. Kode QR membuat juri bisa mencobanya langsung.

Siapkan jawaban jujur: apakah skor sudah dihitung langsung di aplikasi, atau aplikasinya masih prototipe yang menampilkan hasil model.

**Pesan untuk juri.** Solusi kami bisa dipakai hari ini, bukan hanya angka di notebook.

---

## Bagian 5 · Kesimpulan

### Slide 22 · Kesimpulan

**Isi slide.** Empat poin bernomor dan satu kotak batas:
1. **Masalah:** satu dari dua mahasiswa berisiko, dan datanya perlu dibaca jujur.
2. **Akar masalah:** perilaku awal (tugas dan aktivitas daring) dan siklus mengulang, bukan latar belakang.
3. **Model:** gabungan tiga GBDT, F1 OOF 0,78044, public 0,80074, recall 81%.
4. **Tindakan:** tiga tingkat risiko dan Pelita Belajar; 30% teratas, 93% tepat sasaran.

**Batas:** 19% mahasiswa berisiko tetap berskor rendah di minggu ke-4 · M07 paling sulit (AUC 0,70) · fitur tautan butuh data periode berikutnya.

**Penjelasan.** Empat poin ini mengulang alur presentasi dalam satu tarikan napas. Menyebut batas di akhir adalah sikap yang disengaja:
- Sebagian mahasiswa baru bermasalah setelah minggu keempat, dan solusinya adalah skor yang diperbarui setiap minggu.
- M07 paling sulit diprediksi.
- Fitur tautan tidak dipakai untuk peringatan dini.

Tim yang menyebut kelemahannya sendiri biasanya lebih dipercaya daripada tim yang terlihat sempurna.

**Pesan untuk juri.** Kesimpulan kami ringkas, konsisten dengan seluruh presentasi, dan jujur.

### Slide 23 · Terima Kasih

**Isi slide.** "Terima Kasih!", kalimat penutup "Data 4 minggu sudah cukup untuk menolong mahasiswa lebih dulu", foto tim, dan "siap menerima pertanyaan".

**Penjelasan.** Penutup kembali ke cerita tutor di slide pertama: ia tidak perlu menunggu nilai akhir, karena data empat minggu sudah cukup untuk menolong lebih dulu. Mengulang cerita pembuka membuat presentasi terasa utuh. Setelah ucapan terima kasih, tutup dengan salam lintas agama (atau pindahkan salam ke akhir sesi tanya jawab).

**Pesan untuk juri.** Satu kalimat yang diingat: data empat minggu sudah cukup untuk bertindak.

---

## Lima kalimat yang harus diingat juri

1. Satu dari dua mahasiswa berisiko, dan tandanya sudah terlihat di empat minggu pertama.
2. Tugas pertama yang terlewat dan kelas daring yang tidak dibuka adalah tanda paling kuat; berdua, 98,8% berisiko.
3. Lompatan skor terbesar datang dari memahami data, bukan dari model yang lebih rumit.
4. Perilaku, bukan latar belakang, yang menentukan, dan perilaku bisa diubah.
5. Hubungi 30% teratas, dan 93% yang dihubungi memang membutuhkan bantuan.

## Catatan sebelum tampil

- Angka model di slide (0,78044, 0,80074, 10-fold × 3 seed) harus sama dengan notebook yang dikumpulkan. Notebook final di repo saat ini menunjukkan CV 0,7787 dan public 0,79981 (lihat `docs/06_briefing_final.md`, bagian 9).
- Angka segmentasi, kapasitas, matriks dua sinyal, dan "300 → 278" adalah hasil analisis ulang. Cocokkan dengan notebook tim.
- Perbaikan kecil di PPT: label "Precision"/"Recall" di slide 15, dan sorotan tab footer di slide 21.
