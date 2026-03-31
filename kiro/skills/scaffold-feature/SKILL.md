---
description: Scaffold a new feature with all the right patterns - component, API route, database model, types, and tests following organizational standards
---

# Scaffold a New Feature

When asked to build a new feature, follow this structured approach to ensure all organizational standards are met from the start.

## Step 1 - Understand the Requirement
- Ask clarifying questions if the requirement is vague
- Identify: what data is involved, who can access it, what actions can users take
- Determine if this needs: a UI component, an API route, a database model, or all three

## Step 2 - Create the Data Model
- Define TypeScript interfaces in src/types/
- If a database is involved, update the Prisma schema with proper fields (including createdAt, updatedAt, deletedAt for soft deletes)
- Generate and run the migration

## Step 3 - Build the API Layer
- Create API route handlers with authentication middleware
- Add Zod validation schemas for request/response
- Implement proper error handling with the standard response envelope
- Add parameterized database queries

## Step 4 - Build the UI
- Create React components using shadcn/ui or Radix primitives
- Use TypeScript interfaces for all props
- Include semantic HTML and accessibility attributes
- Add form validation with React Hook Form and Zod
- Handle loading, error, and empty states

## Step 5 - Add Tests
- Write unit tests for business logic and utilities
- Write integration tests for API routes
- Use descriptive test names following the testing standards

## Step 6 - Verify
- Run the project health check skill to validate everything meets standards
- Ensure no hardcoded secrets or unapproved dependencies were introduced
