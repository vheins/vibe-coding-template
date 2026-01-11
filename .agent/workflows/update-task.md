---
description: Memperbarui status tugas dalam daftar tugas implementasi
---

Ikuti langkah-langkah berikut untuk memperbarui status tugas di `.agent/tasks/implementation-tasks.md`:

1.  **Cek Dokumentasi Fitur**:
    *   Buka file `.agent/documents/application/modules/<module>/<feature>.md`.
    *   Cek tabel "Implementation Tasks" di bagian bawah.
    *   Pastikan status di file ini sudah diupdate (Todo -> Done).

2.  **Sinkronisasi ke Task Board**:
    *   Salin baris tugas yang sudah Done dari dokumentasi fitur.
    *   Update status yang sesuai di `.agent/tasks/implementation-tasks.md`.
    *   Pastikan ID Tugas cocok (misal: `[MOD]-BE-01`).

3.  **Verifikasi & Commit**:
    *   Jalankan: `git add .agent/tasks/implementation-tasks.md && git commit -m "docs(tasks): sync task status from feature docs"`

// turbo
6.  **Cek Status Git**:
    *   Jalankan: `git status` untuk memastikan perubahan tersimpan.
