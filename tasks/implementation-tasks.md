# Daftar Tugas Implementasi (Implementation Tasks)

Dokumen ini berisi gabungan seluruh tugas implementasi dari modul-modul sistem. Gunakan ini sebagai *backlog* utama untuk pengembangan.

---

## Modul: IAM & Security (`iam-security`)

| ID Tugas | Platform | Status | Deskripsi                                                         |
| :------- | :------- | :----- | :---------------------------------------------------------------- |
| IAM-01   | Backend  | Todo   | Setup database schema (Users, Roles, Permissions).                |
| IAM-02   | Backend  | Todo   | Implement JSON:API compliant Authentication endpoints.            |
| IAM-03   | Frontend | Todo   | Implement Login, Register, Forgot Password Pages.                 |
| IAM-04   | Backend  | Todo   | Implement JSON:API compliant User Management endpoints.           |
| IAM-05   | Frontend | Todo   | Implement User Management Dashboard (List, Create, Edit, Delete). |
| IAM-06   | Backend  | Todo   | Implement JSON:API compliant Role & Permission endpoints.         |
| IAM-07   | Frontend | Todo   | Implement Role & Permission Management UI.                        |

## Modul: Background Jobs (`background-jobs`)

| ID Tugas  | Platform | Status | Deskripsi                                          |
| :-------- | :------- | :----- | :------------------------------------------------- |
| JOB-BE-01 | Backend  | Todo   | Setup Infrastruktur Queue (Redis/Bull)             |
| JOB-BE-02 | Backend  | Todo   | Implementasi Base Worker Class                     |
| JOB-BE-03 | Backend  | Todo   | Setup Dashboard UI untuk Queue (misal: Bull Board) |

## Modul: Taxonomy (`taxonomy`)

| ID Tugas  | Platform | Status | Deskripsi                                                      |
| :-------- | :------- | :----- | :------------------------------------------------------------- |
| TAX-BE-01 | Backend  | Todo   | Buat API CRUD Taxonomy & Terms                                 |
| TAX-BE-02 | Backend  | Todo   | Implementasi Logika Pelampiran Polimorfik                      |
| TAX-BE-03 | Backend  | Todo   | Optimasi Query (hindari N+1 saat mengambil entitas dengan tag) |
| TAX-FE-01 | Frontend | Todo   | Buat Manajer Taxonomy (UI Admin)                               |
| TAX-FE-02 | Frontend | Todo   | Buat Komponen "Tag Input" yang dapat digunakan kembali         |

## Modul: Media Management (`media-management`)

| ID Tugas  | Platform | Status | Deskripsi                                       |
| :-------- | :------- | :----- | :---------------------------------------------- |
| MED-BE-01 | Backend  | Todo   | Setup Storage Driver (Flysystem/Multer)         |
| MED-BE-02 | Backend  | Todo   | API Upload File & Validation                    |
| MED-BE-03 | Backend  | Todo   | Database Schema Migration (Media & Attachments) |
| MED-FE-01 | Frontend | Todo   | Komponen Upload (Drag & Drop, Progress Bar)     |
