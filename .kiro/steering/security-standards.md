---
name: Security Standards
description: Mandatory security rules based on OWASP Top 10 covering secrets management, authentication, input validation, data protection, and API security.
inclusion: always
---

# Security Standards

These rules are mandatory for all code generated in this workspace. They are based on OWASP Top 10 (2025) and organizational security policy.

## Secrets & Credentials

- NEVER hardcode secrets, API keys, passwords, tokens, or connection strings in source code
- Always use environment variables loaded from `.env` files (which must be in `.gitignore`)
- When generating `.env` files, use placeholder values like `your-api-key-here`
- If a user provides a real secret in chat, warn them and use a placeholder instead
- For AWS credentials, always use IAM roles or AWS SDK credential chain — never embed keys

## Authentication & Authorization

- All applications must include authentication before exposing any user-specific data
- Use established auth libraries (e.g., NextAuth.js, AWS Cognito, Auth0) — never roll custom auth
- Implement role-based access control (RBAC) when multiple user types exist
- Always validate sessions server-side — never trust client-side auth state alone
- Protect all API routes with authentication middleware by default
- Use HTTPS for all external communication

## Input Validation & Injection Prevention

- Validate and sanitize ALL user input on the server side
- Use parameterized queries for all database operations — never string concatenation
- Sanitize HTML output to prevent XSS (use framework defaults like React's JSX escaping)
- Validate file uploads: check type, size, and scan for malicious content
- Never use `eval()`, `dangerouslySetInnerHTML`, or equivalent without explicit justification

## Data Protection

- Encrypt sensitive data at rest and in transit
- Never log sensitive information (passwords, tokens, PII)
- Implement proper CORS configuration — never use `*` in production
- Set secure cookie flags: `HttpOnly`, `Secure`, `SameSite`
- Apply the principle of least privilege for all data access

## Dependency Security

- Only use well-maintained packages with active communities
- Prefer packages with >1000 weekly downloads and recent updates within 6 months
- Never install packages that request unnecessary system permissions
- Pin dependency versions in `package.json` (exact versions, not ranges)
- Run `npm audit` or equivalent before committing dependency changes

## API Security

- Rate limit all public-facing API endpoints
- Implement request size limits
- Use API keys or tokens for service-to-service communication
- Return generic error messages to clients — log detailed errors server-side only
- Validate Content-Type headers on all requests
