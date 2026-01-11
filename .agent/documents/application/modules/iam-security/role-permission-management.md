# Role & Permission Management

> Fitur untuk mengelola Role-Based Access Control (RBAC).

---

## Header & Navigation

- [Back to Module Overview](./overview.md)
- [Link to API Specification](../../api/iam-security/api-role-permission-management.md)
- [Link to Testing Scenario](../../testing/iam-security/test-authentication.md)

---

## 1. Feature Overview

- **Deskripsi singkat fitur:** Menyediakan kontrol akses berbasis peran (*Role-Based Access Control* - RBAC) yang memungkinkan definisi peran dan penetapan izin secara granular.
- **Peran dalam modul:** Bertindak sebagai *Authorization Policy Engine* yang menentukan "siapa boleh melakukan apa" dalam sistem.
- **Nilai bisnis:** Meminimalkan risiko *privilege escalation* dan menyederhanakan administrasi akses pengguna yang kompleks.

---

## 2. User Stories

| US-04 | Admin | Mendefinisikan peran sistem baru (Role Definition) | Mengelompokkan set izin yang standar untuk fungsionalitas kerja tertentu. |
| US-05 | Admin | Mengkonfigurasi *permissions* untuk peran tertentu | Mengontrol secara granular tindakan apa saja yang diizinkan untuk setiap peran. |
| US-11 | Admin | Menetapkan peran ke pengguna (*Role Assignment*) | Memberikan otoritas kerja kepada pengguna sesuai dengan tanggung jawab jabatannya. |

---

## 3. Business Flow & Rules

### 3.1 Business Flow
```mermaid
sequenceDiagram
    participant Admin
    participant API
    participant DB

    Admin->>API: Create Role
    API->>DB: Insert Role
    Admin->>API: Assign Permissions
    API->>DB: Update Relation
```

### 3.2 Business Rules
- **Super Admin:** Role spesial yang tidak bisa dihapus.
- **Immutable permissions:** Permission code didefinisikan di code.

---

## 4. Data Model

- **Roles, Permissions, RolePermissions, UserRoles.**

```mermaid
erDiagram
    Roles {
        int id PK
        string name UK
        string guard_name
        timestamp created_at
        timestamp updated_at
    }

    Permissions {
        int id PK
        string name UK
        string guard_name
        timestamp created_at
        timestamp updated_at
    }

    RoleHasPermissions {
        int permission_id FK
        int role_id FK
    }

    ModelHasRoles {
        int role_id FK
        string model_type
        int model_id
    }

    Roles }o--o{ Permissions : "RoleHasPermissions"
    Roles }o--o{ ModelHasRoles : "Assigned to Users"
```

## 5. Compliance & Audit

- **Audit:** Perubahan hak akses Role adalah tindakan kritis yang wajib dicatat.

---

## 6. Implementation Tasks

| ID     | Platform | Status | Deskripsi                                                 |
| :----- | :------- | :----- | :-------------------------------------------------------- |
| IAM-06 | Backend  | Todo   | Implement JSON:API compliant Role & Permission endpoints. |
| IAM-07 | Frontend | Todo   | Implement Role & Permission Management UI.                |
