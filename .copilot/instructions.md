# Copilot Instructions

You are an experienced full stack engineer. Follow these rules:

## General Rules
- Always check for security concerns in code.
- This is a retail + gas station management system.
- Backend: Laravel (root repo).  
- Frontend: React + TypeScript + Tailwind (frontend folder repo).  
- Do not start servers during testing. Always ask me to start the server.  
- Use virtual host URLs (from `.env`) for both frontend and backend.  
- Use Alberta timezone. Date/time format: `Monday, 22 September 2025, 03:55 PM`.  
- Follow existing patterns and styles before introducing new ones.  
- Reuse components when possible. Keep code simple, modular, and reusable.  

## Coding Style
- Follow **PSR-12** coding standards with project-specific adjustments.  
- Use descriptive variable and function names.  
- Use type hints in PHP and `declare(strict_types=1);`.  
- Prefer early returns instead of nested conditionals.  
- Naming conventions:  
  - camelCase → variables, functions  
  - snake_case → array keys  
- Formatting:  
  - **Space before and after parentheses** → `if ( $value )`  
  - **Opening curly brace on the same line** → `function test() {`  
  - Indentation: 4 spaces (no tabs)  

### Example (Laravel PHP)
```php
<?php

declare(strict_types=1);

namespace App\Services;

use App\Models\Sale;
use Illuminate\Support\Collection;

class SalesService {
    /**
     * Get sales summary for a given date.
     *
     * @param string $date
     * @return Collection
     */
    public function getSalesSummary( string $date ): Collection {
        $sales = Sale::whereDate( 'created_at', $date )->get();

        if ( $sales->isEmpty() ) {
            return collect( [] );
        }

        return $sales->groupBy( 'category' )->map( fn ( $items ) => [
            'count' => $items->count(),
            'total' => $items->sum( 'amount' ),
        ] );
    }
}
```

### Framework & Libraries
- Use Laravel best practices (helpers, collections).
- Use React + TypeScript + Tailwind for frontend.
- Prefer reusable UI components over one-offs.

### Example (React + TypeScript + Tailwind)
```javascript
import React from "react";

type ButtonProps = {
  label: string;
  onClick: () => void;
  disabled?: boolean;
};

export default function Button( { label, onClick, disabled = false }: ButtonProps ) {
  return (
    <button
      onClick={onClick}
      disabled={disabled}
      className="rounded-2xl bg-blue-600 px-4 py-2 text-white shadow hover:bg-blue-700 disabled:opacity-50"
    >
      {label}
    </button>
  );
}
```

### Comments & Documentation
- Add PHPDoc/TypeDoc for functions, classes, and props.
- Use inline comments only for non-obvious logic.
- Write self-explanatory code over excessive commenting.

### Testing
- Write PHPUnit tests for backend features.
- Write Jest + React Testing Library tests for frontend.
- Use Arrange–Act–Assert pattern in tests.

### Example (Jest Test)
```javascript
import { render, screen, fireEvent } from "@testing-library/react";
import Button from "./Button";

test( "Button calls onClick when clicked", () => {
  const handleClick = jest.fn();
  render( <Button label="Click Me" onClick={handleClick} /> );

  fireEvent.click( screen.getByText( "Click Me" ) );

  expect( handleClick ).toHaveBeenCalledTimes( 1 );
} );
```

### Other Preferences
- Use environment variables (.env) instead of hardcoding.
- Database queries must be secure and efficient.
- Setup pre-commit hooks:
    - Laravel: PHP_CodeSniffer
    - React: Husky, lint-staged, ESLint, Prettier, Jest
- For new setup instruction, always update README.md file.