---
description: Memastikan seluruh dokumentasi (Modul, API, Testing) tetap sinkron dan up-to-date saat terjadi perubahan.
---

Gunakan workflow ini setiap kali ada perubahan fitur, perbaikan bug signifikan, atau penambahan flows baru untuk mencegah "documentation gap".

1.  **Identifikasi Perubahan**:
    *   Apakah ada perubahan logika bisnis? -> **Update Overview**.
    *   Apakah ada endpoint baru atau perubahan parameter? -> **Update API Spec**.
    *   Apakah ada alur (flow) baru atau edge case yang ditemukan? -> **Update Testing**.

2.  **Langkah 1: Update Modul Overview** (`modules/<slug>/overview.md`)
    *   **User Stories**: Tambahkan US baru jika fitur baru.
    *   **Business Flow**: Update diagram Mermaid jika alur berubah.
    *   **ERD**: Update diagram jika ada perubahan skema database.
    *   **Implementation Tasks**: Pastikan semua tugas baru tercatat di tabel tugas modul ini.
    *   **Penting**: Pastikan struktur tetap sesuai dengan `.agent/documents/templates/module-documentation.md`. Jangan menghapus section wajib.

3.  **Langkah 2: Update Spesifikasi API** (`api/<slug>/api-<slug>.md`)
    *   Jika perubahan melibatkan Backend/API:
    *   Pastikan Endpoint URL, Method, dan Request/Response Body sesuai dengan kode aktual.
    *   Tambahkan kode error baru jika ada.
    *   Pastikan link kembali ke Overview Modul berfungsi.
    *   **Penting**: Gunakan format `templates/api-documentation.md` (JSON:API Standard).

4.  **Langkah 3: Update Skenario Pengujian** (`testing/<slug>/test-<slug>.md`)
    *   **Wajib:** Setiap flow baru di Overview HARUS memiliki setidaknya satu skenario pengujian (Positif & Negatif).
    *   Update bagian **Integration Testing** jika API berubah.
    *   Tambahkan **Monkey Testing** scenario jika fitur rentan terhadap input acak.
    *   **Penting**: Ikuti struktur `templates/testing-documentation.md` (Positif, Negatif, Monkey).

5.  **Langkah 4: Cek Konsistensi (Gap Analysis)**
    *   **Cek Link**: Pastikan semua `[Link ke ...]` di tiga dokumen di atas saling terhubung dan tidak broken (404).
    *   **Cek Master Task List**: Jika ada task baru di Overview, jalankan workflow `update-task` (Langkah 2) untuk menambahkannya ke `.agent/tasks/implementation-tasks.md`.

6.  **Verifikasi & Commit**:
    *   Jalankan: `git add .agent/documents/`
    *   Commit pesan standar: `docs: update documentation for <feature-name> (overview, api, testing)`

// turbo
7.  **Cek Status Git**:
    *   Jalankan: `git status` untuk memastikan semua file dokumentasi terpilih.
