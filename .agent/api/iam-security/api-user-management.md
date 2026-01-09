# API Specification: User Management

> Dokumen ini berisi spesifikasi teknis API untuk fitur User Management.
> Semua endpoint **WAJIB** mengikuti standar **JSON:API** (https://jsonapi.org).

---

## 1. Global Standards

- **Base URL:** `/api/v1`
- **Content-Type:** `application/vnd.api+json`
- **Accept:** `application/vnd.api+json`
- **Date Format:** ISO 8601 (`YYYY-MM-DDTHH:mm:ssZ`)

---

## 2. Endpoints

### 2.1 List Users
- **URL:** `GET /users`
- **Description:** Mendapatkan daftar pengguna dengan paginasi dan filter.
- **Access Control:** Authenticated (Admin)

#### Request

**Headers:**
```http
Accept: application/vnd.api+json
Authorization: Bearer <token>
```

**Query Parameters:**
- `page[number]`: 1
- `page[size]`: 10
- `filter[search]`: John

#### Response

**Success (200 OK):**
```json
{
  "data": [
    {
      "type": "users",
      "id": "uuid-1",
      "attributes": {
        "email": "john@example.com",
        "full_name": "John Doe",
        "status": "ACTIVE"
      },
      "links": {
        "self": "/api/v1/users/uuid-1"
      }
    }
  ],
  "meta": {
    "total_pages": 10,
    "total_items": 100
  },
  "links": {
    "self": "/api/v1/users?page[number]=1&page[size]=10",
    "next": "/api/v1/users?page[number]=2&page[size]=10",
    "last": "/api/v1/users?page[number]=10&page[size]=10"
  }
}
```

---

### 2.2 Get Single User
- **URL:** `GET /users/:id`
- **Description:** Mendapatkan detail satu pengguna berdasarkan ID.
- **Access Control:** Authenticated (Admin/Self)

#### Request

**Headers:**
```http
Accept: application/vnd.api+json
Authorization: Bearer <token>
```

#### Response

**Success (200 OK):**
```json
{
  "data": {
    "type": "users",
    "id": "uuid-1",
    "attributes": {
      "email": "john@example.com",
      "full_name": "John Doe",
      "status": "ACTIVE"
    },
    "links": {
      "self": "/api/v1/users/uuid-1"
    }
  }
}
```

---

### 2.3 Update User
- **URL:** `PATCH /users/:id`
- **Description:** Mengubah data pengguna (profil atau status).
- **Access Control:** Authenticated (Admin/Self)

#### Request

**Headers:**
```http
Content-Type: application/vnd.api+json
Accept: application/vnd.api+json
Authorization: Bearer <token>
```

**Body:**
```json
{
  "data": {
    "type": "users",
    "id": "uuid-1",
    "attributes": {
      "full_name": "John Updated",
      "status": "SUSPENDED"
    }
  }
}
```

#### Response

**Success (200 OK):**
```json
{
  "data": {
    "type": "users",
    "id": "uuid-1",
    "attributes": {
      "email": "john@example.com",
      "full_name": "John Updated",
      "status": "SUSPENDED"
    },
    "links": {
      "self": "/api/v1/users/uuid-1"
    }
  }
}
```

---

### 2.4 Delete User
- **URL:** `DELETE /users/:id`
- **Description:** Menghapus pengguna (Soft Delete).
- **Access Control:** Authenticated (Admin)

#### Request

**Headers:**
```http
Accept: application/vnd.api+json
Authorization: Bearer <token>
```

#### Response

**Success (204 No Content):**
*(Empty Body)*
