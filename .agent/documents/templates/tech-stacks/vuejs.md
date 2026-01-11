# Tech Stack: Vue.js (Vite)

## 1. Core Stack
- **Build Tool**: Vite
- **Language**: TypeScript
- **Styling**: SCSS / Tailwind CSS
- **State**: Pinia (Standard)
- **Routing**: Vue Router 4

## 2. Coding Rules
- **Syntax**: Script Setup (`<script setup lang="ts">`) is mandatory.
- **Reactivity**: Prefer `ref` over `reactive` for consistency.
- **Composables**: Extract logic into `useFeature` functions.
- **Props**: Use `defineProps` with interface defaults.
- **Store Syntax**: Use Setup Stores (`function`) exclusively.

## 3. Architecture
- **Structure**:
  - `/src/components`: Shared components.
  - `/src/views`: Page views.
  - `/src/stores`: Pinia definitions.
  - `/src/composables`: Logic reuse.
  - `/src/services`: API wrappers.

## 4. Testing
- **Unit**: Vitest + Vue Test Utils.
- **E2E**: Cypress.
