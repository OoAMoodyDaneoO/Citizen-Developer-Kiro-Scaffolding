---
description: Run a comprehensive security review of the entire project against OWASP Top 10 and organizational security standards
---

# Security Review

Perform a thorough security audit of this project. Check every file systematically.

## Secrets and Credentials
- Scan all source files for hardcoded secrets, API keys, passwords, tokens, connection strings
- Verify .env files are in .gitignore
- Check that .env.example exists with placeholder values
- Ensure no secrets appear in commit history

## Authentication and Authorization
- Verify all API routes have authentication middleware
- Check that session validation happens server-side
- Ensure RBAC is implemented if multiple user roles exist
- Verify password hashing uses bcrypt with 12+ rounds

## Input Validation
- Check all user inputs are validated server-side with Zod or equivalent
- Verify database queries use parameterized queries (no string concatenation)
- Check for XSS vulnerabilities (unescaped output)
- Verify file upload validation if applicable

## Data Protection
- Check CORS configuration (no wildcard in production config)
- Verify cookie flags (HttpOnly, Secure, SameSite)
- Check that sensitive data is not logged
- Verify HTTPS is enforced for external communication

## Dependencies
- Check for pinned versions in package.json
- Flag any unapproved packages
- Note any packages with known vulnerabilities

## Output
Produce a security report with severity ratings (Critical, High, Medium, Low), specific file and line references, recommended fixes, and an overall security posture rating.
