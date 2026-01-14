---
description: Workflow standar untuk mengimplementasikan kode dari Task, Feature, atau Module.
---

> [!TIP]
> **Skills Delegation**:
> - Gunakan skill `feature-implementation` untuk metodologi TDD dan sinkronisasi dokumentasi.
> - Gunakan skill `tech-stacks` untuk memastikan standar arsitektur (Laravel, Vue, dll) dipatuhi.

1.  **Identifikasi Scope**:
    *   Tentukan target: **Single Task** (e.g., `IAM-BE-01`) atau **Feature/Module** (e.g., `User Management`).
    *   Jika **Feature/Module**, ambil daftar tugas terkait dari `.agent/tasks/implementation-tasks.md` dan kerjakan berurutan (Backend First -> Frontend).

2.  **Context Loading (Wajib)**:
    *   Baca **Feature Docs** di `.agent/documents/application/modules/...` untuk memahami *Business Rules* dan *ERD*.
    *   Baca **API Specs** (untuk Backend) atau **Test Scenarios** untuk memahami ekspektasi output.

3.  **Iterasi Implementasi (Per Task)**:
    *   **Step 3.1: Create/Update Test (Red)**
        *   Untuk Backend: Buat Feature Test (seperti `tests/Feature/Scenarios/...`).
        *   Untuk Frontend: Pastikan setup page/component test siap.
        *   Jalankan test -> Pastikan gagal (Red).
    *   **Step 3.2: Write Code (Green)**
        *   Implementasi solusi (Migration -> Model -> Service -> Controller / Store -> UI).
        *   **Strict Rule**: Pastikan nama field database, endpoint API, dan headers (`Accept`, `Authorization`) SAMA PERSIS dengan dokumentasi.
    *   **Step 3.3: Verification**
        *   Jalankan test suite.
        *   Pastikan passed (Green).

4.  **Finalisasi Per Task**:
    *   Jalankan linting/formatting.
    *   Jalankan workflow `/update-task` untuk menandai task sebagai `Done`.
    *   Commit dengan format semantic: `feat(<module>): <description> (<TASK-ID>)`.
