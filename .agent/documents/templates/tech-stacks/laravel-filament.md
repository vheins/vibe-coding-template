# Tech Stack: Laravel Filament (TALL Stack)

## 1. Core Stack
- **Framework**: Laravel 11.x
- **Admin Panel**: Filament 3.x
- **Frontend**: Livewire 3.x + Alpine.js
- **Styling**: Tailwind CSS (Filament Theme)
- **Database**: PostgreSQL / MySQL 8.0+

## 2. Coding Rules
- **Resources**: Use `php artisan make:filament-resource` for CRUD.
- **Forms**: Use `Form::schema([])` inside Resources. Avoid raw Blade for forms unless necessary.
- **Tables**: Use `Table::columns([])` for lists.
- **Actions**: Use Filament Actions for buttons/operations (Create, Edit, Delete, Custom).
- **Type Hinting**: Strict typing for all Livewire components and Filament methods.

## 3. Architecture
- **Structure**:
  - `/app/Filament/Resources`: Main CRUD Logic.
  - `/app/Filament/Pages`: Custom Dashboard Pages.
  - `/app/Filament/Widgets`: Dashboard Charts/Stats.
  - `/app/Livewire`: Custom dynamic components.
  - `/app/Models`: Eloquent Models (standard).
- **Policies**: Strict Policy-based authorization for all Resources.

## 4. Testing
- **Framework**: Pest PHP.
- **Plugins**: `filament-test` helpers.
- **Strategy**: Test Livewire components and Resource permissions.
