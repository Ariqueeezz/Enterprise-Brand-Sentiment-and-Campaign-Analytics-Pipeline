## DoD Summary — User Story 1
**"Sebagai Data Engineer, saya ingin memproses dataset ulasan skala masif menggunakan PySpark agar tidak terkendala limitasi memori."**

**Dataset:** Amazon Reviews 2023 (McAuley Lab) — Kategori: Electronics
**Environment:** Google Colab + Google Drive
**Sumber data:** https://mcauleylab.ucsd.edu/public_datasets/data/amazon_2023/raw/review_categories/Electronics.jsonl.gz

---

### Task 1.1 — Download & Standarisasi Dataset

| No. | Kriteria DoD | Status | Keterangan |
|-----|--------------|--------|------------|
| 1 | Dataset ulasan publik terstruktur | ✅ Done | Amazon Reviews 2023, format `.jsonl.gz` |
| 2 | Ukuran dataset > 5 GB | ✅ Done | 6.03 GB |
| 3 | Memiliki fitur teks (ulasan) | ✅ Done | Field `title`, `text` |
| 4 | Memiliki label (rating/bintang) | ✅ Done | Field `rating` (1.0–5.0) |
| 5 | Tersimpan aman & siap diakses skrip | ✅ Done | Google Drive, dapat diakses via `spark.read.json()` |

### Task 1.2 — Setup PySpark Session & Sinkronisasi Skema

| No. | Kriteria DoD | Status | Keterangan |
|-----|--------------|--------|------------|
| 1 | PySpark session berhasil diinisialisasi | ✅ Done | Konfigurasi driver memory 8g, shuffle partitions disesuaikan |
| 2 | Skema data didefinisikan eksplisit (bukan auto-infer) | ✅ Done | `StructType` mencakup 10 field (rating, title, text, dll.) |
| 3 | Data berhasil dibaca sesuai skema tanpa error | ✅ Done | Divalidasi via `df.printSchema()` & `df.show()` |
| 4 | DataFrame siap digunakan untuk tahap EDA/preprocessing berikut | ✅ Done | Di-cache untuk efisiensi query Task 1.3 |

### Task 1.3 — EDA Terdistribusi via Spark SQL

| No. | Kriteria DoD | Status | Keterangan |
|-----|--------------|--------|------------|
| 1 | Distribusi rating (class imbalance) teridentifikasi | ✅ Done | Query agregasi per rating 1.0–5.0 |
| 2 | Missing/null values per kolom teridentifikasi | ✅ Done | Cek null count seluruh kolom |
| 3 | Statistik word count (min/max/avg/median) tersedia | ✅ Done | Basis penentuan `max_length` tokenizer di EPIC-2 |
| 4 | Insight word count per rating tersedia | ✅ Done | Analisis tambahan pola panjang review vs rating |
| 5 | Visualisasi ringan dari hasil agregasi | ✅ Done | Bar chart distribusi rating (data teragregasi, bukan raw) |

---

### Kesimpulan
**User Story 1 — DONE ✅**
Seluruh task (1.1, 1.2, 1.3) telah diselesaikan dan divalidasi. Dataset siap dilanjutkan ke **Story 2: Pipeline Pembersihan Teks Scalable** (Task 2.1–2.2).

### Catatan Pembelajaran (Opsional — untuk portofolio/skripsi)
- Pengalaman pertama menggunakan PySpark: instalasi, konfigurasi session, dan query Spark SQL di lingkungan Google Colab.
- Insight kunci dari EDA akan dipakai untuk keputusan desain di EPIC-2 dan EPIC-3 (contoh: distribusi rating memengaruhi strategi class weighting saat training model).