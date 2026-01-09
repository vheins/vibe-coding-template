# TESTING DOCUMENTATION: Authentication

> Dokumen ini berisi rencana dan skenario pengujian untuk fitur Authentication pada modul IAM & Security.

---

## Header & Navigation

- [Back to Module Overview](../../application/modules/iam-security/overview.md)
- [Link ke Feature Specification](../../application/modules/iam-security/authentication.md)
- [Link ke API Specification](../../application/api/iam-security/api-authentication.md)

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
  - `POST /auth/login` (Login)
  - `POST /auth/register` (Register)
  - `POST /auth/forgot-password` (Forgot Password)
- **Database Interactions:**
  - Verify user creation
  - Verify token storage (refresh tokens)

### 2.3 End-to-End (E2E) Testing
- **Key User Flows:**
  - User Registration -> Login -> Access Protected Route
  - Forgot Password -> Email Link -> Reset Password -> Login

---

## 3. Test Scenarios (Backend / API)

### 3.1 Login (POST /auth/login)

| ID           | Test Case                     | Pre-condition       | Input Data                       | Expected Result                         | Priority |
| :----------- | :---------------------------- | :------------------ | :------------------------------- | :-------------------------------------- | :------- |
| AUTH-API-001 | Login with valid credentials  | User exists, active | Valid Email, Valid Password      | 200 OK, Access & Refresh Token returned | High     |
| AUTH-API-002 | Login with invalid password   | User exists         | Valid Email, Invalid Password    | 401 Unauthorized                        | High     |
| AUTH-API-003 | Login with non-existent email | -                   | Unregistered Email, Any Password | 401 Unauthorized (Generic Message)      | High     |
| AUTH-API-004 | Login with missing fields     | -                   | Empty Email or Password          | 400 Bad Request (Validation Error)      | Medium   |

### 3.2 Register (POST /auth/register)

| ID           | Test Case                          | Pre-condition | Input Data                  | Expected Result                 | Priority |
| :----------- | :--------------------------------- | :------------ | :-------------------------- | :------------------------------ | :------- |
| AUTH-API-011 | Register new user                  | Email unique  | Valid Name, Email, Password | 201 Created, User Data returned | High     |
| AUTH-API-012 | Register with existing email       | User exists   | Existing Email              | 409 Conflict                    | High     |
| AUTH-API-013 | Register with weak password        | -             | Password < 8 chars          | 422 Unprocessable Entity        | Medium   |
| AUTH-API-014 | Register with invalid email format | -             | Invalid Email               | 422 Unprocessable Entity        | Medium   |

### 3.3 Forgot Password

| ID           | Test Case                       | Pre-condition | Input Data         | Expected Result                  | Priority |
| :----------- | :------------------------------ | :------------ | :----------------- | :------------------------------- | :------- |
| AUTH-API-021 | Request reset for valid email   | User exists   | Valid Email        | 202 Accepted, Email sent         | High     |
| AUTH-API-022 | Request reset for invalid email | -             | Unregistered Email | 202 Accepted (Security practice) | Medium   |

### 3.4 Reset Password (POST /auth/reset-password)

| ID           | Test Case                | Pre-condition      | Input Data          | Expected Result          | Priority |
| :----------- | :----------------------- | :----------------- | :------------------ | :----------------------- | :------- |
| AUTH-API-031 | Reset with valid token   | Valid Token exists | Token, New Password | 200 OK, Password Updated | High     |
| AUTH-API-032 | Reset with expired token | Token Expired      | Token, New Password | 400 Bad Request          | High     |
| AUTH-API-033 | Reset with invalid token | -                  | Random String       | 400 Bad Request          | Medium   |

---

## 4. Frontend Testing Scenarios

### 4.1 Component / Unit Testing

| ID          | Component      | Test Case                   | Expected Behavior                                   |
| :---------- | :------------- | :-------------------------- | :-------------------------------------------------- |
| AUTH-FE-001 | LoginForm      | Submit empty form           | Display "Email is required", "Password is required" |
| AUTH-FE-002 | LoginForm      | Submit invalid email format | Display "Invalid email format"                      |
| AUTH-FE-003 | RegisterForm   | Password mismatch           | Display "Passwords do not match"                    |
| AUTH-FE-004 | ForgotPassword | Submit success              | Show success toast/message "Reset link sent"        |

### 4.2 E2E Testing (User Flows)

| ID           | Flow Name                | Steps                                                                               | Expected Outcome                                           |
| :----------- | :----------------------- | :---------------------------------------------------------------------------------- | :--------------------------------------------------------- |
| AUTH-E2E-001 | Login Success & Redirect | 1. Open Login<br>2. Fill Valid Creds<br>3. Submit                                   | Redirect to Dashboard, Token stored in LocalStorage/Cookie |
| AUTH-E2E-002 | Register & Auto Login    | 1. Open Register<br>2. Fill Data<br>3. Submit                                       | Account created, Redirect to Dashboard                     |
| AUTH-E2E-003 | Logout                   | 1. Click Logout Button                                                              | Redirect to Login, Token cleared                           |
| AUTH-E2E-004 | Full Password Reset      | 1. Request Reset<br>2. (Mock) Get Token<br>3. Open Reset Page<br>4. Submit New Pass | Password updated, Redirect to Login, New Pass works        |

---

## 5. Manual Testing Scenarios

> Pengujian manual untuk UX dan penanganan kasus edge yang sulit diotomatisasi.

| ID           | Scenario                                | Steps                                                     | Expected Result                                                     |
| :----------- | :-------------------------------------- | :-------------------------------------------------------- | :------------------------------------------------------------------ |
| AUTH-MAN-001 | Login with slow internet                | Throttle network to 3G, attempt login                     | Loading spinner appears, no timeout error immediately               |
| AUTH-MAN-002 | Password visibility toggle              | Type password, click "eye" icon                           | Password text becomes visible/hidden                                |
| AUTH-MAN-003 | Copy-paste disabled in password confirm | Try to paste password in confirm field                    | (Optional) Paste might be blocked or allowed depending on UX policy |
| AUTH-MAN-004 | Email case sensitivity                  | Login with `USER@Example.com`                             | Should accept and treat as `user@example.com`                       |
| AUTH-MAN-005 | Email Link Validation                   | 1. Request Reset<br>2. Check Email Inbox<br>3. Click Link | Link opens correct app page with token param, no 404 error          |


---

## 6. Security Testing

- **Authentication Checks:** Ensure password is never returned in response.
- **Token Security:** Verify JWT signature and expiration.
- **Rate Limiting:** Test login endpoint for brute force protection (e.g., 5 failed attempts).
- **SQL Injection:** Test input fields with SQL payloads.

---

## 7. Performance Testing (Optional)

- **Load Testing:** Simulate 100 concurrent logins.
- **Latency:** Ensure login response time < 500ms.

---

## 8. Test Data

- **Sample Data:**
  - Valid User: `user@example.com` / `Password123!`
- **Mock Data:** Email service should be mocked for integration tests.

---

## 9. Known Issues & Limitations

- **Deferred:** Lockout mechanism not yet implemented (Test Case AUTH-TC-005 Skipped).
