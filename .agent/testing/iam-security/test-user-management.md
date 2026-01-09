# TESTING DOCUMENTATION: User Management

> Dokumen ini berisi rencana dan skenario pengujian untuk fitur User Management pada modul IAM & Security.

---

## Header & Navigation

- [Back to Module Overview](../../modules/iam-security/overview.md)
- [Link to Feature Specification](../../modules/iam-security/user-management.md)
- [Link to API Specification](../../api/iam-security/api-user-management.md)

---

## 1. Test Overview

- **Module Name:** IAM & Security - User Management
- **Scope of Testing:** CRUD operations for users, Profile management.
- **Test Tools:** Jest, Supertest.

---

## 2. Test Strategy

### 2.1 Unit Testing
- **Coverage Target:** >80%

### 2.2 Integration Testing
- **API Endpoints:**
  - `GET /users` (List Users)
  - `GET /users/:id` (Get User)
  - `PATCH /users/:id` (Update User)
  - `DELETE /users/:id` (Delete User)

---

## 3. Test Scenarios

### 3.1 User CRUD

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| USR-TC-001 | Get user list (Admin) | Admin Token | - | 200 OK, List of users | High |
| USR-TC-002 | Get user profile (Self) | User Token | - | 200 OK, User details | High |
| USR-TC-003 | Update user profile | User Token | New Name/Bio | 200 OK, Updated data | Medium |
| USR-TC-004 | Delete user (Admin) | Admin Token | Target User ID | 204 No Content | Low |

---

## 4. Security Testing

- **Authorization:** Ensure users cannot update other users' profiles (IDOR check).
- **Access Control:** Ensure only Admins can list all users or delete users.
