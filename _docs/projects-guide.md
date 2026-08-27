---
title: "Panduan Pembaruan Halaman Projects"
subtitle: "Lab Data dan Komputasi Geoteknik — lab-datageo.github.io"
date: "Mei 2026"
---

# Panduan Pembaruan Halaman Projects

**Situs:** lab-datageo.github.io  
**Halaman:** /projects  
**Diperbarui:** Mei 2026

---

## Gambaran Umum Sistem

Halaman Projects menggunakan dua jalur input tergantung apakah proyek memerlukan halaman detail atau tidak.

| Jenis Proyek | Di mana input | Butuh file baru? |
|---|---|---|
| **Proyek biasa** (hanya muncul di tabel) | `_data/projects.yml` | Tidak — cukup tambah baris di file yang sudah ada |
| **Proyek unggulan** (punya halaman detail/studi kasus) | `_projects/TANGGAL-nama.md` | Ya — buat file baru |

Sebagian besar proyek cukup dimasukkan sebagai **proyek biasa**. Proyek unggulan hanya untuk proyek yang perlu ditampilkan secara lengkap sebagai studi kasus.

---

## Bagian 1 — Menambah Proyek Biasa

Proyek biasa **hanya muncul di tabel** pada halaman Projects. Cara inputnya sangat sederhana: cukup buka satu file YAML dan tambahkan beberapa baris.

### Langkah-langkah

1. Buka file **`_data/projects.yml`** menggunakan teks editor (Notepad, VS Code, dll.)
2. Gulir ke bawah hingga akhir file
3. Tambahkan entri baru dengan format berikut:

```yaml
- title: "Judul Proyek"
  date: "YYYY-MM-DD"
  client: "Nama Klien"
  service_type: "Slope Stability"
  market_sector: "Infrastructure"
  keywords:
    - kata kunci 1
    - kata kunci 2
```

4. Simpan file
5. Commit dan push ke GitHub

### Contoh Nyata

```yaml
- title: "Analisis Stabilitas Lereng Jalan Tol"
  date: "2026-03-15"
  client: "PT Jasa Marga"
  service_type: "Slope Stability"
  market_sector: "Transportation"
  keywords:
    - slope stability
    - highway
    - limit equilibrium
```

### Proyek Berstatus Ongoing (Sedang Berjalan)

Tambahkan baris `status: "ongoing"` untuk proyek yang masih berjalan. Proyek ini akan tampil sebagai **kartu hijau** di bagian atas halaman, bukan di tabel.

```yaml
- title: "Investigasi Tanah Kawasan Industri"
  date: "2026-01-10"
  client: "Confidential – Developer Swasta"
  service_type: "Site Investigation"
  market_sector: "Building"
  status: "ongoing"
  keywords:
    - soil investigation
    - borehole
```

Ketika proyek selesai, hapus baris `status: "ongoing"` (atau ganti menjadi `status: "completed"`), dan proyek akan otomatis pindah ke tabel.

---

## Bagian 2 — Menambah Proyek Unggulan (dengan Halaman Detail)

Proyek unggulan memiliki halaman sendiri berisi deskripsi lengkap, hasil utama, dan gambar. Gunakan jalur ini hanya untuk proyek yang ingin ditampilkan sebagai studi kasus.

### Langkah-langkah

1. Buka folder **`_projects/`**
2. Buat file baru dengan nama format: **`YYYY-MM-DD-nama-singkat.md`**  
   Contoh: `2026-03-15-analisis-lereng-tol.md`
3. Isi file dengan template berikut (salin dari `_projects/_template.md`):

```markdown
---
title: "Judul Proyek Lengkap"
date: "2026-03-15"
client: "Nama Klien"
status: "ongoing"            # hapus baris ini jika proyek sudah selesai
scope: >
  Deskripsi singkat ruang lingkup dan tantangan teknis proyek.
  Bisa beberapa kalimat.
role: "Principal Geotechnical Consultant"
key_outcomes:
  - "Hasil atau deliverabel utama 1"
  - "Hasil atau deliverabel utama 2"
  - "Hasil atau deliverabel utama 3"
service_type: "Slope Stability"
market_sector: "Infrastructure"
keywords:
  - slope stability
  - finite element
image: "/static/img/projects/2026_nama-proyek.jpg"
---
```

4. Jika ada gambar, letakkan file gambar di folder **`static/img/projects/`**
5. Simpan file, commit, dan push ke GitHub

### Contoh Nyata

```markdown
---
title: "Perkuatan Lereng Jalan Tol Trans-Jawa Km 214"
date: "2026-02-28"
client: "PT Jasa Marga (Persero) Tbk"
scope: >
  Evaluasi stabilitas lereng sepanjang 3 km pada ruas Tol Trans-Jawa
  akibat longsoran kecil pasca hujan lebat. Meliputi investigasi lapangan,
  uji laboratorium, dan analisis numerik 2D.
role: "Principal Geotechnical Consultant"
key_outcomes:
  - "Identifikasi mekanisme kegagalan menggunakan metode Morgenstern-Price"
  - "Rekomendasi soil nail dan perbaikan drainase sebagai tindakan remediasi"
  - "Probabilitas kegagalan berkurang dari 22% menjadi di bawah 3%"
service_type: "Slope Stability"
market_sector: "Transportation"
keywords:
  - slope stability
  - soil nail
  - Trans-Jawa
image: "/static/img/projects/2026_tol-trans-jawa.jpg"
---
```

Di halaman tabel, proyek ini akan tampil dengan lencana **Featured** dan bisa diklik untuk membuka halaman detailnya.

---

## Bagian 3 — Referensi Field

### Field untuk `_data/projects.yml` (Proyek Biasa)

| Field | Wajib? | Keterangan |
|---|---|---|
| `title` | Ya | Judul proyek |
| `date` | Ya | Tanggal selesai atau mulai, format `YYYY-MM-DD` |
| `client` | Ya | Nama klien (boleh disamarkan, misal: `"Confidential – BUMN"`) |
| `service_type` | Ya | Lihat daftar pilihan di bawah |
| `market_sector` | Ya | Lihat daftar pilihan di bawah |
| `status` | Tidak | `"ongoing"` untuk proyek berjalan; hilangkan jika sudah selesai |
| `keywords` | Tidak | Daftar kata kunci untuk filter di halaman; gunakan huruf kecil |

### Field Tambahan untuk `_projects/` (Proyek Unggulan)

| Field | Wajib? | Keterangan |
|---|---|---|
| `scope` | Dianjurkan | Deskripsi ruang lingkup proyek (1–3 paragraf) |
| `role` | Dianjurkan | Peran konsultan dalam proyek |
| `key_outcomes` | Dianjurkan | Daftar hasil/deliverabel utama |
| `image` | Tidak | Path gambar di folder `static/img/projects/` |

---

## Bagian 4 — Pilihan Nilai Field

### `service_type` (Jenis Layanan)

Gunakan salah satu nilai berikut agar filter dan pengelompokan bekerja dengan konsisten:

- `Foundation Engineering`
- `Site Investigation`
- `Slope Stability`
- `Ground Improvement`
- `Numerical Modelling`
- `Risk Assessment`

### `market_sector` (Sektor Pasar)

Gunakan salah satu nilai berikut:

- `Infrastructure`
- `Mining`
- `Building`
- `Energy`
- `Transportation`
- `Water`

> Nilai di luar daftar tetap berfungsi, tetapi gunakan nilai yang konsisten agar pengelompokan rapi.

---

## Bagian 5 — Tips & Catatan Penting

**Format tanggal:** Selalu gunakan format `YYYY-MM-DD` (contoh: `2026-03-15`). Format lain dapat menyebabkan urutan tampilan tidak benar.

**Indentasi YAML:** Gunakan 2 spasi untuk indentasi. Jangan gunakan Tab. Kesalahan indentasi akan menyebabkan error saat build.

**Tanda kutip:** Judul yang mengandung karakter khusus (`:`, `#`, `"`) harus dibungkus tanda kutip ganda:
```yaml
title: "Analisis CPT: Evaluasi Daya Dukung Fondasi"
```

**Nama file proyek unggulan:** Gunakan huruf kecil dan tanda hubung, tanpa spasi:
```
2026-03-15-analisis-lereng-tol.md   ← benar
2026-03-15-Analisis Lereng Tol.md   ← salah
```

**Gambar:** Ukuran gambar yang disarankan adalah lebar maksimal 1200px. Format JPG atau PNG.

**Klien rahasia:** Jika nama klien tidak bisa dipublikasikan, gunakan deskripsi umum:
```yaml
client: "Confidential – Perusahaan Tambang"
client: "Confidential – BUMN"
client: "Confidential – Pemerintah Daerah"
```

---

## Ringkasan Cepat

```
Proyek baru selesai, tidak perlu detail?
  → Buka _data/projects.yml, tambah entri baru di bawah, simpan.

Proyek baru selesai, perlu halaman studi kasus?
  → Buat file baru di _projects/YYYY-MM-DD-nama.md.

Proyek sedang berjalan?
  → Tambah status: "ongoing" di entri YAML atau file .md.

Proyek ongoing sudah selesai?
  → Hapus baris status: "ongoing".
```
