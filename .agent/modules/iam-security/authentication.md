# Authentication Specification

> Dokumen ini menjelaskan detail spesifikasi teknis untuk fitur Authentication (Login, Register, Forgot Password).

---

## 1. User Stories

| ID | Role | Goal | Benefit |
| :--- | :--- | :--- | :--- |
| US-01 | Guest | Mendaftar akun baru | Dapat mengakses fitur sistem |
| US-02 | Guest | Melakukan login | Mendapatkan akses ke akun pribadi |
| US-03 | Guest | Mereset password yang lupa | Memulihkan akses ke akun |
| US-07 | User | Melakukan logout | Mengamankan akun saat selesai menggunakan |
| US-08 | User | Refresh Token | Memperpanjang sesi tanpa login ulang |

---

## 2. Business Flow

### 2.1 Login Flow

```mermaid
sequenceDiagram
    participant User
    participant Client
    participant API as Auth Service
    participant DB as Database

    User->>Client: Input Email & Password
    Client->>API: POST /auth/login
    API->>DB: Find User by Email
    alt User Not Found
        API-->>Client: 401 Unauthorized
    else User Found
        API->>API: Verify Password Hash
        alt Invalid Password
            API-->>Client: 401 Unauthorized
        else Valid Password
            API->>API: Generate Access & Refresh Token
            API-->>Client: 200 OK (Tokens)
        end
    end
```

### 2.2 Register Flow

```mermaid
sequenceDiagram
    participant User
    participant Client
    participant API as Auth Service
    participant DB as Database

    User->>Client: Input Registration Data
    Client->>API: POST /auth/register
    API->>DB: Check if Email exists
    alt Email Exists
        API-->>Client: 400 Bad Request (Email taken)
    else Email Available
        API->>API: Validate Password Strength
        API->>API: Hash Password
        API->>DB: Create User Record
        API-->>Client: 201 Created
    end
```

### 2.3 Forgot Password Flow

```mermaid
sequenceDiagram
    participant User
    participant Client
    participant API as Auth Service
    participant DB as Database
    participant Email as Email Service

    User->>Client: Request Password Reset (Email)
    Client->>API: POST /auth/forgot-password
    API->>DB: Find User by Email
    alt User Found
        API->>API: Generate Reset Token
        API->>DB: Save Token & Expiry
        API->>Email: Send Reset Link
    end
    API-->>Client: 200 OK (Message sent if email exists)

    Note over User, Client: User clicks link in email
    User->>Client: Input New Password
    Client->>API: POST /auth/reset-password
    API->>DB: Validate Token
    alt Valid Token
        API->>DB: Update Password Hash
        API->>DB: Invalidate Token
        API-->>Client: 200 OK (Success)
    else Invalid/Expired
        API-->>Client: 400 Bad Request
    end
```

---

## 3. API Schema

### 3.1 Register
- **Endpoint:** `POST /api/v1/auth/register`
- **Request:**
  ```json
  {
    "email": "user@example.com",
    "password": "securePassword123",
    "full_name": "John Doe"
  }
  ```
- **Response (201 Created):**
  ```json
  {
    "id": "uuid-...",
    "email": "user@example.com",
    "message": "Registration successful"
  }
  ```

### 3.2 Login
- **Endpoint:** `POST /api/v1/auth/login`
- **Request:**
  ```json
  {
    "email": "user@example.com",
    "password": "securePassword123"
  }
  ```
- **Response (200 OK):**
  ```json
  {
    "access_token": "eyJhbG...",
    "refresh_token": "eyJhbG...",
    "expires_in": 3600
  }
  ```

### 3.3 Forgot Password
- **Endpoint:** `POST /api/v1/auth/forgot-password`
- **Request:** `{"email": "user@example.com"}`
- **Response:** `{"message": "If email exists, reset link sent."}`

### 3.4 Reset Password
- **Endpoint:** `POST /api/v1/auth/reset-password`
- **Request:**
  ```json
  {
    "token": "reset-token-xyz",
    "new_password": "newSecurePassword1"
  }
  ```
- **Response:** `{"message": "Password updated successfully."}`
