# DSCO 2026 — Data Science Club Olympiads (Binus University)

Tema: **Beyond the Data Horizon: Decoding the Future of Education**

Tugas: memprediksi apakah seorang mahasiswa **berisiko** (`at_risk` = 0/1) dari data demografi, asesmen, dan aktivitas belajar daring. Metrik: **F1 score**.

## Tanggal penting

| Tanggal | Agenda |
|---|---|
| 3 – 31 Okt 2026 | Babak penyisihan di Kaggle (maks. 3 submission/hari) |
| 1 Nov 2026, 23:59 WIB | Deadline form notebook + CSV (top 15 private LB) |
| 5 Nov 2026 | Pengumuman 10 finalis |
| 27 Nov 2026 | Final (presentasi) & awarding |

## Aturan inti

- Hanya data panitia — **tanpa data eksternal**.
- **Tanpa AutoML**, **tanpa model pre-trained**, **tanpa ubah label manual**.
- Python saja. Augmentasi dari data sendiri dan pseudo-labelling **boleh**.
- Hanya akun **ketua** yang submit.
- Notebook final harus bisa **Run All**, baca CSV tanpa direktori, dan hasilnya cocok dengan CSV yang disubmit.

Detail lengkap ada di `docs/`.

## Struktur folder

```
dscobinus/
├── README.md
├── requirements.txt
├── data/
│   ├── raw/            # train.csv, test.csv, sample_submission.csv (jangan diedit)
│   └── processed/      # hasil preprocessing (bisa dibuat ulang)
├── docs/
│   ├── Guidebook DSCO 2026.pdf
│   ├── 01_aturan_kompetisi.md
│   ├── 02_faq_technical_meeting.md
│   ├── 03_timeline.md
│   ├── 04_dataset.md
│   └── 05_checklist_submission.md
├── notebooks/          # 01_eda → 99_final_submission
├── src/                # fungsi bantu untuk eksperimen (bukan untuk notebook final)
├── models/             # model / artefak tersimpan
├── submissions/        # CSV submission + log skor
└── reports/
    └── figures/        # grafik untuk PPT final
```

## Dokumen

| File | Isi |
|---|---|
| [docs/01_aturan_kompetisi.md](docs/01_aturan_kompetisi.md) | Aturan lengkap, larangan, format submission, babak final, rubrik |
| [docs/02_faq_technical_meeting.md](docs/02_faq_technical_meeting.md) | Tanya jawab technical meeting + implikasinya |
| [docs/03_timeline.md](docs/03_timeline.md) | Jadwal dan anggaran submission |
| [docs/04_dataset.md](docs/04_dataset.md) | Deskripsi dataset, kelompok fitur, temuan kualitas data |
| [docs/05_checklist_submission.md](docs/05_checklist_submission.md) | Checklist sebelum submit dan sebelum pengumpulan |
| [docs/06_briefing_final.md](docs/06_briefing_final.md) | Briefing babak final: angka kunci, notebook, struktur PPT, naskah 13 menit, bank tanya jawab, checklist hari-H |
| [docs/07_latihan_tanya_jawab.md](docs/07_latihan_tanya_jawab.md) | 60 pertanyaan latihan tanya jawab final + kunci jawaban, rantai pertanyaan lanjutan, cara latihan |
| [submissions/README.md](submissions/README.md) | Log setiap submission |

## Setup

```bash
pip install -r requirements.txt
```
