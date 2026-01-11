# File Management

> Fitur pengelolaan file, upload, dan retrieval media.

---

## Header & Navigation

- [Back to Module Overview](./overview.md)
- [Link to API Specification](../../api/media-management/api-media-management.md)
- [Link to Testing Scenario](../../testing/media-management/test-media-management.md)

---

## 1. Feature Overview

- **Deskripsi singkat fitur:** Menyediakan layanan manajemen aset digital terpusat yang mencakup pengunggahan (*upload*), penyimpanan multi-provider, transformasi media, dan manajemen metadata.
- **Peran dalam modul:** Bertindak sebagai *unified storage interface* yang mengabstraksi kompleksitas driver penyimpanan fisik.
- **Nilai bisnis:** Mengoptimalkan biaya penyimpanan melalui strategi kompresi/retensi dan memastikan ketersediaan aset tinggi (*high availability*).

---

## 2. User Stories

### US-MED-01 — Upload Avatar Pengguna

**Sebagai** User
**Saya ingin** Upload Avatar Pengguna
**Sehingga** Akun lebih personal dan dikenali

**Acceptance Criteria:**

* Format: JPG, PNG, WEBP
* Max size: 2MB
* Auto-crop rasio 1:1
* Magic bytes validation

### US-MED-02 — Kelola Galeri Produk

**Sebagai** Admin
**Saya ingin** Kelola Galeri Produk
**Sehingga** Katalog penjualan terlihat menarik

**Acceptance Criteria:**

* Multi-upload support
* Drag & Drop reorder
* Set Featured Image
* Delete obsolete images

### US-MED-03 — Auto Resize & Thumbnail

**Sebagai** Sistem
**Saya ingin** Auto Resize & Thumbnail
**Sehingga** Loading page lebih cepat

**Acceptance Criteria:**

* Varian: Original, Medium (800px), Thumb (200px)
* Auto-compression
* Standardized naming convention

### US-MED-04 — Lampiran Dokumen Transaksi

**Sebagai** User
**Saya ingin** Lampiran Dokumen Transaksi
**Sehingga** Administrasi transaksi valid

**Acceptance Criteria:**

* Format: PDF, DOCX
* Browser Preview
* Secure Signed URL download
* Antivirus scan on upload

## 3. Business Flow & Rules

### 3.1 Business Flow

#### Upload & Attach Flow
```mermaid
sequenceDiagram
    participant Client
    participant API as Media Service
    participant Storage as Cloud Storage (S3)
    participant DB as Database

    Client->>API: Upload File (Multipart)
    API->>API: Validate (Size, MIME)
    API->>Storage: Put Object
    Storage-->>API: URL / Path
    API->>DB: Save Metadata (MEDIA Table)
    
    alt With Attachment Info
        API->>DB: Link to Entity (MEDIA_ATTACHMENT)
    end

    API-->>Client: 201 Created (Media Object)
```

### 3.2 Business Rules
- **Max File Size:** 5MB (Img), 20MB (Doc).
- **Allowed Types:** JPG, PNG, WEBP, PDF.
- **Cleanup:** Temp files akan dihapus jika tidak di-link dalam 24 jam.

---

## 4. Data Model

> Diagram Entity Relationship untuk Media Management.

- **Media:** Metadata file (Filename, Size, URL, Disk).
- **MediaAttachment:** Tabel pivot polimorfik (Entity Type, Entity ID).

```mermaid
erDiagram
    Media {
        int id PK
        string disk "s3, local"
        string directory
        string filename UK
        string extension
        string mime_type
        string aggregate_type "image, document, video"
        int size
        text metadata "json"
        timestamp created_at
        timestamp updated_at
    }

    MediaAttachments {
        int media_id FK
        string entity_type
        int entity_id
        string tag "avatar, gallery, document"
        timestamp attached_at
    }

    Media ||--o{ MediaAttachments : "attached to"
```

---

## 5. Compliance & Audit

- **Access Control:** File privat hanya bisa diakses via Presigned URL/Proxy.

---

## 6. Implementation Tasks

| ID        | Platform | Status | Deskripsi                                       |
| :-------- | :------- | :----- | :---------------------------------------------- |
| MED-BE-01 | Backend  | Todo   | Setup Storage Driver (Flysystem/Multer)         |
| MED-BE-02 | Backend  | Todo   | API Upload File & Validation                    |
| MED-BE-03 | Backend  | Todo   | Database Schema Migration (Media & Attachments) |
| MED-FE-01 | Frontend | Todo   | Komponen Upload (Drag & Drop, Progress Bar)     |
