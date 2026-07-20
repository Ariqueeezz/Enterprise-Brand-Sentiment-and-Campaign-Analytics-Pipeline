## DoD Check — Sub-Task (EBSCAP-3): Download & Standarisasi Dataset Skala Besar

**Link JIRA**: https://raihanariq395.atlassian.net/browse/EBSCAP-3

**Dataset:** Amazon Reviews 2023 (McAuley Lab) — Kategori: Electronics

**Sumber:** https://mcauleylab.ucsd.edu/public_datasets/data/amazon_2023/raw/review_categories/Electronics.jsonl.gz

**Lokasi penyimpanan:** Google Drive — `/skripsi-project/data/raw/Electronics.jsonl.gz`

| No. | Kriteria DoD | Status | Keterangan |
|-----|--------------|--------|------------|
| 1 | Dataset ulasan publik terstruktur | ✅ Done | Amazon Reviews 2023, format `.jsonl.gz` |
| 2 | Ukuran dataset > 5 GB | ✅ Done | 6.03 GB |
| 3 | Memiliki fitur teks (ulasan) | ✅ Done | Field `title`, `text` |
| 4 | Memiliki label (rating/bintang) | ✅ Done | Field `rating` (1.0–5.0) |
| 5 | Tersimpan aman di storage yang siap diakses skrip | ✅ Done | Google Drive, dapat diakses via `spark.read.json()` |

**Kesimpulan:** Task 1.1 — **DONE** ✅