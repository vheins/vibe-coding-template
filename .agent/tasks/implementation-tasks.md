# Daftar Tugas Implementasi (Implementation Tasks)

Dokumen ini berisi gabungan seluruh tugas implementasi dari modul-modul sistem. Gunakan ini sebagai *backlog* utama untuk pengembangan.

---

## Modul: IAM & Security (`iam-security`)

**Deskripsi:** Modul IAM & Security bertanggung jawab atas manajemen identitas pengguna, otentikasi (verifikasi identitas), dan otorisasi (hak akses) dalam sistem.

**Dokumentasi:**
- [Overview](../documents/application/modules/iam-security/overview.md)
- [API Spec](../documents/application/api/iam-security/api-authentication.md)
- [Testing](../documents/application/testing/iam-security/test-authentication.md)

### Backend

| ID Tugas  | Component  | Status | Deskripsi                                                       |
| :-------- | :--------- | :----- | :-------------------------------------------------------------- |
| IAM-BE-01 | Migration  | Todo   | Create `users` table with standard timestamps & soft deletes.   |
| IAM-BE-02 | Seeder     | Todo   | Create `UserSeeder` for Admin & Public role.                    |
| IAM-BE-03 | Model      | Todo   | Setup `User` model arguments (fillable, cast, relations).       |
| IAM-BE-04 | Repository | Todo   | Implement `UserRepository` (Interface & Implementation).        |
| IAM-BE-05 | Service    | Todo   | Implement `UserService` (Business Logic for Suspend/Activate).  |
| IAM-BE-06 | Controller | Todo   | Implement `UserController` (Resource Controller) with JSON:API. |
| IAM-BE-07 | Routes     | Todo   | Register routes in `api.php`.                                   |
| IAM-BE-08 | Tests      | Todo   | Create Feature Test (Positive/Negative/Permission).             |

### Frontend

| ID Tugas  | Component   | Status | Deskripsi                                              |
| :-------- | :---------- | :----- | :----------------------------------------------------- |
| IAM-FE-01 | State       | Todo   | Setup Pinia Store / Context for User.                  |
| IAM-FE-02 | API Service | Todo   | Create `UserService` (Axios wrapper).                  |
| IAM-FE-03 | Component   | Todo   | Create `UserListTable` component.                      |
| IAM-FE-04 | Component   | Todo   | Create `UserForm` component (Add/Edit).                |
| IAM-FE-05 | Page        | Todo   | Implement `UserIndex`, `UserCreate`, `UserEdit` pages. |
| IAM-FE-06 | Integration | Todo   | Connect UI to API & Handle errors.                     |

---

## Modul: Taxonomy (`taxonomy`)

**Deskripsi:** Modul Taxonomy menyediakan sistem klasifikasi terpusat.

**Dokumentasi:**
- [Overview](../documents/application/modules/taxonomy/overview.md)
- [API Spec](../documents/application/api/taxonomy/api-taxonomy.md)
- [Testing](../documents/application/testing/taxonomy/test-taxonomy.md)

### Backend

| ID Tugas  | Component  | Status | Deskripsi                                               |
| :-------- | :--------- | :----- | :------------------------------------------------------ |
| TAX-BE-01 | Migration  | Todo   | Create `taxonomies` and `terms` tables with indices.    |
| TAX-BE-02 | Migration  | Todo   | Create `entity_terms` polymorphic pivot table.          |
| TAX-BE-03 | Model      | Todo   | Setup `Taxonomy` & `Term` models with relations.        |
| TAX-BE-04 | Service    | Todo   | Implement `TaxonomyService` (CRUD & Attachment Logic).  |
| TAX-BE-05 | Controller | Todo   | Implement `TaxonomyController` with JSON:API standards. |
| TAX-BE-06 | Routes     | Todo   | Register API routes.                                    |
| TAX-BE-07 | Tests      | Todo   | Create Unit & Feature tests for Taxonomy ops.           |

### Frontend

| ID Tugas  | Component   | Status | Deskripsi                                 |
| :-------- | :---------- | :----- | :---------------------------------------- |
| TAX-FE-01 | State       | Todo   | Setup Taxonomy Store (Pinia/Context).     |
| TAX-FE-02 | API         | Todo   | Create `TaxonomyService` wrapper.         |
| TAX-FE-03 | Component   | Todo   | Create `TaxonomyManager` UI for Admin.    |
| TAX-FE-04 | Component   | Todo   | Create reusable `TagInput` component.     |
| TAX-FE-05 | Integration | Todo   | Integrate `TagInput` into existing forms. |

---

## Modul: Background Jobs (`background-jobs`)

**Status:** *Pending Granularization*

| ID Tugas  | Platform | Status | Deskripsi                                          |
| :-------- | :------- | :----- | :------------------------------------------------- |
| JOB-BE-01 | Backend  | Todo   | Setup Infrastruktur Queue (Redis/Bull)             |
| JOB-BE-02 | Backend  | Todo   | Implementasi Base Worker Class                     |
| JOB-BE-03 | Backend  | Todo   | Setup Dashboard UI untuk Queue (misal: Bull Board) |

---

## Modul: Media Management (`media-management`)

**Status:** *Pending Granularization*

| ID Tugas  | Platform | Status | Deskripsi                                       |
| :-------- | :------- | :----- | :---------------------------------------------- |
| MED-BE-01 | Backend  | Todo   | Setup Storage Driver (Flysystem/Multer)         |
| MED-BE-02 | Backend  | Todo   | API Upload File & Validation                    |
| MED-BE-03 | Backend  | Todo   | Database Schema Migration (Media & Attachments) |
| MED-FE-01 | Frontend | Todo   | Komponen Upload (Drag & Drop, Progress Bar)     |

---

## Modul: Configuration (`configuration`)

**Status:** *Pending Granularization*

| ID Tugas  | Platform | Status | Deskripsi                                     |
| :-------- | :------- | :----- | :-------------------------------------------- |
| CFG-BE-01 | Backend  | Todo   | Create Configuration Table & CRUD API         |
| CFG-BE-02 | Backend  | Todo   | Implement Caching Layer (Redis)               |
| CFG-BE-03 | Backend  | Todo   | Implement Public Endpoint for FE              |
| CFG-FE-01 | Frontend | Todo   | Create Admin Config Management Page           |
| CFG-FE-02 | Frontend | Todo   | Integrate Global State with Public Config API |

---

## Modul: Notification (`notification`)

**Status:** *Pending Standardization*

| ID Tugas  | Platform | Status | Deskripsi                                       |
| :-------- | :------- | :----- | :---------------------------------------------- |
| NOT-BE-01 | Backend  | Todo   | Setup Notification Service & Queue (Redis/Bull) |
| NOT-BE-02 | Backend  | Todo   | Implement Provider Adapters (Email, Push)       |
| NOT-BE-03 | Backend  | Todo   | Implement API `POST /send` & `GET /list`        |
| NOT-FE-01 | Frontend | Todo   | Implement Notification Bell & Badge             |
| NOT-FE-02 | Frontend | Todo   | Implement Notification List Page                |
| NOT-FE-03 | Frontend | Todo   | Implement Admin Template Editor                 |
