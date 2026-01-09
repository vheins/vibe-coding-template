# API Specification: Authentication

> Dokumen ini berisi spesifikasi teknis API untuk fitur Authentication.
> Semua endpoint **WAJIB** mengikuti standar **JSON:API** (https://jsonapi.org).

---

## 1. Global Standards

- **Base URL:** `/api/v1`
- **Content-Type:** `application/vnd.api+json`
- **Accept:** `application/vnd.api+json`
- **Date Format:** ISO 8601 (`YYYY-MM-DDTHH:mm:ssZ`)

---

## 2. Endpoints

### 2.1 Register (Create User)
- **URL:** `POST /auth/register`
- **Description:** Mendaftarkan pengguna baru.
- **Access Control:** Public

#### Request

**Headers:**
```http
Content-Type: application/vnd.api+json
Accept: application/vnd.api+json
```

**Body:**
```json
{
  "data": {
    "type": "auth_register",
    "attributes": {
      "email": "user@example.com",
      "password": "securePassword123",
      "full_name": "John Doe"
    }
  }
}
```

#### Response

**Success (201 Created):**
```json
{
  "data": {
    "type": "users",
    "id": "uuid-1234",
    "attributes": {
      "email": "user@example.com",
      "full_name": "John Doe",
      "status": "ACTIVE",
      "created_at": "2023-10-10T10:00:00Z"
    },
    "links": {
      "self": "/api/v1/users/uuid-1234"
    }
  }
}
```

---

### 2.2 Login (Auth Login)
- **URL:** `POST /auth/login`
- **Description:** Melakukan login dan mendapatkan token akses.
- **Access Control:** Public

#### Request

**Headers:**
```http
Content-Type: application/vnd.api+json
Accept: application/vnd.api+json
```

**Body:**
```json
{
  "data": {
    "type": "auth_login",
    "attributes": {
      "email": "user@example.com",
      "password": "securePassword123"
    }
  }
}
```

#### Response

**Success (200 OK):**
```json
{
  "data": {
    "type": "auth_session",
    "id": "uuid-token-session",
    "attributes": {
      "access_token": "eyJhbG...",
      "refresh_token": "eyJhbG...",
      "expires_in": 3600,
      "token_type": "Bearer"
    },
    "links": {
      "self": "/api/v1/auth/session"
    }
  }
}
```

---

### 2.3 Forgot Password (Request Reset)
- **URL:** `POST /password-reset-requests`
- **Description:** Meminta link reset password via email.
- **Access Control:** Public

#### Request

**Headers:**
```http
Content-Type: application/vnd.api+json
Accept: application/vnd.api+json
```

**Body:**
```json
{
  "data": {
    "type": "password-reset-requests",
    "attributes": {
      "email": "user@example.com"
    }
  }
}
```

#### Response

**Success (202 Accepted):**
```json
{
  "meta": {
    "message": "If the email exists, a reset link has been sent."
  },
  "data": null
}
```

---

### 2.4 Reset Password (Execute Reset)
- **URL:** `POST /password-resets`
- **Description:** Mengatur ulang password menggunakan token reset.
- **Access Control:** Public

#### Request

**Headers:**
```http
Content-Type: application/vnd.api+json
Accept: application/vnd.api+json
```

**Body:**
```json
{
  "data": {
    "type": "password-resets",
    "attributes": {
      "token": "reset-token-xyz",
      "new_password": "newSecurePassword1"
    }
  }
}
```

#### Response

**Success (200 OK):**
```json
{
   "meta": {
      "message": "Password updated successfully."
   },
   "data": null
}
```
