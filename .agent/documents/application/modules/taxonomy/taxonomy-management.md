# Taxonomy Management

> Fitur pengelolaan klasifikasi, kategori, dan tagging terpusat.

---

## Header & Navigation

- [Back to Module Overview](./overview.md)
- [Link to API Specification](../../api/taxonomy/api-taxonomy.md)
- [Link to Testing Scenario](../../testing/taxonomy/test-taxonomy.md)

---

## 1. Feature Overview

- **Deskripsi singkat fitur:** Menyediakan mekanisme klasifikasi entitas yang fleksibel melalui struktur taksonomi (Hierarkis/Flat) dan *tagging* polimorfik.
- **Peran dalam modul:** Berfungsi sebagai *Single Source of Truth* untuk standarisasi nomenklatur dan pengelompokan data di seluruh sistem.
- **Nilai bisnis:** Mengeliminasi redundansi struktur data kategori, meningkatkan konsistensi pelaporan, dan memungkinkan navigasi konten yang lebih kaya.

---

## 2. User Stories

| ID        | Peran (Role) | Tujuan (Goal)                                                       | Manfaat (Benefit)                                                                                         |
| :-------- | :----------- | :------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------- |
| US-TAX-01 | Admin        | Membuat definisi Taksonomi baru (misal: "Skill", "Kategori Produk") | Mempersiapkan struktur klasifikasi yang relevan untuk kebutuhan fitur baru tanpa mengubah skema database. |
| US-TAX-02 | Admin        | Menambah *Terms* baru ke dalam Taksonomi yang sudah ada             | Memperkaya opsi klasifikasi yang tersedia bagi pengguna akhir.                                            |
| US-TAX-03 | Sistem       | Melampirkan *Term* ke entitas bisnis secara polimorfik              | Mengklasifikasikan data (misal: memberikan skill ke karyawan) tanpa membuat tabel relasi khusus.          |
| US-TAX-04 | Pengguna     | Melakukan filter data berdasarkan *Term* spesifik                   | Menemukan item yang relevan dengan cepat melalui navigasi berbasis aspek (*faceted search*).              |

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

```mermaid
erDiagram
    Taxonomies {
        int id PK
        string name
        string slug UK
        string description
        boolean is_hierarchical
        timestamp created_at
        timestamp updated_at
    }

    Terms {
        int id PK
        int taxonomy_id FK
        int parent_id FK
        string name
        string slug UK
        string description
        int order
        timestamp created_at
        timestamp updated_at
    }

    EntityTerms {
        int term_id FK
        string entity_type
        int entity_id
        timestamp created_at
    }

    Taxonomies ||--o{ Terms : "contains"
    Terms }o--o{ EntityTerms : "assigned to"
```

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
