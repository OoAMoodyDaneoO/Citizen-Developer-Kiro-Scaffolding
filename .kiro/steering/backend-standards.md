---
inclusion: always
---

# Backend & API Standards

## Approved Backend Stack

- **Runtime**: Node.js 20+ with TypeScript
- **API Framework**: Next.js API Routes (preferred), Express.js, or AWS Lambda
- **Database**: PostgreSQL (preferred), DynamoDB, or SQLite for prototypes
- **ORM**: Prisma (preferred) or DynamoDB DocumentClient
- **Validation**: Zod for request/response validation
- **Authentication**: NextAuth.js, AWS Cognito, or Auth0

## API Design

- Use RESTful conventions with consistent URL patterns
- Use proper HTTP methods: GET (read), POST (create), PUT (update), DELETE (remove)
- Return appropriate HTTP status codes (200, 201, 400, 401, 403, 404, 500)
- All API responses must follow a consistent envelope format:

```json
{
  "success": true,
  "data": {},
  "error": null
}
```

- Implement pagination for list endpoints (limit/offset or cursor-based)
- Version APIs when breaking changes are needed (`/api/v1/...`)

## Error Handling

- Never expose stack traces or internal error details to clients
- Log errors with context (request ID, user ID, timestamp) server-side
- Use structured error responses with error codes clients can programmatically handle
- Implement global error handling middleware — don't rely on try/catch in every route
- Handle async errors properly — no unhandled promise rejections

## Database Patterns

- Always use migrations for schema changes — never modify databases directly
- Use transactions for operations that modify multiple records
- Index frequently queried columns
- Implement soft deletes for user data (add `deletedAt` column)
- Never store passwords in plain text — use bcrypt with minimum 12 rounds
- Sanitize all query inputs — use parameterized queries exclusively

## Environment Configuration

- Use `.env` files for local development (always in `.gitignore`)
- Use `.env.example` with placeholder values committed to the repo
- Validate all environment variables at application startup
- Separate configuration by environment: development, staging, production
- Never commit environment-specific configuration to source control
