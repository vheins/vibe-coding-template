---
description: Memperbarui status tugas dalam daftar tugas implementasi
---

Ikuti langkah-langkah berikut untuk memperbarui status tugas di `tasks/implementation-tasks.md`:

1.  **Identifikasi Tugas**:
    *   Jalankan perintah: `cat tasks/implementation-tasks.md`
    *   Cari **ID Tugas** yang relevan (misal: `IAM-01`).

2.  **Tambahkan Tugas Baru (Jika Belum Ada)**:
    *   Jika ID Tugas tidak ditemukan tapi ada di dokumentasi modul (Overview/Implementation Tasks):
    *   Identifikasi tabel modul yang tepat (misal: `## Modul: Notification`).
    *   Tambahkan baris baru dengan format:
        `| <ID-BARU> | <Platform> | Todo | <Deskripsi dari Overview> |`
    *   Contoh: `| NOT-BE-99 | Backend | Todo | Implementasi fitur baru X |`

3.  **Perbarui Status**:
    *   Gunakan tool `replace_file_content` untuk mengubah kolom **Status**.
    *   Ubah dari `Todo` menjadi `In Progress` saat memulai.
    *   Ubah dari `In Progress` menjadi `Done` saat selesai dan diverifikasi.
    *   Contoh perubahan baris:
        *   *Sebelum*: `| IAM-01 | Backend | Todo | ...`
        *   *Sesudah*: `| IAM-01 | Backend | Done | ...`

4.  **Tambahkan Catatan (Opsional)**:
    *   Jika ada detail penting (misal: PR Link, kendala), tambahkan di kolom Deskripsi atau buat catatan kaki di bawah tabel modul terkait.

5.  **Verifikasi & Commit**:
    *   Pastikan format tabel markdown tidak rusak.
    *   Jalankan: `git add tasks/implementation-tasks.md && git commit -m "docs(tasks): update <TASK-ID> status / add new task"`

// turbo
6.  **Cek Status Git**:
    *   Jalankan: `git status` untuk memastikan perubahan tersimpan.
