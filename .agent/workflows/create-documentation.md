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

3.  **Baca Template Standard**:
    *   Baca konten dari file template berikut untuk memahami strukturnya:
        *   `.agent/documents/templates/module-overview.md` (Untuk landing page modul)
        *   `.agent/documents/templates/feature-documentation.md` (Untuk detail fitur)
        *   `.agent/documents/templates/api-documentation.md`
        *   `.agent/documents/templates/testing-documentation.md`

4.  **Buat File Dokumentasi**:
    *   **Module Overview** (`overview.md`):
        *   Buat file `.agent/documents/application/modules/<module-slug>/overview.md`.
        *   Gunakan konten dari `module-overview.md`.
        *   Isi ringkasan level tinggi.
        *   Link ke All Modules: `../../../README.md`.
    
    *   **Feature Documentation** (Opsional untuk fitur kompleks):
        *   Jika modul memiliki fitur kompleks (misal: "Payment Processing", "Refund Logic"), buat file terpisah `.agent/documents/application/modules/<module-slug>/<feature-name>.md`.
        *   Gunakan konten dari `feature-documentation.md`.
        *   Move detail teknis, alur bisnis, dan user stories yang panjang ke sini.
        *   Tambahkan link fitur ini di table "Feature List" pada `overview.md`.
    
    *   **API Specification**:
        *   Buat file `.agent/documents/application/api/<module-slug>/api-<module-slug>.md`.
        *   Gunakan konten dari `api-documentation.md`.
        *   Link kembali ke Modul: `../../modules/<module-slug>/overview.md`.

    *   **Test Scenarios**:
        *   Buat file `.agent/documents/application/testing/<module-slug>/test-<module-slug>.md`.
        *   Gunakan konten dari `testing-documentation.md`.
        *   Link kembali ke Modul: `../../modules/<module-slug>/overview.md`.

5.  **Review dan Finalisasi**:
    *   Beritahu pengguna bahwa kerangka dokumentasi telah dibuat.
    *   Sebutkan file-file yang telah dibuat.