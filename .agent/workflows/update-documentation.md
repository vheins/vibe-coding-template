---
description: Memastikan sinkronisasi total dokumentasi (Overlap Check).
---

Workflow ini **WAJIB** dijalankan setiap kali ada perubahan pada salah satu dari: Logika Bisnis, API, atau Testing. Tujuannya adalah menghilangkan "Documentation Gap".

# Prinsip: "Change One, Check All"
Setiap perubahan pada satu dokumen **HARUS** memicu pemeriksaan pada dokumen lain yang terkait.

# Langkah 1: Identifikasi Sumber Perubahan
Tentukan apa yang memicu update ini:
- **A. Perubahan Fitur/Bisnis**: (misal: "User perlu email verifikasi saat register")
- **B. Perubahan API**: (misal: "Tambah field `phone_number` di response `/users`")
- **C. Perubahan Testing**: (misal: "Menambah skenario negatif untuk validasi password")

# Langkah 2: Eksekusi Sinkronisasi (Wajib Berurutan)

## 2.1 Update Module Documentation (`modules/<slug>/`)
- [ ] **Jika Sumber A**: Update User Stories, Flow, dan Rules di file fitur terkait.
- [ ] **Jika Sumber B/C**: Cek apakah perubahan teknis ini sesuai dengan bisnis rules yang ada? Jika tidak, **UPDATE Module Doc** dulu agar sesuai realita.

## 2.2 Update API Specification (`api/<slug>/`)
- [ ] **Sinkronisasi**: Cek apakah perubahan di 2.1 mengubah request/response?
- [ ] **Aksi**: Tambah/Hapus/Edit endpoint di `api-<slug>.md`.
- [ ] **Validasi**: Pastikan setiap field baru di module doc ada di API spec.

## 2.3 Update Testing Scenarios (`testing/<slug>/`)
- [ ] **Sinkronisasi**: Cek apakah perubahan di 2.1 atau 2.2 butuh test case baru?
- [ ] **Aksi**:
    - Update Happy Path (Positif).
    - Update Validation Rules (Negatif).
    - Update Security/Monkey Test jika endpoint publik berubah.

## 2.4 Update Module Overview (`modules/<slug>/overview.md`)
- [ ] **Cek**: Apakah ada fitur baru yang belum masuk "Feature List"?
- [ ] **Aksi**: Update daftar fitur dan link file-nya.

# Langkah 3: Final Verification (The Gap Check)
Jawab pertanyaan berikut sebelum commit. Jika ada "TIDAK", ulangi langkah terkait.

1. Apakah User Story di Module Doc sudah ter-cover di API Endpoint? (Ya/Tidak)
2. Apakah setiap API Endpoint punya minimal 1 Test Case Positif & 1 Negatif? (Ya/Tidak)
3. Apakah Overview mencantumkan semua fitur terbaru? (Ya/Tidak)

# Langkah 4: Commit
Jika semua "Ya":
- Jalankan: `git add .agent/documents/`
- Commit: `docs: sync documentation for <module-name> (feature, api, testing)`
