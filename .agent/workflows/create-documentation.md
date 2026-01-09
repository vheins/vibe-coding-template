---
description: create documentation
---

Ikuti langkah-langkah berikut untuk membuat set dokumentasi baru untuk sebuah modul:

1.  **Identifikasi Nama Modul**:
    *   Tentukan nama modul dari permintaan pengguna (misal: "Payment", "Order", "Inventory").
    *   Sebut ini sebagai `<module-slug>` (format kebab-case, misal: `payment-gateway`).

2.  **Buat Struktur Direktori**:
    *   Buat folder berikut jika belum ada:
        *   `.agent/documents/application/modules/<module-slug>/`
        *   `.agent/documents/application/api/<module-slug>/`
        *   `.agent/documents/application/testing/<module-slug>/`

3.  **Baca Template**:
    *   Baca konten dari file template berikut untuk memahami strukturnya:
        *   `.agent/documents/templates/module-documentation.md`
        *   `.agent/documents/templates/api-documentation.md`
        *   `.agent/documents/templates/testing-documentation.md`

4.  **Buat File Dokumentasi**:
    *   **Module Overview**:
        *   Buat file `.agent/documents/application/modules/<module-slug>/overview.md`.
        *   Gunakan konten dari `module-documentation.md`.
        *   Ganti placeholder seperti `<module-name>` dengan nama modul sebenarnya (misal: "Payment Gateway").
        *   Pastikan Tautan Relatif benar:
            *   Link ke All Modules: `../../../README.md`
            *   Link ke Testing: `../../testing/<module-slug>/overview.md`
            *   Link ke API: `../../api/<module-slug>/api-<module-slug>.md`
    
    *   **API Specification**:
        *   Buat file `.agent/documents/application/api/<module-slug>/api-<module-slug>.md`.
        *   Gunakan konten dari `api-documentation.md`.
        *   Ganti placeholder.
        *   Pastikan Tautan Relatif benar:
            *   Kembali ke Modul: `../../modules/<module-slug>/overview.md`

    *   **Test Scenarios**:
        *   Buat file `.agent/documents/application/testing/<module-slug>/test-<module-slug>.md` (atau `overview.md` jika lebih disukai sebagai entri utama).
        *   Gunakan konten dari `testing-documentation.md`.
        *   Ganti placeholder.
        *   Pastikan Tautan Relatif benar:
            *   Kembali ke Modul: `../../modules/<module-slug>/overview.md`
            *   Link ke API: `../../api/<module-slug>/api-<module-slug>.md`

5.  **Review dan Finalisasi**:
    *   Beritahu pengguna bahwa kerangka dokumentasi telah dibuat.
    *   Sebutkan file-file yang telah dibuat.
    *   Minta detail logika bisnis atau API spesifik kepada pengguna untuk mengisi bagian-bagian tersebut.