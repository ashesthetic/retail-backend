# Retail + Gas Station Management System API

A comprehensive retail and gas station management system API built with Laravel. This is the backend API that serves data to the React frontend application.

## Repository

- **Backend Repository**: [retail-backend](https://github.com/ashesthetic/retail-backend)
- **Backend URL**: `git@github.com:ashesthetic/retail-backend.git`
- **Frontend Repository**: [retail-frontend](https://github.com/ashesthetic/retail-frontend)
- **Frontend URL**: `git@github.com:ashesthetic/retail-frontend.git`

## API Information

- **Base URL**: `https://api.retail.test`
- **Version**: Laravel 12.x
- **Type**: API-only (no web views)
- **Authentication**: Laravel Sanctum

## Tech Stack

### Backend
- **Framework**: Laravel 12.x (PHP)
- **Standards**: PSR-12 coding standards with project-specific adjustments
- **PHP Version**: PHP 8.1+
- **Database**: MySQL
- **Authentication**: Laravel Sanctum
- **Testing**: PHPUnit

### Frontend
- **Framework**: React with TypeScript
- **Styling**: Tailwind CSS
- **Build Tool**: Vite
- **Location**: `frontend/` folder (separate repository)

## Quick Start

### Prerequisites

- PHP >= 8.1
- Composer
- Laravel Valet (for local development)
- MySQL (database)
- Git

### Installation

1. **Clone the repository**:
   ```bash
   git clone git@github.com:ashesthetic/retail-backend.git
   cd retail-backend
   ```

2. **Install PHP dependencies**:
   ```bash
   composer install
   ```

3. **Environment Configuration**:
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. **Configure your `.env` file**:
   ```env
   APP_NAME="Retail API"
   APP_URL=https://api.retail.test
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=retail_db
   DB_USERNAME=root
   DB_PASSWORD=your_password
   ```

5. **Database Setup**:
   ```bash
   # Create the database first
   mysql -u root -p -e "CREATE DATABASE retail_db;"
   
   # Run migrations
   php artisan migrate
   php artisan db:seed
   ```

6. **Virtual Host Setup** (using Laravel Valet):
   ```bash
   valet link api.retail
   valet secure api.retail
   ```

7. **Test the API**:
   ```bash
   curl https://api.retail.test/api/health
   ```

## API Endpoints

### Public Endpoints
- **Health Check**: `GET /api/health`
- **Version Info**: `GET /api/version`

### Authentication Required
- **User Profile**: `GET /api/user` (requires Sanctum token)

All API routes are prefixed with `/api` and return JSON responses.

## Development Guidelines

### Code Style

- **PHP**: Follow PSR-12 standards with project-specific formatting
- **Formatting Rules**:
  - Space before and after parentheses: `if ( $value )`
  - Opening brace on same line: `function test() {`
  - Indentation: 4 spaces (no tabs)
  - Use `declare(strict_types=1);` in all PHP files

### Naming Conventions

- **PHP**: camelCase for variables/functions, snake_case for array keys
- **Database**: snake_case for table and column names
- **Routes**: kebab-case for API endpoints

### Testing

- **Backend**: PHPUnit for Laravel features
- **Pattern**: Arrange–Act–Assert in all tests
- **Coverage**: Aim for >80% code coverage

### Example API Controller

```php
<?php

declare(strict_types=1);

namespace App\Http\Controllers\Api;

use App\Http\Controllers\Controller;
use Illuminate\Http\JsonResponse;
use Illuminate\Http\Request;

class ExampleController extends Controller {
    /**
     * Get example data.
     */
    public function index( Request $request ): JsonResponse {
        $data = collect( [
            'message' => 'Example API endpoint',
            'timestamp' => now()->toISOString(),
        ] );

        return response()->json( $data );
    }
}
```

## Features

- Retail inventory management API
- Gas station operations API
- Point of sale system API
- Customer management API
- Sales reporting and analytics API
- Multi-location support
- RESTful API design
- JSON responses
- API authentication with Sanctum

## Configuration

### Timezone
- **Default**: Alberta timezone (America/Edmonton)
- **Date Format**: ISO 8601 (`2025-09-22T15:30:00.000Z`)

### CORS
- Configured for frontend domain
- Supports preflight requests
- JSON content type handling

## Security

- Laravel Sanctum for API authentication
- HTTPS enforced (via Valet)
- Input validation on all endpoints
- Rate limiting on API routes
- CORS properly configured
- Environment variables for sensitive data

## Database

### Configuration
- MySQL database
- Database name: `retail_db`
- Migrations included
- Seeders for sample data

### Setup
1. Create database: `mysql -u root -p -e "CREATE DATABASE retail_db;"`
2. Configure `.env` with your MySQL credentials
3. Run migrations: `php artisan migrate`
4. Seed data: `php artisan db:seed`

### Production
- MySQL recommended for production
- Environment-based configuration
- Database backups recommended

## Contributing

1. Follow the established coding standards
2. Write tests for new API endpoints
3. Use descriptive commit messages
4. Create feature branches for new development
5. Submit pull requests for code review

## Frontend Integration

The React frontend should connect to this API using:
- Base URL: `https://api.retail.test`
- Authentication: Bearer token (Sanctum)
- Content-Type: `application/json`

Example frontend API call:
```javascript
const response = await fetch('https://api.retail.test/api/health');
const data = await response.json();
```

## Support

For issues and feature requests, please use the GitHub issues tracker.
