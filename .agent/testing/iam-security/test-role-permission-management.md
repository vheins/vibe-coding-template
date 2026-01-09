# TESTING DOCUMENTATION: Role & Permission Management

> Dokumen ini berisi rencana dan skenario pengujian untuk fitur Role & Permission Management pada modul IAM & Security.

---

## Header & Navigation

- [Back to Module Overview](../../modules/iam-security/overview.md)
- [Link to Feature Specification](../../modules/iam-security/role-permission-management.md)
- [Link to API Specification](../../api/iam-security/api-role-permission-management.md)

---

## 1. Test Overview

- **Module Name:** IAM & Security - Role & Permission Management
- **Scope of Testing:** Role creation, Permission assignment, RBAC enforcement.
- **Test Tools:** Jest, Supertest.

---

## 2. Test Strategy

### 2.1 Unit Testing
- **Coverage Target:** >80%
- **Critical Components:** RBAC Middleware/Guard.

### 2.2 Integration Testing
- **API Endpoints:**
  - `GET /roles`
  - `POST /roles`
  - `GET /permissions`

---

## 3. Test Scenarios

### 3.1 Roles & Permissions

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| RBAC-TC-001 | Create new role | Admin Token | Role Name: "Editor" | 201 Created | High |
| RBAC-TC-002 | Assign permission to role | Admin Token | Role ID, Permission ID | 200 OK | High |
| RBAC-TC-003 | Access endpoint with correct role | User has Role | - | 200 OK / Success | High |
| RBAC-TC-004 | Access endpoint without correct role | User lacks Role | - | 403 Forbidden | High |

---

## 4. Security Testing

- **Privilege Escalation:** Ensure regular users cannot assign Admin role to themselves.
