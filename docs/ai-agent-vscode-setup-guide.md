# VS Code Setup Guide for AI Agents (GitHub Copilot)

## Overview

This guide provides best practices for structuring your projects and configuring VS Code to maximize effectiveness when working with AI coding assistants like GitHub Copilot.

---

## Essential Files for AI Context

### 1\. `.github/copilot-instructions.md`

Create project-specific instructions for GitHub Copilot:

```markdown
# Project Context for GitHub Copilot

## Project Overview
[Brief description of what this project does]

## Tech Stack
- Language: [e.g., Python 3.11, TypeScript 5.0]
- Framework: [e.g., React 18, FastAPI]
- Database: [e.g., PostgreSQL, MongoDB]
- Testing: [e.g., Jest, pytest]

## Coding Standards
- Use [specific style guide, e.g., PEP 8, Airbnb]
- Prefer [functional/OOP/specific patterns]
- Always include type hints/annotations
- Write docstrings for all functions

## Architecture Patterns
- Follow [MVC/MVVM/Clean Architecture/etc.]
- Use dependency injection
- Separate concerns: [specific patterns]

## Naming Conventions
- Files: [snake_case/kebab-case/PascalCase]
- Functions: [camelCase/snake_case]
- Classes: [PascalCase]
- Constants: [UPPER_SNAKE_CASE]

## Testing Requirements
- Minimum coverage: [e.g., 80%]
- Test file naming: [pattern]
- Mock external dependencies
```

### 2\. `README.md`

A comprehensive README helps AI understand project context:

```markdown
# Project Name

## Description
[Clear, concise description]

## Getting Started

### Prerequisites
- Node.js 18+
- Python 3.11+
- Docker

### Installation
```bash
npm install
# or
pip install -r requirements.txt
```

### Running the Project

```bash
npm run dev
# or
python main.py
```

## Project Structure

```
project-root/
├── src/
│   ├── components/
│   ├── services/
│   ├── utils/
│   └── types/
├── tests/
├── docs/
└── config/
```

## Key Concepts

\[Explain domain-specific concepts, business logic, or unique patterns\]

## Contributing

\[Guidelines for code contributions\]

```

### 3. `ARCHITECTURE.md`
Document your system architecture:

```markdown
# Architecture Documentation

## System Overview
[High-level architecture diagram or description]

## Component Responsibilities
- **Component A**: Handles X
- **Component B**: Manages Y

## Data Flow
[Describe how data moves through the system]

## Design Decisions
- **Decision**: Why we chose X over Y
- **Trade-offs**: What we gained/lost

## External Dependencies
- API A: Used for [purpose]
- Service B: Handles [functionality]
```

### 4\. `CONVENTIONS.md`

Detailed coding conventions:

```markdown
# Coding Conventions

## File Organization
- One component per file
- Group related files in directories
- Index files for clean imports

## Error Handling
- Always use try-catch for async operations
- Create custom error classes
- Log errors with context

## Comments
- Use JSDoc/docstrings for public APIs
- Explain "why" not "what"
- Keep comments up-to-date

## Git Commit Messages
- Format: `type(scope): description`
- Types: feat, fix, docs, refactor, test, chore
```

---

## Directory Structure Best Practices

### Recommended Project Structure

```
project-root/
├── .github/
│   ├── copilot-instructions.md
│   └── workflows/
├── .vscode/
│   ├── settings.json
│   ├── extensions.json
│   └── tasks.json
├── docs/
│   ├── ARCHITECTURE.md
│   ├── API.md
│   └── CONVENTIONS.md
├── src/
│   ├── components/
│   ├── services/
│   ├── utils/
│   ├── types/
│   ├── constants/
│   └── config/
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── scripts/
├── config/
├── .gitignore
├── .editorconfig
├── README.md
├── package.json (or requirements.txt, etc.)
└── tsconfig.json (or equivalent config)
```

---

## VS Code Configuration

### `.vscode/settings.json`

Project-specific VS Code settings:

```json
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll": true,
    "source.organizeImports": true
  },
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "files.associations": {
    "*.css": "css",
    "*.js": "javascript"
  },
  "github.copilot.enable": {
    "*": true,
    "yaml": true,
    "plaintext": false,
    "markdown": true
  },
  "github.copilot.advanced": {
    "debug.overrideEngine": "gpt-4",
    "debug.testOverrideProxyUrl": "",
    "debug.overrideProxyUrl": ""
  },
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.organizeImports": true
    }
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

### `.vscode/extensions.json`

Recommended extensions:

```json
{
  "recommendations": [
    "github.copilot",
    "github.copilot-chat",
    "dbaeumer.vscode-eslint",
    "esbenp.prettier-vscode",
    "ms-python.python",
    "ms-python.vscode-pylance",
    "ms-vscode.vscode-typescript-next",
    "usernamehw.errorlens",
    "streetsidesoftware.code-spell-checker"
  ]
}
```

### `.vscode/tasks.json`

Common tasks for quick access:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Run Tests",
      "type": "shell",
      "command": "npm test",
      "group": {
        "kind": "test",
        "isDefault": true
      }
    },
    {
      "label": "Build",
      "type": "shell",
      "command": "npm run build",
      "group": {
        "kind": "build",
        "isDefault": true
      }
    }
  ]
}
```

---

## Configuration Files for Better AI Context

### `.editorconfig`

Consistent coding styles:

```ini
root = true

[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
indent_style = space
indent_size = 2

[*.py]
indent_size = 4

[*.md]
trim_trailing_whitespace = false

[Makefile]
indent_style = tab
```

### `tsconfig.json` (TypeScript)

Strong typing helps AI understand code:

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "ESNext",
    "lib": ["ES2020", "DOM"],
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"],
      "@components/*": ["src/components/*"],
      "@utils/*": ["src/utils/*"]
    }
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist"]
}
```

### `pyproject.toml` (Python)

Python project configuration:

```toml
[tool.black]
line-length = 88
target-version = ['py311']
include = '\.pyi?$'

[tool.isort]
profile = "black"
line_length = 88

[tool.pytest.ini_options]
testpaths = ["tests"]
python_files = ["test_*.py"]
python_functions = ["test_*"]

[tool.mypy]
python_version = "3.11"
warn_return_any = true
warn_unused_configs = true
disallow_untyped_defs = true
```

---

## Best Practices for AI-Friendly Code

### 1\. Use Descriptive Names

```javascript
// Good - AI understands intent
function calculateUserMonthlySubscriptionTotal(userId, month) { }

// Bad - AI lacks context
function calc(u, m) { }
```

### 2\. Add Type Annotations

```typescript
// TypeScript
interface User {
  id: string;
  name: string;
  email: string;
}

function getUser(id: string): Promise<User> { }
```

```python
# Python
from typing import List, Optional

def get_users(limit: int = 10) -> List[User]:
    pass
```

### 3\. Write Clear Comments for Complex Logic

```javascript
/**
 * Calculates the compound interest using the formula A = P(1 + r/n)^(nt)
 * where P = principal, r = rate, n = compounds per year, t = years
 */
function calculateCompoundInterest(principal, rate, compounds, years) {
  return principal * Math.pow(1 + rate / compounds, compounds * years);
}
```

### 4\. Use Consistent File Naming

```
// Components
UserProfile.tsx
OrderList.tsx

// Services
userService.ts
orderService.ts

// Utils
dateFormatter.ts
stringHelpers.ts

// Tests
UserProfile.test.tsx
userService.test.ts
```

### 5\. Create Type Definition Files

```typescript
// types/user.ts
export interface User {
  id: string;
  name: string;
  email: string;
  role: UserRole;
}

export enum UserRole {
  ADMIN = 'admin',
  USER = 'user',
  GUEST = 'guest'
}
```

---

## GitHub Copilot-Specific Tips

### 1\. Use Copilot Chat Effectively

* **@workspace**: Ask about your entire workspace

* **#file**: Reference specific files

* **#selection**: Work with selected code

* **/explain**: Understand complex code

* **/fix**: Get bug fixes

* **/tests**: Generate test cases

### 2\. Write Intent Comments

```javascript
// Create a function that fetches user data from the API,
// caches it in localStorage, and returns a User object
// Handle errors gracefully and return null if user not found
```

### 3\. Provide Examples in Comments

```python
# Example usage:
# result = process_data([1, 2, 3], transform=lambda x: x * 2)
# result should be [2, 4, 6]
def process_data(items, transform):
    pass
```

### 4\. Use TODO Comments

```javascript
// TODO: Add input validation for email format
// TODO: Implement retry logic for failed API calls
// TODO: Add unit tests for edge cases
```

---

## Documentation Files to Include

### `docs/API.md`

Document your API endpoints:

```markdown
# API Documentation

## Endpoints

### GET /api/users
Retrieves a list of users

**Parameters:**
- `limit` (optional): Number of users to return (default: 10)
- `offset` (optional): Pagination offset (default: 0)

**Response:**
```json
{
  "users": [...],
  "total": 100
}
```

**Example:**

```bash
curl https://api.example.com/api/users?limit=5
```

```

### `docs/TROUBLESHOOTING.md`
Common issues and solutions:

```markdown
# Troubleshooting Guide

## Common Issues

### Issue: Build fails with "Module not found"
**Solution:** Run `npm install` to ensure all dependencies are installed

### Issue: Tests fail in CI but pass locally
**Solution:** Check environment variables and ensure test database is configured
```

---

## Environment Configuration

### `.env.example`

Template for environment variables:

```bash
# Database
DATABASE_URL=postgresql://localhost:5432/mydb
DATABASE_POOL_SIZE=10

# API Keys
API_KEY=your_api_key_here
SECRET_KEY=your_secret_key_here

# Feature Flags
ENABLE_FEATURE_X=false
DEBUG_MODE=false

# External Services
STRIPE_API_KEY=sk_test_...
SENDGRID_API_KEY=SG...
```

---

## Pre-commit Hooks

### `.husky/pre-commit` or similar

Ensure code quality before commits:

```bash
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npm run lint
npm run type-check
npm test
```

---

## Additional Tips

### 1\. Keep Dependencies Updated

Maintain a `package.json` or `requirements.txt` with clear version constraints:

```json
{
  "dependencies": {
    "react": "^18.2.0",
    "typescript": "^5.0.0"
  }
}
```

### 2\. Use Linting Configuration

`.eslintrc.json` or `.pylintrc` helps AI understand code standards:

```json
{
  "extends": ["eslint:recommended", "plugin:@typescript-eslint/recommended"],
  "rules": {
    "no-console": "warn",
    "prefer-const": "error",
    "@typescript-eslint/explicit-function-return-type": "warn"
  }
}
```

### 3\. Create a Glossary

`docs/GLOSSARY.md` for domain-specific terms:

```markdown
# Glossary

- **Widget**: A reusable UI component that displays data
- **Pipeline**: A series of data processing steps
- **Tenant**: An organization using our multi-tenant system
```

### 4\. Document Dependencies

`docs/DEPENDENCIES.md`:

```markdown
# Dependencies

## Core Dependencies
- **React**: UI framework - chosen for component reusability
- **TypeScript**: Type safety and better IDE support

## Why We Use X
- **Zustand over Redux**: Simpler API, less boilerplate
- **Vitest over Jest**: Faster, better ESM support
```

---

## Checklist for New Projects

* \[ \] Create `.github/copilot-instructions.md`

* \[ \] Write comprehensive `README.md`

* \[ \] Set up `.vscode/settings.json`

* \[ \] Add `.vscode/extensions.json`

* \[ \] Configure `.editorconfig`

* \[ \] Add type configuration (`tsconfig.json`, `pyproject.toml`)

* \[ \] Create `ARCHITECTURE.md`

* \[ \] Document conventions in `CONVENTIONS.md`

* \[ \] Set up linting and formatting

* \[ \] Add `.env.example`

* \[ \] Create project structure with clear directories

* \[ \] Add API documentation

* \[ \] Set up pre-commit hooks

* \[ \] Document dependencies and why they were chosen

---

## Resources

* [GitHub Copilot Documentation](https://docs.github.com/en/copilot)

* [VS Code Documentation](https://code.visualstudio.com/docs)

* [TypeScript Handbook](https://www.typescriptlang.org/docs/)

* [Python Type Hints](https://docs.python.org/3/library/typing.html)

---

## Conclusion

By implementing these files, structures, and configurations, you create a rich context that helps AI agents like GitHub Copilot understand your project better, leading to more accurate and relevant code suggestions. The key is providing clear, consistent, and comprehensive documentation that both humans and AI can understand.