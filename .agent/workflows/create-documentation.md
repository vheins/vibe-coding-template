---
description: create documentation
---

Follow these steps to create a new documentation set for a module:

1.  **Identify the Module Name**:
    *   Determine the name of the module from the user's request (e.g., "Payment", "Order", "Inventory").
    *   Let's refer to this as `<module-slug>` (kebab-case, e.g., `payment-gateway`).

2.  **Create Directory Structure**:
    *   Create the following folders if they don't exist:
        *   `.agent/documents/application/modules/<module-slug>/`
        *   `.agent/documents/application/api/<module-slug>/`
        *   `.agent/documents/application/testing/<module-slug>/`

3.  **Read Templates**:
    *   Read the content of the following template files to understand the structure:
        *   `.agent/documents/templates/module-documentation.md`
        *   `.agent/documents/templates/api-documentation.md`
        *   `.agent/documents/templates/testing-documentation.md`

4.  **Create Documentation Files**:
    *   **Module Overview**:
        *   Create `.agent/documents/application/modules/<module-slug>/overview.md`.
        *   Use the content from `module-documentation.md`.
        *   Replace placeholders like `<module-name>` with the actual module name (e.g., "Payment Gateway").
        *   Ensure the Relative Links are correct:
            *   Link to All Modules: `../../../README.md`
            *   Link to Testing: `../../testing/<module-slug>/overview.md`
            *   Link to API: `../../api/<module-slug>/api-<module-slug>.md`
    
    *   **API Specification**:
        *   Create `.agent/documents/application/api/<module-slug>/api-<module-slug>.md`.
        *   Use the content from `api-documentation.md`.
        *   Replace placeholders.
        *   Ensure Relative Links:
            *   Back to Module: `../../modules/<module-slug>/overview.md`

    *   **Test Scenarios**:
        *   Create `.agent/documents/application/testing/<module-slug>/test-<module-slug>.md` (or `overview.md` if prefered as main entry).
        *   Use the content from `testing-documentation.md`.
        *   Replace placeholders.
        *   Ensure Relative Links:
            *   Back to Module: `../../modules/<module-slug>/overview.md`
            *   Link to API: `../../api/<module-slug>/api-<module-slug>.md`

5.  **Review and Finalize**:
    *   Notify the user that the documentation skeleton has been created.
    *   List the created files.
    *   Ask the user for specific business logic or API details to fill in the sections.

