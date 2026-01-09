# Taxonomy Management

> Fitur pengelolaan klasifikasi, kategori, dan tagging terpusat.

---

## Header & Navigation

- [Back to Module Overview](./overview.md)
- [Link to API Specification](../../api/taxonomy/api-taxonomy.md)
- [Link to Testing Scenario](../../testing/taxonomy/test-taxonomy.md)

---

## 1. Feature Overview

- **Deskripsi singkat fitur:** Manajemen namespace taksonomi (Hierarkis/Flat) dan assignment ke entitas lain.
- **Peran dalam modul:** Single Source of Truth klasifikasi.
- **Nilai bisnis:** Eliminasi redundansi tabel kategori dan konsistensi data.

---

## 2. User Stories

| ID        | Peran (Role) | Tujuan (Goal)                             | Manfaat (Benefit)                                        |
| :-------- | :----------- | :---------------------------------------- | :------------------------------------------------------- |
| US-TAX-01 | Admin        | Membuat Taxonomy baru (misal: "Skill")    | Mempersiapkan sistem untuk fitur baru (Profil Karyawan). |
| US-TAX-02 | Admin        | Menambah Term pada Taxonomy               | Menyediakan opsi pilihan bagi pengguna.                  |
| US-TAX-03 | Sistem       | Attach Term "Javascript" ke Karyawan A    | Klasifikasi skill tanpa mengubah tabel Employee.         |
| US-TAX-04 | Pengguna     | Memfilter Produk berdasarkan "Elektronik" | Menemukan item yang relevan dengan cepat.                |

---

## 3. Business Flow & Rules

### 3.1 Business Flow

#### Term Attachment (Polymorphic)
```mermaid
sequenceDiagram
    participant Client as Domain Module
    participant API as Taxonomy Service
    participant DB as Database

    Client->>API: Attach Term
    Note right of Client: entity="product", id=101, code="electronics"
    
    API->>DB: Validate Taxonomy & Term
    alt Valid
        API->>DB: Insert EntityTerm
        API-->>Client: 200 OK
    else Invalid
        API-->>Client: 400 Bad Request
    end
```

### 3.2 Business Rules
- **Stable Codes:** Taxonomy & Term wajib punya `slug/code` yang unik dan stabil.
- **Polymorphic:** Tabel relasi menggunakan `entity_type` dan `entity_id`.
- **Validation:** Cegah duplikasi tag pada entitas yang sama.

---

## 4. Data Model

- **Taxonomy:** Namespace (misal `product_category`, `tags`).
- **Term:** Nilai (misal `electronics`, `fashion`).
- **EntityTerm:** Pivot table.

*(Lihat ERD lengkap di Module Overview jika diperlukan)*

---

## 5. Compliance & Audit

- **Audit:** Perubahan struktur taksonomi (Taxonomy/Term) wajib dicatat aktor-nya.

---

## 6. Implementation Tasks

| ID        | Platform | Status | Deskripsi                                              |
| :-------- | :------- | :----- | :----------------------------------------------------- |
| TAX-BE-01 | Backend  | Todo   | Buat API CRUD Taxonomy & Terms                         |
| TAX-BE-02 | Backend  | Todo   | Implementasi Logika Pelampiran Polimorfik              |
| TAX-BE-03 | Backend  | Todo   | Optimasi Query (N+1 Problem)                           |
| TAX-FE-01 | Frontend | Todo   | Buat Manajer Taxonomy (UI Admin)                       |
| TAX-FE-02 | Frontend | Todo   | Buat Komponen "Tag Input" yang dapat digunakan kembali |
