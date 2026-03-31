---
description: Run a full project health check covering code quality, security, accessibility, testing, and documentation completeness
---

# Project Health Check

Perform a comprehensive health check of this project across all organizational standards.

## Code Quality
- Check TypeScript strict mode is enabled
- Verify no use of any type
- Check for proper error handling (no unhandled promise rejections)
- Verify consistent naming conventions
- Check file/folder structure follows standards

## Security
- Run through the security checklist (secrets, auth, input validation, data protection)
- Check dependency security
- Verify environment configuration

## Accessibility
- Check all components for semantic HTML usage
- Verify images have alt attributes
- Check form labels and ARIA attributes
- Verify keyboard navigation support
- Check color contrast considerations

## Testing
- Check test coverage exists for business logic
- Verify API routes have tests
- Check test naming conventions
- Verify no tests depend on external services without mocks

## Documentation
- Check README exists and is helpful for non-developers
- Verify .env.example is complete
- Check that complex functions have comments
- Verify API endpoints are documented

## Output
Produce a health report card with ratings for each category (A through F) and include specific action items to improve each rating, prioritized by impact.
