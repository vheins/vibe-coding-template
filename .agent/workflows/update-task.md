---
description: Memperbarui status tugas dalam daftar tugas implementasi
---

Ikuti langkah-langkah berikut untuk memperbarui status tugas di `tasks/implementation-tasks.md`:

1.  **Baca Daftar Tugas**:
    *   Jalankan perintah: `cat tasks/implementation-tasks.md`
    *   Identifikasi **ID Tugas** yang sedang dikerjakan (misal: `IAM-01`, `NOT-BE-02`).

2.  **Perbarui Status**:
    *   Gunakan tool `replace_file_content` untuk mengubah kolom **Status**.
    *   Ubah dari `Todo` menjadi `In Progress` saat memulai.
    *   Ubah dari `In Progress` menjadi `Done` saat selesai dan diverifikasi.
    *   Contoh perubahan baris:
        *   *Sebelum*: `| IAM-01 | Backend | Todo | ...`
        *   *Sesudah*: `| IAM-01 | Backend | Done | ...`

3.  **Tambahkan Catatan (Opsional)**:
    *   Jika ada detail penting (misal: PR Link, kendala), tambahkan di kolom Deskripsi atau buat catatan kaki di bawah tabel modul terkait.

4.  **Verifikasi & Commit**:
    *   Pastikan format tabel markdown tidak rusak.
    *   Jalankan: `git add tasks/implementation-tasks.md && git commit -m "docs(tasks): update <TASK-ID> status to <STATUS>"`

// turbo
5.  **Cek Status Git**:
    *   Jalankan: `git status` untuk memastikan perubahan tersimpan.
