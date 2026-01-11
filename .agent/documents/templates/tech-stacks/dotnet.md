# Tech Stack: .NET (Enterprise)

## 1. Core Stack
- **Framework**: .NET 10 (LTS)
- **Language**: C# 14+
- **Web Framework**: ASP.NET Core Web API
- **ORM**: Entity Framework Core
- **Database**: SQL Server 2022+ / PostgreSQL 17+

## 2. Coding Rules
- **Async/Await**: Use `async Task<T>` for all I/O operations.
- **Dependency Injection**: Use built-in `IServiceCollection`.
- **LINQ**: Prefer Method Syntax over Query Syntax.
- **Nullability**: Enable `<Nullable>enable</Nullable>` in csproj.
- **Records**: Use `record` for DTOs and immutable data structures.

## 3. Architecture
- **Pattern**: Clean Architecture.
- **Structure**:
  - `src/Application`: Interfaces, MediatR Handlers, DTOs.
  - `src/Domain`: Entities, Value Objects, Domain Events.
  - `src/Infrastructure`: EF Core, External Services.
  - `src/API`: Controllers, Middleware.

## 4. Testing
- **Framework**: xUnit.
- **Assertions**: FluentAssertions.
- **Mocking**: NSubstitute or Moq.
- **Integration**: `WebApplicationFactory`.
