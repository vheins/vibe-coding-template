---
description: Memastikan seluruh dokumentasi (Modul, API, Testing) tetap sinkron dan up-to-date saat terjadi perubahan.
---

Gunakan workflow ini setiap kali ada perubahan fitur, perbaikan bug signifikan, atau penambahan flows baru untuk mencegah "documentation gap".

1.  **Identifikasi Perubahan**:
    *   Apakah ada perubahan logika bisnis? -> **Update Feature Documentation**.
    *   Apakah ini fitur baru? -> **Buat Feature baru & Update Overview**.
    *   Apakah ada endpoint baru? -> **Update API Spec**.
    *   Apakah ada alur baru? -> **Update Testing**.

2.  **Langkah 1: Update Modul Documentation** (`modules/<slug>/`)
    *   **Jika Fitur Baru:**
        *   Buat file `<feature-name>.md` baru menggunakan template `templates/feature-documentation.md`.
        *   Tambahkan link fitur tersebut ke `overview.md` di bagian "Feature List".
    *   **Jika Update Fitur:**
        *   Edit file spesifik fitur tersebut (misal: `job-processing.md`).
        *   Update User Stories, Business Flow, dan Rules.
    *   **Jika Global Module change:**
        *   Edit `overview.md` (hanya untuk arsitektur level tinggi atau dependensi global).

3.  **Langkah 2: Update Spesifikasi API** (`api/<slug>/api-<slug>.md`)
    *   Update Endpoint URL, Request Body, Response.
    *   Pastikan sesuai standar JSON:API.
    *   Pastikan referensi ke Feature Docs benar.

4.  **Langkah 3: Update Skenario Pengujian** (`testing/<slug>/test-<slug>.md`)
    *   Update Test Case untuk mencakup aturan bisnis baru yang ditulis di Feature Doc.
    *   Tambahkan Monkey Testing jika perlu.

5.  **Langkah 4: Cek Konsistensi**
    *   Pastikan HEADER semua dokumen menggunakan Bahasa Inggris (misal: `# Feature Name`, `## Business Flow`).
    *   Pastikan tidak ada tautan buntu (broken links).

6.  **Verifikasi & Commit**:
    *   Jalankan: `git add .agent/documents/`
    *   Commit: `docs: update documentation for <feature> (module, api, testing)`

// turbo
7.  **Cek Status Git**:
    *   Jalankan: `git status`.
