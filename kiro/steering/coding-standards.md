---
name: Coding Standards & Quality
description: General coding principles, TypeScript standards, file/folder structure, naming conventions, and git practices for readable, maintainable code.
inclusion: always
---

# Coding Standards & Quality

## General Principles

- Write code that is readable by non-developers — use descriptive variable and function names
- Prefer clarity over cleverness — no one-liners that require 5 minutes to understand
- Keep functions small and focused — one function, one responsibility
- Add comments explaining WHY, not WHAT — the code should explain what it does
- Every file should have a brief comment at the top explaining its purpose

## TypeScript Standards

- Enable `strict` mode in `tsconfig.json` — no exceptions
- Define interfaces for all data shapes — props, API responses, database models
- Use `enum` or union types for fixed sets of values
- Prefer `const` over `let` — never use `var`
- Use async/await over raw Promises — easier to read and debug
- Export types alongside their implementations

## File & Folder Structure

```
src/
  components/     # Reusable UI components
  pages/          # Page-level components / routes
  lib/            # Shared utilities and helpers
  hooks/          # Custom React hooks
  types/          # TypeScript type definitions
  api/            # API route handlers
  styles/         # Global styles and Tailwind config
```

- One component per file — name the file the same as the component
- Co-locate tests next to the code they test (`Button.tsx` → `Button.test.tsx`)
- Group related files by feature when the project grows large

## Naming Conventions

- Components: PascalCase (`UserProfile.tsx`)
- Functions and variables: camelCase (`getUserById`)
- Constants: UPPER_SNAKE_CASE (`MAX_RETRY_COUNT`)
- Types and interfaces: PascalCase with descriptive names (`UserProfileProps`)
- Files: Match the primary export name
- Boolean variables: prefix with `is`, `has`, `should` (`isLoading`, `hasError`)

## Git & Version Control

- Write meaningful commit messages: `feat: add user login page` not `update stuff`
- Follow conventional commits: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`
- Keep commits small and focused — one logical change per commit
- Never commit `.env` files, `node_modules`, or build artifacts
- Always include a `.gitignore` appropriate for the tech stack
