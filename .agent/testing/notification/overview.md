# Testing Overview: Notification Module

- [Back to Module Overview](../../modules/notification/overview.md)

---

## 1. Test Overview

- **Module Name:** Notification
- **Scope:** Unit Test (Template Rendering), Integration Test (API & Queue), E2E (Flow pengiriman).
- **Test Tools:** Jest, Supertest, Mailhog (untuk mock SMTP).

---

## 2. Test Strategy

### 2.1 Unit Testing
- Test fungsi render template Mustache.
- Test logic preference filtering.

### 2.2 Integration Testing
- Test API `POST /send` response 202.
- Test API `GET /notifications` pagination.
- Verify job masuk ke Redis Queue.

### 2.3 End-to-End (E2E) Testing
- Simulate send -> verify mock email received.
- Verify notification appears in `GET /list`.

---
