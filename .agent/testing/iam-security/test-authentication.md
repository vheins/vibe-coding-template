# TESTING DOCUMENTATION: Authentication

> Dokumen ini berisi rencana dan skenario pengujian untuk fitur Authentication pada modul IAM & Security.

---

## Header & Navigation

- [Back to Module Overview](../../modules/iam-security/overview.md)
- [Link ke Feature Specification](../../modules/iam-security/authentication.md)
- [Link ke API Specification](../../api/iam-security/api-authentication.md)

---

## 1. Test Overview

- **Module Name:** IAM & Security - Authentication
- **Scope of Testing:** Unit Testing (Services), Integration Testing (API Endpoints), E2E (Login/Register Flows), Security Testing.
- **Test Tools:** Jest (Unit/Integration), Supertest (API), Playwright (E2E).

---

## 2. Test Strategy

### 2.1 Unit Testing
- **Coverage Target:** >80%
- **Critical Components:**
  - Password Hashing (Bcrypt/Argon2)
  - JWT Generation & Verification
  - Input Validation Logic

### 2.2 Integration Testing
- **API Endpoints:**
  - `POST /tokens` (Login)
  - `POST /users` (Register)
  - `POST /password-reset-requests` (Forgot Password)
- **Database Interactions:**
  - Verify user creation
  - Verify token storage (refresh tokens)

### 2.3 End-to-End (E2E) Testing
- **Key User Flows:**
  - User Registration -> Login -> Access Protected Route
  - Forgot Password -> Email Link -> Reset Password -> Login

---

## 3. Test Scenarios

### 3.1 Login (POST /tokens)

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| AUTH-TC-001 | Login with valid credentials | User exists, active | Valid Email, Valid Password | 201 Created, Access & Refresh Token returned | High |
| AUTH-TC-002 | Login with invalid password | User exists | Valid Email, Invalid Password | 401 Unauthorized | High |
| AUTH-TC-003 | Login with non-existent email | - | Unregistered Email, Any Password | 401 Unauthorized (Generic Message) | High |
| AUTH-TC-004 | Login with missing fields | - | Empty Email or Password | 400 Bad Request (Validation Error) | Medium |

### 3.2 Register (POST /users)

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| AUTH-TC-011 | Register new user | Email unique | Valid Name, Email, Password | 201 Created, User Data returned | High |
| AUTH-TC-012 | Register with existing email | User exists | Existing Email | 409 Conflict | High |
| AUTH-TC-013 | Register with weak password | - | Password < 8 chars | 422 Unprocessable Entity | Medium |
| AUTH-TC-014 | Register with invalid email format | - | Invalid Email | 422 Unprocessable Entity | Medium |

### 3.3 Forgot Password

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| AUTH-TC-021 | Request reset for valid email | User exists | Valid Email | 202 Accepted, Email sent | High |
| AUTH-TC-022 | Request reset for invalid email | - | Unregistered Email | 202 Accepted (Security practice) | Medium |

---

## 4. Security Testing

- **Authentication Checks:** Ensure password is never returned in response.
- **Token Security:** Verify JWT signature and expiration.
- **Rate Limiting:** Test login endpoint for brute force protection (e.g., 5 failed attempts).
- **SQL Injection:** Test input fields with SQL payloads.

---

## 5. Performance Testing (Optional)

- **Load Testing:** Simulate 100 concurrent logins.
- **Latency:** Ensure login response time < 500ms.

---

## 6. Test Data

- **Sample Data:**
  - Valid User: `user@example.com` / `Password123!`
- **Mock Data:** Email service should be mocked for integration tests.

---

## 7. Known Issues & Limitations

- **Deferred:** Lockout mechanism not yet implemented (Test Case AUTH-TC-005 Skipped).
