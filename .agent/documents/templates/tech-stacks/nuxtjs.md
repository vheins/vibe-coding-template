# Tech Stack: Nuxt.js (Vue 3)

## 1. Core Stack
- **Framework**: Nuxt 3.x
- **Language**: TypeScript
- **Styling**: Tailwind CSS / UnoCSS
- **State**: Pinia (Standard)
- **HTTP**: `$fetch` / `useFetch` (Native)

## 2. Coding Rules
- **Composables**: Use auto-imported composables for logic reuse.
- **Server Routes**: Use `/server/api` for backend logic.
- **Type Safety**: Strictly typed props and emits using `defineProps<T>()`.
- **Pages**: Use `definePageMeta` for middleware and layout config.
- **Store Syntax**: Use Setup Stores (`function`) exclusively.

## 3. Architecture
- **Structure**:
  - `/components`: Atomic components (Auto-imported).
  - `/composables`: Shared logic (Auto-imported).
  - `/pages`: File-system routing.
  - `/server`: API routes (Nitro).
  - `/stores`: Pinia stores.

## 4. Testing
- **Unit**: Vitest + @nuxt/test-utils.
- **E2E**: Playwright.
