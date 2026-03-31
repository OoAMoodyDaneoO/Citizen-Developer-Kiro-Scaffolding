---
inclusion: always
---

# Testing Standards

## When To Write Tests

- Tests should be written for all business logic and utility functions
- API route handlers should have integration tests
- Critical user flows should have end-to-end tests
- Tests are NOT required for simple presentational components with no logic

## Approved Testing Tools

- **Unit/Integration**: Vitest (preferred) or Jest
- **Component Testing**: React Testing Library
- **E2E Testing**: Playwright (preferred) or Cypress
- **API Testing**: Supertest with Vitest

## Testing Principles

- Test behavior, not implementation — test what the user sees and does
- Use descriptive test names: `it('should display error when email is invalid')`
- Arrange-Act-Assert pattern for all tests
- Don't test framework internals — trust React, Next.js, etc.
- Mock external dependencies (APIs, databases) — don't make real network calls in unit tests
- Keep tests independent — no test should depend on another test's state

## Minimum Coverage Expectations

- Utility functions: 90%+ coverage
- API routes: 80%+ coverage
- Business logic: 80%+ coverage
- Overall project: aim for 70%+ as a baseline

## Test File Conventions

- Test files live next to the code they test
- Name pattern: `[filename].test.ts` or `[filename].test.tsx`
- E2E tests live in a top-level `e2e/` directory
- Use `describe` blocks to group related tests
- Run tests with `--run` flag for single execution (not watch mode)
