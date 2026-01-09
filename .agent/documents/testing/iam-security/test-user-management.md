# TESTING DOCUMENTATION: User Management

> Dokumen ini berisi rencana dan skenario pengujian untuk fitur User Management pada modul IAM & Security.

---

## Header & Navigation

- [Back to Module Overview](../../application/modules/iam-security/overview.md)
- [Link to Feature Specification](../../application/modules/iam-security/user-management.md)
- [Link to API Specification](../../application/api/iam-security/api-user-management.md)

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

## 3. Test Scenarios (Backend / API)

### 3.1 User CRUD

| ID          | Test Case               | Pre-condition | Input Data     | Expected Result       | Priority |
| :---------- | :---------------------- | :------------ | :------------- | :-------------------- | :------- |
| USR-API-001 | Get user list (Admin)   | Admin Token   | -              | 200 OK, List of users | High     |
| USR-API-002 | Get user profile (Self) | User Token    | -              | 200 OK, User details  | High     |
| USR-API-003 | Update user profile     | User Token    | New Name/Bio   | 200 OK, Updated data  | Medium   |
| USR-API-004 | Delete user (Admin)     | Admin Token   | Target User ID | 204 No Content        | Low      |

---

## 4. Frontend Testing Scenarios

### 4.1 Component / Unit Testing

| ID         | Component    | Test Case                | Expected Behavior                                 |
| :--------- | :----------- | :----------------------- | :------------------------------------------------ |
| USR-FE-001 | UserTable    | Render list of users     | Table shows columns: Name, Email, Status, Actions |
| USR-FE-002 | UserProfile  | Edit mode toggle         | Clicking "Edit" enables form fields               |
| USR-FE-003 | AvatarUpload | Upload invalid file type | Show error "Images only"                          |

### 4.2 E2E Testing

| ID          | Flow Name          | Steps                                                             | Expected Outcome                                |
| :---------- | :----------------- | :---------------------------------------------------------------- | :---------------------------------------------- |
| USR-E2E-001 | Admin Deletes User | 1. Admin Login<br>2. Go to User List<br>3. Click Delete on User X | User X removed from list, Success toast appears |

---

## 5. Manual Testing Scenarios

| ID          | Scenario           | Steps                           | Expected Result                                  |
| :---------- | :----------------- | :------------------------------ | :----------------------------------------------- |
| USR-MAN-001 | Pagination UI      | Navigate through pages of users | Correct data loads, Previous/Next buttons work   |
| USR-MAN-002 | Profile Image Crop | Upload image, try cropping      | Crop tool works smoothly, final image is cropped |

---

## 6. Security Testing

- **Authorization:** Ensure users cannot update other users' profiles (IDOR check).
- **Access Control:** Ensure only Admins can list all users or delete users.
