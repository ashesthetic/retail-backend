# Retail + Gas Station Management System

A comprehensive retail and gas station management system built with modern web technologies.

## Repository

- **Backend Repository**: [retail-backend](https://github.com/ashesthetic/retail-backend)
- **Backend URL**: `git@github.com:ashesthetic/retail-backend.git`
- **Frontend Repository**: [retail-frontend](https://github.com/ashesthetic/retail-frontend)
- **Frontend URL**: `git@github.com:ashesthetic/retail-frontend.git`

## Tech Stack

### Backend
- **Framework**: Laravel (PHP)
- **Standards**: PSR-12 coding standards with project-specific adjustments
- **PHP Version**: Requires PHP with strict types support
- **Database**: MySQL/PostgreSQL (configurable via environment)

### Frontend
- **Framework**: React with TypeScript
- **Styling**: Tailwind CSS
- **Build Tool**: Vite/Webpack
- **Location**: `frontend/` folder (separate repository)

## Project Structure

```
retail/
├── backend/                 # Laravel backend (this repository)
├── frontend/               # React + TypeScript frontend (separate repo)
├── .env                    # Environment configuration
└── README.md              # This file
```

## Setup Instructions

### Prerequisites

- PHP >= 8.1
- Composer
- Node.js >= 18
- npm/yarn
- MySQL/PostgreSQL
- Git

### Backend Setup (Laravel)

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
   - Set database credentials
   - Configure virtual host URLs
   - Set timezone to Alberta (America/Edmonton)

5. **Database Setup**:
   ```bash
   php artisan migrate
   php artisan db:seed
   ```

6. **Start the development server**:
   ```bash
   php artisan serve
   ```

### Frontend Setup (React + TypeScript)

1. **Clone the frontend repository**:
   ```bash
   git clone git@github.com:ashesthetic/retail-frontend.git frontend
   cd frontend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Start development server**:
   ```bash
   npm run dev
   ```

## Development Guidelines

### Code Style

- **PHP**: Follow PSR-12 standards with project-specific formatting
- **JavaScript/TypeScript**: Use ESLint and Prettier
- **Formatting Rules**:
  - Space before and after parentheses: `if ( $value )`
  - Opening brace on same line: `function test() {`
  - Indentation: 4 spaces (no tabs)

### Naming Conventions

- **PHP**: camelCase for variables/functions, snake_case for array keys
- **TypeScript**: camelCase for variables/functions, PascalCase for components

### Testing

- **Backend**: PHPUnit for Laravel features
- **Frontend**: Jest + React Testing Library
- **Pattern**: Arrange–Act–Assert in all tests

### Pre-commit Hooks

#### Backend
- PHP_CodeSniffer for code quality

#### Frontend
- Husky + lint-staged
- ESLint + Prettier
- Jest for automated testing

## Features

- Retail inventory management
- Gas station operations
- Point of sale system
- Customer management
- Sales reporting and analytics
- Multi-location support

## Configuration

### Timezone
- **Default**: Alberta timezone (America/Edmonton)
- **Date Format**: `Monday, 22 September 2025, 03:55 PM`

### Virtual Hosts
- Use virtual host URLs from `.env` configuration
- Separate URLs for frontend and backend environments

## Security

- All database queries use secure, parameterized statements
- Environment variables for sensitive configuration
- Input validation on all user inputs
- CSRF protection enabled
- Rate limiting on API endpoints

## Contributing

1. Follow the established coding standards
2. Write tests for new features
3. Use descriptive commit messages
4. Create feature branches for new development
5. Submit pull requests for code review

## Support

For issues and feature requests, please use the GitHub issues tracker in the respective repositories.
