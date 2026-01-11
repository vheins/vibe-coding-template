---
description: generate test scenarios
---

Workflow ini digunakan untuk menghasilkan skenario pengujian (Backend & Frontend) yang komprehensif berdasarkan fitur dan spesifikasi API yang tersedia, sesuai dengan template di `.agent/documents/templates/testing-overview.md` dan `.agent/documents/templates/testing-feature.md`.

# Langkah 1: Pengumpulan Konteks
1. **Identifikasi Modul**: Tentukan nama modul yang akan dibuatkan skenarionya (misal: `inventory`, `finance`).
2. **Baca Dokumentasi Terkait**:
   - Baca overview modul: `.agent/documents/application/modules/<module-name>/overview.md`
   - Baca feature docs: `.agent/documents/application/modules/<module-name>/<feature-name>.md`
   - Baca API spec: `.agent/documents/application/api/<module-name>/api-<module-name>.md`
3. **Pahami Business Rules**: Identifikasi aturan bisnis kritis, invarian ERP (misal: "No over-allocation"), dan alur status.

# Langkah 2: Strukturisasi Skenario
Dokumentasi testing dipecah menjadi dua bagian:
1. **Testing Overview (`test-<module>.md`)**: Index utama untuk modul.
2. **Feature Testing (`test-<feature>.md`)**: Skenario detail per fitur.

# Langkah 3: Generasi Skenario (Feature Testing)
Untuk setiap fitur dalam modul, buat file `test-<feature-name>.md` menggunakan template `.agent/documents/templates/testing-feature.md`.
Isi skenario berdasarkan logika berikut:
1. **Kasus Positif (Happy Path)**:
   - Creation, Update, Deletion sukses.
   - Status transitions (Draft -> Submitted -> Approved).
2. **Kasus Negatif (Validation)**:
   - Input invalid, mandatory fields missing.
   - Violation of Business Rules (e.g., Stock < 0).
3. **Monkey & Security**:
   - Spamming, Race Conditions, Privilege Escalation.

# Langkah 4: Pembuatan Overview Index
Setelah semua file fitur dibuat:
1.  Gunakan template `.agent/documents/templates/testing-overview.md`.
2.  Buat file utama: `.agent/documents/application/testing/<module-name>/test-<module-name>.md`.
3.  List semua fitur yang telah dibuatkan skenarionya beserta link ke file masing-masing.

# Langkah 5: Keamanan & Integritas ERP
1. **Security**:
   - Cek Role & Permission (User A tidak bisa edit data User B).
   - Proteksi XSS/SQLi standar pada input field.
2. **ERP Invariants**:
   - Pastikan total header sinkron dengan detail baris.
   - Pastikan pergerakan stok/jurnal hanya terjadi pada saat Posting.

# Langkah 6: Finalisasi
1. **Review Internal**: Pastikan skenario mencakup semua User Story yang didefinisikan di Feature Documentation.
2. **Verifikasi Link**: Pastikan link file di overview document berfungsi dengan baik.
