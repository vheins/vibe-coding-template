---
trigger: always_on
---

# Documentation Standards & Rules

You are the guardian of this project's documentation. Adhere to these rules strictly when creating or updating any technical documentation.

## 1. Core Principles
- **No Gap Policy**: Every User Story must have an API Endpoint. Every API Endpoint must have a Test Scenario.
- **Synchronization**: If you update the Logic/Business Rule, you MUST update the API and Testing docs. Use the "Change One, Check All" principle.
- **Research First**: Never guess. Research the codebase or industry best practices before writing "Overview" or "Features".

## 2. Structure Standards
All modules must follow this structure:
- `.agent/documents/application/modules/<module>/overview.md` (Landing Page)
- `.agent/documents/application/modules/<module>/<feature>.md` (Detailed Logic - Optional/Complex)
- `.agent/documents/application/api/<module>/api-<module>.md` (Technical Contract)
- `.agent/documents/application/testing/<module>/test-<module>.md` (Verification Plan)

## 3. Content Guidelines

### Feature Documentation
- **User Stories**: MUST use the table format with `ID`, `As a`, `I want to`, `So that`, `Acceptance Criteria`, and `Priority`.
- **Detail**: "So that" (Goal/Benefit) is mandatory to understand the *Why*.
- **Data Model**: MUST include a Mermaid ERD for relationships.

### API Documentation
- **Standard**: **JSON:API** (https://jsonapi.org) is mandatory.
- **Content**:
    - URL must use kebab-case.
    - Explicit `Request` and `Response` JSON bodies.
    - Include `4xx` and `5xx` error examples.

### Testing Documentation
- **Coverage**:
    - **Positive**: Happy paths.
    - **Negative**: Validation errors, edge cases.
    - **Monkey**: Chaos/Fuzzing tests (e.g., random inputs, ID enumeration).
    - **Security**: IDOR, XSS, Permission checks.
- **Priority**: Mark every case as `High`, `Medium`, or `Low`.

## 4. Templates
ALWAYS use the templates located in `.agent/documents/templates/` as your base. Do not invent new formats.

## 5. Workflows
- To create new docs: Use the logic from `workflows/create-documentation.md`.
- To update docs: Use the logic from `workflows/update-documentation.md`.

FAILURE TO FOLLOW THESE RULES will result in documentation drift and is unacceptable.
