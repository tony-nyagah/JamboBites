# JamboBites AI Agents Development Guide 🤖

## Overview

This file provides automated workflows, standards enforcement, and procedural guidelines for AI agents working on JamboBites. All agents must follow these standards to ensure code quality, consistency, and maintainability.

## Core Principles

### 1. Code Quality Standards

- **Zero Tolerance**: No code should be committed without passing all quality checks
- **Format First**: Always format code before any other operations
- **Test Coverage**: Maintain 80%+ test coverage for all new code
- **Type Safety**: All TypeScript and Python code must be fully typed
- **Documentation**: Every function, class, and module must have documentation

### 2. Automation Philosophy

- **Ask Before Breaking Changes**: Always confirm before making breaking API changes
- **Auto-Fix When Possible**: Automatically fix linting and formatting issues
- **Run Tests Automatically**: Run relevant tests after every code change
- **Validate Before Commit**: Run all checks before suggesting commits

## Development Environment Setup

### Required Tools

```bash
# Backend (Python)
- Python 3.11+
- ruff (formatting & linting)
- mypy (type checking)
- pytest (testing)
- coverage (test coverage)

# Frontend (TypeScript)
- Node.js 20+
- TypeScript 5+
- ESLint
- Prettier
- Vitest (testing)

# Mobile (Kotlin)
- JDK 17+
- Kotlin 1.9+
- ktlint (formatting)
- detekt (linting)
```

### Tool Configuration

#### Backend: Ruff Configuration

```toml
# pyproject.toml
[tool.ruff]
target-version = "py311"
line-length = 100
select = [
    "E",   # pycodestyle errors
    "W",   # pycodestyle warnings
    "F",   # pyflakes
    "I",   # isort
    "B",   # flake8-bugbear
    "C4",  # flake8-comprehensions
    "UP",  # pyupgrade
    "ARG", # flake8-unused-arguments
    "SIM", # flake8-simplify
]
ignore = [
    "E501",  # line too long (handled by formatter)
    "B008",  # function calls in argument defaults
    "W191",  # indentation contains tabs
]

[tool.ruff.format]
quote-style = "single"
indent-style = "space"
line-ending = "auto"

[tool.ruff.isort]
known-first-party = ["jambobites", "apps", "core"]

[tool.ruff.per-file-ignores]
"__init__.py" = ["F401"]
"*/migrations/*" = ["E501"]
```

#### Frontend: ESLint + Prettier

```json
// .eslintrc.json
{
  "extends": [
    "@nuxt/eslint-config",
    "plugin:@typescript-eslint/recommended",
    "plugin:vue/vue3-recommended",
    "prettier"
  ],
  "rules": {
    "vue/multi-word-component-names": "off",
    "@typescript-eslint/no-explicit-any": "error",
    "@typescript-eslint/explicit-function-return-type": "warn",
    "no-console": ["warn", { "allow": ["warn", "error"] }]
  }
}

// .prettierrc
{
  "semi": false,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5",
  "printWidth": 100,
  "arrowParens": "avoid"
}
```

#### Mobile: ktlint + detekt

```kotlin
// .editorconfig
[*.{kt,kts}]
indent_size = 4
insert_final_newline = true
max_line_length = 120
```

## Automated Workflows

### Workflow 1: Create New Django App

**Trigger**: When creating a new Django app
**Steps**:

1. Navigate to `backend/apps/`
2. Create app directory with standard structure
3. Generate `__init__.py`, `models.py`, `views.py`, `serializers.py`, `urls.py`, `admin.py`, `tests/`
4. Add app to `INSTALLED_APPS` in settings
5. Generate basic documentation in `README.md`
6. Format all files with ruff
7. Run type checks with mypy
8. Create initial migration if models exist

**Example**:

```bash
cd backend/apps
mkdir -p new_app/{tests,migrations}
touch new_app/{__init__.py,models.py,views.py,serializers.py,urls.py,admin.py}
cd ../..
ruff format backend/apps/new_app/
ruff check --fix backend/apps/new_app/
mypy backend/apps/new_app/
```

### Workflow 2: Create API Endpoint

**Trigger**: When adding a new API endpoint
**Steps**:

1. Define serializer with full type hints
2. Create ViewSet/APIView with proper permissions
3. Add URL pattern
4. Write comprehensive tests (list, create, retrieve, update, delete)
5. Add API documentation (docstrings)
6. Format code with ruff
7. Run tests to verify
8. Update API documentation

**Quality Checks**:

- ✅ Serializer has all required fields
- ✅ Proper authentication/permissions
- ✅ Input validation implemented
- ✅ Error handling for all edge cases
- ✅ Tests cover all CRUD operations
- ✅ API documentation is complete

### Workflow 3: Create Nuxt Page/Component

**Trigger**: When creating a new page or component
**Steps**:

1. Create component file with proper naming (PascalCase for components)
2. Implement with TypeScript `<script setup lang="ts">`
3. Define Props and Emits interfaces
4. Add proper accessibility attributes
5. Implement responsive design with DaisyUI
6. Add loading and error states
7. Format with Prettier
8. Lint with ESLint
9. Create corresponding test file
10. Run tests

**Quality Checks**:

- ✅ Full TypeScript typing (no `any`)
- ✅ Props and Emits properly typed
- ✅ Accessibility attributes present
- ✅ Responsive design implemented
- ✅ Loading states handled
- ✅ Error states handled
- ✅ Tests written and passing

### Workflow 4: Add Database Model

**Trigger**: When adding a new Django model
**Steps**:

1. Create model with proper field types
2. Add `__str__` method
3. Add Meta class with ordering, indexes
4. Add model validation in `clean()` method
5. Create corresponding serializer
6. Update admin.py with proper configuration
7. Format with ruff
8. Type check with mypy
9. Create and run migrations
10. Write model tests
11. Update API documentation

**Quality Checks**:

- ✅ All fields properly typed
- ✅ Relationships properly defined
- ✅ Indexes on frequently queried fields
- ✅ Validation logic implemented
- ✅ Admin properly configured
- ✅ Tests cover all model methods
- ✅ Migration runs without errors

### Workflow 5: Implement Feature (Full Stack)

**Trigger**: When implementing a complete feature
**Steps**:

1. **Backend**:

   - Create/update models
   - Create migrations
   - Implement serializers
   - Create ViewSet/views
   - Add URL patterns
   - Write comprehensive tests
   - Format and lint code
   - Verify all tests pass

2. **Frontend**:

   - Create TypeScript types matching backend
   - Implement API service methods
   - Create composables if needed
   - Build UI components with DaisyUI
   - Add loading/error states
   - Implement form validation
   - Format and lint code
   - Write component tests
   - Verify all tests pass

3. **Integration**:
   - Test full user flow
   - Check responsive design
   - Verify accessibility
   - Test error scenarios
   - Ensure proper state management

**Quality Checks**:

- ✅ Backend tests passing (80%+ coverage)
- ✅ Frontend tests passing (80%+ coverage)
- ✅ E2E flow works correctly
- ✅ All code formatted and linted
- ✅ Type checking passes
- ✅ No console errors or warnings
- ✅ Responsive on mobile/tablet/desktop
- ✅ Accessible (keyboard navigation, screen readers)

## Code Formatting & Linting

### Before Every Commit

Run these commands automatically:

#### Backend

```bash
# Format code
ruff format backend/

# Fix auto-fixable linting issues
ruff check --fix backend/

# Type check
mypy backend/

# Run tests
pytest backend/ --cov=backend --cov-report=term-missing

# Check coverage threshold
coverage report --fail-under=80
```

#### Frontend

```bash
# Format code
prettier --write "frontend/**/*.{ts,vue,js,json,css}"

# Lint and fix
eslint --fix "frontend/**/*.{ts,vue,js}"

# Type check
nuxi typecheck frontend/

# Run tests
vitest run frontend/

# Check coverage
vitest run --coverage
```

#### Mobile

```bash
# Format code
ktlint -F "mobile/**/*.kt"

# Lint
detekt --config mobile/detekt.yml --input mobile/app/src

# Run tests
./gradlew test

# Check coverage
./gradlew jacocoTestReport
```

## Automated Quality Gates

### Gate 1: Code Formatting

**Must Pass**: All code must be properly formatted

```bash
# Backend
ruff format --check backend/

# Frontend
prettier --check "frontend/**/*.{ts,vue,js,json}"

# Mobile
ktlint "mobile/**/*.kt"
```

### Gate 2: Linting

**Must Pass**: No linting errors allowed

```bash
# Backend
ruff check backend/

# Frontend
eslint "frontend/**/*.{ts,vue,js}"

# Mobile
detekt --config mobile/detekt.yml --input mobile/app/src
```

### Gate 3: Type Checking

**Must Pass**: All code must be properly typed

```bash
# Backend
mypy backend/ --strict

# Frontend
nuxi typecheck frontend/
```

### Gate 4: Tests

**Must Pass**: All tests must pass, 80%+ coverage

```bash
# Backend
pytest backend/ --cov=backend --cov-report=term-missing --cov-fail-under=80

# Frontend
vitest run --coverage

# Mobile
./gradlew test jacocoTestReport
```

### Gate 5: Security

**Must Pass**: No security vulnerabilities

```bash
# Backend
safety check
bandit -r backend/

# Frontend
npm audit

# Mobile
./gradlew dependencyCheckAnalyze
```

## Code Review Checklist

### For Every Code Change

- [ ] Code is formatted with proper tools (ruff/prettier/ktlint)
- [ ] No linting errors
- [ ] All types properly defined (no `any` in TypeScript)
- [ ] Tests written and passing
- [ ] Test coverage >= 80%
- [ ] Documentation updated
- [ ] No console.log statements (use proper logging)
- [ ] Error handling implemented
- [ ] Loading states implemented
- [ ] Accessibility attributes present
- [ ] Responsive design verified
- [ ] Performance optimized
- [ ] Security best practices followed

### For API Changes

- [ ] Backward compatible OR breaking change documented
- [ ] API documentation updated
- [ ] Proper error responses defined
- [ ] Input validation implemented
- [ ] Rate limiting considered
- [ ] Authentication/authorization checked
- [ ] Database queries optimized

### For UI Changes

- [ ] DaisyUI components used consistently
- [ ] Responsive on all screen sizes
- [ ] Keyboard navigation works
- [ ] Screen reader accessible
- [ ] Loading states pleasant
- [ ] Error messages helpful
- [ ] Animations smooth (60fps)
- [ ] Images optimized

## Common Tasks & Commands

### Backend Development

```bash
# Create new app
python backend/manage.py startapp app_name apps/app_name

# Make migrations
python backend/manage.py makemigrations

# Run migrations
python backend/manage.py migrate

# Create superuser
python backend/manage.py createsuperuser

# Run development server
python backend/manage.py runserver

# Run tests
pytest backend/apps/specific_app/

# Format code
ruff format backend/

# Lint code
ruff check --fix backend/

# Type check
mypy backend/
```

### Frontend Development

```bash
# Install dependencies
npm install

# Run dev server
npm run dev

# Build for production
npm run build

# Format code
npm run format

# Lint code
npm run lint

# Type check
npm run typecheck

# Run tests
npm run test

# Run tests in watch mode
npm run test:watch

# Generate component
npx nuxi add component components/ComponentName
```

### Mobile Development

```bash
# Build app
./gradlew assembleDebug

# Run tests
./gradlew test

# Format code
./gradlew ktlintFormat

# Lint code
./gradlew detekt

# Generate coverage report
./gradlew jacocoTestReport
```

## Error Handling Patterns

### Backend Error Handling

```python
from rest_framework.exceptions import ValidationError, NotFound
from rest_framework.response import Response
from rest_framework import status

class MenuItemViewSet(viewsets.ModelViewSet):
    def create(self, request, *args, **kwargs):
        try:
            serializer = self.get_serializer(data=request.data)
            serializer.is_valid(raise_exception=True)
            self.perform_create(serializer)

            return Response(
                {
                    'success': True,
                    'data': serializer.data,
                    'message': 'Menu item created successfully',
                },
                status=status.HTTP_201_CREATED
            )
        except ValidationError as e:
            return Response(
                {
                    'success': False,
                    'error': {
                        'code': 'VALIDATION_ERROR',
                        'message': 'Invalid input data',
                        'details': e.detail,
                    }
                },
                status=status.HTTP_400_BAD_REQUEST
            )
        except Exception as e:
            logger.error(f'Error creating menu item: {str(e)}')
            return Response(
                {
                    'success': False,
                    'error': {
                        'code': 'INTERNAL_ERROR',
                        'message': 'An unexpected error occurred',
                    }
                },
                status=status.HTTP_500_INTERNAL_SERVER_ERROR
            )
```

### Frontend Error Handling

```typescript
// composables/useApi.ts
export const useApi = () => {
  const handleError = (error: any): string => {
    if (error.response) {
      // Server responded with error
      const message =
        error.response.data?.error?.message || "An error occurred";
      return message;
    } else if (error.request) {
      // Request made but no response
      return "Network error. Please check your connection.";
    } else {
      // Something else happened
      return "An unexpected error occurred";
    }
  };

  const fetchData = async <T>(url: string): Promise<T> => {
    try {
      const response = await $fetch<ApiResponse<T>>(url);

      if (!response.success) {
        throw new Error(response.error?.message || "Request failed");
      }

      return response.data;
    } catch (error) {
      const message = handleError(error);
      useToast().error(message);
      throw error;
    }
  };

  return { fetchData };
};
```

## Git Commit Standards

### Commit Message Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Code style (formatting, missing semi colons, etc)
- `refactor`: Code refactoring
- `perf`: Performance improvement
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

### Examples

```bash
feat(menu): add menu item search functionality

Implement full-text search for menu items with category filtering.
Includes backend API endpoint and frontend UI component.

- Add search endpoint to MenuItemViewSet
- Create search composable with debouncing
- Add search input to menu page
- Write tests for search functionality

Closes #123

---

fix(orders): resolve order status update race condition

Fix race condition when multiple staff members update order status simultaneously.
Implement optimistic locking with version field.

Fixes #456

---

refactor(auth): improve JWT token refresh logic

Simplify token refresh flow and add better error handling.
No functional changes.
```

## Pre-Commit Hooks

### Setup Pre-Commit

```bash
# Install pre-commit
pip install pre-commit

# Install hooks
pre-commit install
```

### .pre-commit-config.yaml

```yaml
repos:
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.1.6
    hooks:
      - id: ruff
        args: [--fix]
      - id: ruff-format

  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v1.7.1
    hooks:
      - id: mypy
        additional_dependencies: [django-stubs]

  - repo: https://github.com/pre-commit/mirrors-prettier
    rev: v3.1.0
    hooks:
      - id: prettier
        files: \.(ts|vue|js|json|css|md)$

  - repo: https://github.com/pre-commit/mirrors-eslint
    rev: v8.55.0
    hooks:
      - id: eslint
        files: \.(ts|vue|js)$
        args: [--fix]
```

## Performance Optimization Rules

### Backend Performance

1. **Always use select_related/prefetch_related** for related objects
2. **Add database indexes** on frequently queried fields
3. **Use pagination** for list endpoints (max 100 items per page)
4. **Cache frequently accessed data** in Redis
5. **Use database transactions** for multi-model operations
6. **Optimize N+1 queries** with proper eager loading
7. **Use async views** for I/O-bound operations

### Frontend Performance

1. **Lazy load images** with `@nuxt/image`
2. **Use virtual scrolling** for long lists
3. **Debounce search inputs** (300ms minimum)
4. **Cache API responses** where appropriate
5. **Split code by route** (automatic with Nuxt)
6. **Optimize bundle size** (check regularly)
7. **Use Web Workers** for heavy computations

### Mobile Performance

1. **Implement pagination** for all lists
2. **Cache images** with Coil
3. **Use lazy columns** for scrollable lists
4. **Optimize database queries** with Room
5. **Use coroutines** for async operations
6. **Implement offline-first** architecture
7. **Minimize recompositions** in Compose

## Security Best Practices

### Backend Security

- ✅ Always validate and sanitize user input
- ✅ Use parameterized queries (ORM handles this)
- ✅ Implement rate limiting on all endpoints
- ✅ Use HTTPS only in production
- ✅ Set proper CORS policies
- ✅ Implement CSRF protection
- ✅ Use secure password hashing (Django default)
- ✅ Keep dependencies updated
- ✅ Never log sensitive data
- ✅ Validate file uploads (type, size)

### Frontend Security

- ✅ Never store sensitive data in localStorage
- ✅ Use httpOnly cookies for tokens
- ✅ Sanitize user-generated content
- ✅ Implement CSP headers
- ✅ Validate all form inputs
- ✅ Use secure random for IDs
- ✅ Keep dependencies updated
- ✅ Avoid eval() and innerHTML
- ✅ Implement XSS protection

### Mobile Security

- ✅ Use encrypted SharedPreferences
- ✅ Implement certificate pinning
- ✅ Obfuscate code with R8
- ✅ Validate all API responses
- ✅ Use secure random for tokens
- ✅ Implement root detection
- ✅ Keep dependencies updated
- ✅ Use SafetyNet API

## Agent Decision Tree

### When to Ask for Confirmation

1. Making breaking changes to public APIs
2. Deleting files or large blocks of code
3. Modifying database schemas in production
4. Changing authentication/security logic
5. Installing new major dependencies
6. Modifying deployment configurations
7. Changing environment variables

### When to Proceed Automatically

1. Formatting code
2. Fixing linting issues
3. Adding tests
4. Updating documentation
5. Adding type hints
6. Refactoring without changing behavior
7. Adding error handling

### When to Stop and Report

1. Tests are failing
2. Security vulnerabilities detected
3. Breaking changes without migrations
4. Type checking errors
5. Circular dependencies detected
6. Performance regression detected
7. Coverage drops below 80%

## Troubleshooting Common Issues

### Backend Issues

```bash
# Migration conflicts
python manage.py migrate --fake <app_name> <migration_number>
python manage.py migrate

# Clear all migrations and start fresh (dev only!)
find . -path "*/migrations/*.py" -not -name "__init__.py" -delete
find . -path "*/migrations/*.pyc"  -delete
python manage.py makemigrations
python manage.py migrate

# Django cache issues
python manage.py clear_cache

# Port already in use
lsof -ti:8000 | xargs kill -9
```

### Frontend Issues

```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install

# Clear Nuxt cache
rm -rf .nuxt .output
npm run dev

# Fix TypeScript issues
npm run typecheck

# Port already in use
lsof -ti:3000 | xargs kill -9
```

### Mobile Issues

```bash
# Clean build
./gradlew clean

# Invalidate caches and restart Android Studio

# Clear gradle cache
rm -rf ~/.gradle/caches/

# Reset ADB
adb kill-server
adb start-server
```

## Success Criteria

### Definition of Done

A task is only complete when ALL of the following are true:

- [ ] Code is formatted with proper tools
- [ ] No linting errors
- [ ] All types properly defined
- [ ] Tests written and passing
- [ ] Test coverage >= 80%
- [ ] Documentation updated
- [ ] Code reviewed and approved
- [ ] No security vulnerabilities
- [ ] Performance benchmarks met
- [ ] Accessibility verified
- [ ] Mobile responsive verified
- [ ] Error handling implemented
- [ ] Deployed to staging successfully

---

**Remember**: Quality over speed. It's better to take time to do it right than to rush and create technical debt. Every shortcut taken today becomes tomorrow's bug. 🐛❌

**The JamboBites Standard**: Beautiful, performant, maintainable, and accessible code. Always. ✨
