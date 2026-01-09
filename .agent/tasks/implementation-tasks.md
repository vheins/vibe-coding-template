# Daftar Tugas Implementasi (Implementation Tasks)

Dokumen ini berisi gabungan seluruh tugas implementasi dari modul-modul sistem. Gunakan ini sebagai *backlog* utama untuk pengembangan.

---

## Modul: IAM & Security (`iam-security`)

**Deskripsi:** Modul IAM & Security bertanggung jawab atas manajemen identitas pengguna, otentikasi (verifikasi identitas), dan otorisasi (hak akses) dalam sistem.

**Dokumentasi:**
- [Overview](../documents/application/modules/iam-security/overview.md)
- [API Spec](../documents/application/api/iam-security/api-authentication.md)
- [Testing](../documents/application/testing/iam-security/test-authentication.md)

| ID Tugas | Platform | Status | Deskripsi                                                         |
| :------- | :------- | :----- | :---------------------------------------------------------------- |
| IAM-01   | Backend  | Todo   | Setup database schema (Users, Roles, Permissions).                |
| IAM-02   | Backend  | Todo   | Implement JSON:API compliant Authentication endpoints.            |
| IAM-03   | Frontend | Todo   | Implement Login, Register, Forgot Password Pages.                 |
| IAM-04   | Backend  | Todo   | Implement JSON:API compliant User Management endpoints.           |
| IAM-05   | Frontend | Todo   | Implement User Management Dashboard (List, Create, Edit, Delete). |
| IAM-06   | Backend  | Todo   | Implement JSON:API compliant Role & Permission endpoints.         |
| IAM-07   | Frontend | Todo   | Implement Role & Permission Management UI.                        |

---

## Modul: Background Jobs (`background-jobs`)

**Deskripsi:** Modul Background Jobs bertanggung jawab untuk menangani pemrosesan tugas asinkron, penjadwalan (scheduled tasks), dan pengelolaan antrian (queue management).

**Dokumentasi:**
- [Overview](../documents/application/modules/background-jobs/overview.md)
- [API Spec](../documents/application/api/background-jobs/api-background-jobs.md)
- [Testing](../documents/application/testing/background-jobs/test-background-jobs.md)

| ID Tugas  | Platform | Status | Deskripsi                                          |
| :-------- | :------- | :----- | :------------------------------------------------- |
| JOB-BE-01 | Backend  | Todo   | Setup Infrastruktur Queue (Redis/Bull)             |
| JOB-BE-02 | Backend  | Todo   | Implementasi Base Worker Class                     |
| JOB-BE-03 | Backend  | Todo   | Setup Dashboard UI untuk Queue (misal: Bull Board) |

---

## Modul: Taxonomy (`taxonomy`)

**Deskripsi:** Modul Taxonomy menyediakan sistem klasifikasi terpusat, dapat digunakan kembali, dan agnostik entitas untuk aplikasi (Kategori, Tag, Label, Skill).

**Dokumentasi:**
- [Overview](../documents/application/modules/taxonomy/overview.md)
- [API Spec](../documents/application/api/taxonomy/api-taxonomy.md)
- [Testing](../documents/application/testing/taxonomy/test-taxonomy.md)

| ID Tugas  | Platform | Status | Deskripsi                                                      |
| :-------- | :------- | :----- | :------------------------------------------------------------- |
| TAX-BE-01 | Backend  | Todo   | Buat API CRUD Taxonomy & Terms                                 |
| TAX-BE-02 | Backend  | Todo   | Implementasi Logika Pelampiran Polimorfik                      |
| TAX-BE-03 | Backend  | Todo   | Optimasi Query (hindari N+1 saat mengambil entitas dengan tag) |
| TAX-FE-01 | Frontend | Todo   | Buat Manajer Taxonomy (UI Admin)                               |
| TAX-FE-02 | Frontend | Todo   | Buat Komponen "Tag Input" yang dapat digunakan kembali         |

---

## Modul: Media Management (`media-management`)

**Deskripsi:** Modul Media Management menyediakan layanan terpusat untuk menangani pengunggahan, penyimpanan, dan pengambilan aset digital (File, Gambar, Dokumen).

**Dokumentasi:**
- [Overview](../documents/application/modules/media-management/overview.md)
- [API Spec](../documents/application/api/media-management/api-media-management.md)
- [Testing](../documents/application/testing/media-management/test-media-management.md)

| ID Tugas  | Platform | Status | Deskripsi                                       |
| :-------- | :------- | :----- | :---------------------------------------------- |
| MED-BE-01 | Backend  | Todo   | Setup Storage Driver (Flysystem/Multer)         |
| MED-BE-02 | Backend  | Todo   | API Upload File & Validation                    |
| MED-BE-03 | Backend  | Todo   | Database Schema Migration (Media & Attachments) |
| MED-FE-01 | Frontend | Todo   | Komponen Upload (Drag & Drop, Progress Bar)     |

---

## Modul: Configuration (`configuration`)

**Deskripsi:** Modul Configuration menyediakan mekanisme terpusat untuk mengelola pengaturan sistem, feature flags, dan parameter aplikasi secara dinamis.

**Dokumentasi:**
- [Overview](../documents/application/modules/configuration/overview.md)
- [API Spec](../documents/application/api/configuration/api-configurations.md)
- [Testing](../documents/application/testing/configuration/overview.md)

| ID Tugas  | Platform | Status | Deskripsi                                     |
| :-------- | :------- | :----- | :-------------------------------------------- |
| CFG-BE-01 | Backend  | Todo   | Create Configuration Table & CRUD API         |
| CFG-BE-02 | Backend  | Todo   | Implement Caching Layer (Redis)               |
| CFG-BE-03 | Backend  | Todo   | Implement Public Endpoint for FE              |
| CFG-FE-01 | Frontend | Todo   | Create Admin Config Management Page           |
| CFG-FE-02 | Frontend | Todo   | Integrate Global State with Public Config API |

---

## Modul: Notification (`notification`)

**Deskripsi:** Modul Notification mengelola dan mengirimkan pesan kepada pengguna melalui berbagai saluran (Email, Push, SMS, In-App) dengan pengelolaan template terpusat.

**Dokumentasi:**
- [Overview](../.agent/documents/application/modules/notification/overview.md)
- [API Spec](../.agent/documents/application/api/notification/api-notifications.md)
- [Testing](../.agent/documents/application/testing/notification/overview.md)

| ID Tugas  | Platform | Status | Deskripsi                                       |
| :-------- | :------- | :----- | :---------------------------------------------- |
| NOT-BE-01 | Backend  | Todo   | Setup Notification Service & Queue (Redis/Bull) |
| NOT-BE-02 | Backend  | Todo   | Implement Provider Adapters (Email, Push)       |
| NOT-BE-03 | Backend  | Todo   | Implement API `POST /send` & `GET /list`        |
| NOT-FE-01 | Frontend | Todo   | Implement Notification Bell & Badge             |
| NOT-FE-02 | Frontend | Todo   | Implement Notification List Page                |
| NOT-FE-03 | Frontend | Todo   | Implement Admin Template Editor                 |
