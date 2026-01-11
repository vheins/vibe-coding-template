# Tech Stack: Flutter (Modular)

## 1. Core Stack
- **Framework**: Flutter 3.27+
- **Language**: Dart 3.0+
- **State Management**: Riverpod (Generator)
- **Architecture**: Clean Architecture (Feature-first)

## 2. Coding Rules
- **Immutability**: Use `freezed` for all Data Classes and State.
- **Async**: Use `Future` and `Stream` with `AsyncValue` in Riverpod.
- **Widgets**: Split large widgets into smaller, private extracted widgets.
- **Null Safety**: Strict null safety compliant.

## 3. Architecture
- **Structure**:
  - `/lib/src/features`: Feature modules (Auth, Product, etc).
  - `/lib/src/common_widgets`: Shared UI components.
  - `/lib/src/utils`: Helpers and extensions.
- **Layering**:
  - *Presentation*: Widgets & Controllers.
  - *Domain*: Entities (Pure Dart).
  - *Data*: Repositories & Data Sources.

## 4. Testing
- **Unit**: `mocktail` for mocking repositories.
- **Widget**: Test UI logic and interactions.
- **Integration**: `integration_test` package for E2E.
