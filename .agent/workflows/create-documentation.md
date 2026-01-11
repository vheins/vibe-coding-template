---
description: create documentation
---

Workflow ini digunakan untuk membuat set dokumentasi lengkap (Overview, Feature, API, Testing) untuk modul baru atau yang sudah ada. Workflow ini cerdas dan akan melakukan riset terlebih dahulu sebelum menulis.

# Langkah 1: Analisis & Riset
1. **Identifikasi Modul**:
   - Tentukan nama modul dari input user (misal: `user-management`, `payment`, `inventory`).
2. **Tentukan Konteks**:
   - Apakah ini modul **Global/Umum** (contoh: "User Management", "Authentication")?
   - Atau modul **Spesifik/Custom** (contoh: "Gojek Driver Allocation", "Tokopedia Promo")?
3. **Lakukan Riset**:
   - **Jika Global**: Gunakan pengetahuan umum industri (Best Practices) untuk fitur, endpoint, dan testing standar. Jangan ragu menambahkan fitur best-practice meskipun user tidak meminta spesifik (misal: "Audit Log" untuk User Management).
   - **Jika Spesifik**: Lakukan pencarian di codebase (`find_by_name`, `grep_search`) untuk menemukan model, controller, atau file terkait yang sudah ada. Pahami logika bisnisnya.

# Langkah 2: Perencanaan Konten (Breakdown)
Sebelum membuat file, susun rencana konten di memori atau scratchpad:
1. **Fitur Utama**: Apa saja fitur kuncinya? (misal: Login, Register, Forgot Password).
2. **API Endpoints**: Endpoint apa yang dibutuhkan untuk mendukung fitur tersebut? (Method, URL, Request/Response body). Sesuaikan dengan standar JSON:API.
3. **Skenario Testing**:
   - Positif (Happy Path).
   - Negatif (Validation, Error Handling).
   - Security & Monkey Testing.

# Langkah 3: Pembuatan Dokumentasi (Execution)
Gunakan template yang ada di `.agent/documents/templates/` sebagai dasar. Jangan menulis dari nol, selalu isi template.

## 3.1 Buat Struktur Folder
Pastikan folder berikut ada (buat jika belum):
- `.agent/documents/application/modules/<module-name>/`
- `.agent/documents/application/api/<module-name>/`
- `.agent/documents/application/testing/<module-name>/`

## 3.2 Tulis Feature Documentation
Untuk setiap fitur kompleks, buat file spesifik (opsional jika modul sederhana, bisa digabung di overview):
- **File**: `.agent/documents/application/modules/<module-name>/<feature-name>.md`
- **Template**: `.agent/documents/templates/feature-documentation.md`
- **Isi**: Detail User Stories, Acceptance Criteria, dan Data Model.

## 3.3 Tulis API Specification
- **File**: `.agent/documents/application/api/<module-name>/api-<module-name>.md`
- **Template**: `.agent/documents/templates/api-documentation.md`
- **Isi**: Definisikan semua endpoint yang direncanakan di Langkah 2. Pastikan contoh JSON Request/Response lengkap.

## 3.4 Tulis Testing Scenarios
- **File**: `.agent/documents/application/testing/<module-name>/test-<module-name>.md`
- **Template**: `.agent/documents/templates/testing-documentation.md`
- **Isi**: Masukkan semua skenario test (Positif, Negatif, Security, Monkey) lengkap dengan Priority.

## 3.5 Rangkum dalam Module Overview
- **File**: `.agent/documents/application/modules/<module-name>/overview.md`
- **Template**: `.agent/documents/templates/module-overview.md`
- **Isi**:
  - Hapus bagian instruksi template.
  - Isi "Feature List" dengan link ke file feature/API/testing yang baru dibuat.
  - Buat diagram arsitektur sederhana (Mermaid) jika perlu.

# Langkah 4: Finalisasi
1. **Review**: Pastikan semua link antar dokumen berfungsi (bisa diklik).
2. **Lapor**: Beritahu user bahwa dokumentasi untuk modul `<module-name>` siap direview.