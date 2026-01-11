# Tech Stack: Laravel (Enterprise)

## 1. Core Stack
- **Framework**: Laravel 11.x
- **Language**: PHP 8.2+
- **Database**: PostgreSQL / MySQL 8.0+
- **API Standard**: JSON:API (Strict)

## 2. Architectural Guidelines
- **Pattern**: Service-Repository Pattern.
  - *Controller*: Handle Request/Response only.
  - *Service*: Business Logic (Transaction Management).
  - *Repository*: Eloquent/DB Query abstraction.
- **Models**: Use `Guarded` ($guarded = []) and Casts.
- **DTO**: Use `DataTransferObject` (spatie/laravel-data) for complex inputs.

## 3. Coding Standards
- **Strict Types**: Always use `declare(strict_types=1);`.
- **Type Hinting**: All method arguments and return types must be typed.
- **Error Handling**: Throw custom Exceptions, catch in `ExceptionHandler`.
- **Validation**: Use FormRequests for strict validation.

## 4. Testing Strategy
- **Framework**: Pest PHP / PHPUnit.
- **Strategy**: 
  - *Feature Test*: Test API Endpoints (Happy & Sad paths).
  - *Unit Test*: Test Complex Service Logic.
- **Coverage**: Minimum 80%.
