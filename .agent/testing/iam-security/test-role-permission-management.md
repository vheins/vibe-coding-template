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

## 3. Test Scenarios (Backend / API)

### 3.1 Roles & Permissions

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| RBAC-API-001 | Create new role | Admin Token | Role Name: "Editor" | 201 Created | High |
| RBAC-API-002 | Assign permission to role | Admin Token | Role ID, Permission ID | 200 OK | High |
| RBAC-API-003 | Access endpoint with correct role | User has Role | - | 200 OK / Success | High |
| RBAC-API-004 | Access endpoint without correct role | User lacks Role | - | 403 Forbidden | High |

---

## 4. Frontend Testing Scenarios

### 4.1 Component / Unit Testing

| ID | Component | Test Case | Expected Behavior |
| :--- | :--- | :--- | :--- |
| RBAC-FE-001 | RoleManager | Add duplicate permission | Prevent selection or show "Already added" |
| RBAC-FE-002 | PermissionGuard | User lacks permission | Component returns null or Redirects to 403 Page |

### 4.2 E2E Testing

| ID | Flow Name | Steps | Expected Outcome |
| :--- | :--- | :--- | :--- |
| RBAC-E2E-001 | Role Assignment | 1. Admin assigns "Editor" to User A<br>2. User A logs in | User A can see Editor-only menus |

---

## 5. Manual Testing Scenarios

| ID | Scenario | Steps | Expected Result |
| :--- | :--- | :--- | :--- |
| RBAC-MAN-001 | Menu Visibility | Log in as different roles | Menu items appear/disappear based on role |

---

## 6. Security Testing

- **Privilege Escalation:** Ensure regular users cannot assign Admin role to themselves.
