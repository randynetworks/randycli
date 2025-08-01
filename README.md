# `randy` - Sistem Kontrol Versi Sederhana untuk Database PostgreSQL

`randy` adalah sebuah alat baris perintah (CLI) yang terinspirasi oleh Git, namun dirancang khusus untuk melakukan versioning pada database PostgreSQL. Alih-alih melacak perubahan pada file teks, `randy` melacak perubahan pada skema dan data database Anda dengan membuat "snapshot" di setiap commit.

---
## Fitur Utama
* **Inisialisasi**: Mudah untuk memulai repositori di proyek yang ada.
* **Commit**: Menyimpan snapshot dari seluruh skema dan data database.
* **Status**: Membandingkan kondisi database *live* dengan commit terakhir dan menunjukkan perubahan data secara rinci.
* **Log**: Melihat riwayat commit dari yang terbaru hingga terlama.
* **Checkout & Reset**: Mengembalikan kondisi database ke titik commit tertentu.

---
## Prasyarat
Sebelum menginstal, pastikan sistem Anda memiliki:
* `bash` (tersedia di hampir semua Linux dan macOS).
* `postgresql-client` (menyediakan `psql`, `pg_dump`, `dropdb`, `createdb`).
* Utilitas standar Unix: `tar`, `sort`, `sed`, `grep`, `mktemp`.

---
## Instalasi
Untuk membuat perintah `randy` bisa diakses secara global dari direktori mana pun:

1.  **Simpan Kode**: Simpan seluruh kode skrip `randy` yang telah kita buat ke dalam **satu file** bernama `randy`.
2.  **Jadikan Executable**: Buka terminal, navigasi ke folder tempat Anda menyimpan file `randy`, dan jalankan:
    ```bash
    chmod +x randy
    ```
3.  **Salin ke PATH**: Salin file tunggal tersebut ke direktori `PATH` sistem Anda:
    ```bash
    sudo cp randy /usr/local/bin/
    ```
4.  **Verifikasi**: Buka terminal **baru** dan verifikasi instalasi:
    ```bash
    which randy
    # Output seharusnya: /usr/local/bin/randy
    ```
---

## Konfigurasi Awal
Sebelum Anda bisa membuat commit, Anda harus mengatur identitas Anda. Pengaturan ini disimpan secara lokal untuk setiap repositori.

```bash
# Pindah ke direktori proyek Anda
cd /path/to/your/project

# Inisialisasi repositori (jika belum)
randy init

# Atur nama dan email Anda
randy config user.name "Nama Lengkap Anda"
randy config user.email "email@anda.com"
