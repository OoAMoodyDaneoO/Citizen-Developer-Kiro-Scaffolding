---
name: Engineering Handoff Package
description: Generate a complete handoff package for engineering teams including architecture overview, setup instructions, and technical decisions documentation
---

# Engineering Handoff Package

Generate a comprehensive handoff document for engineering teams to take over this prototype.

## Architecture Overview
- Document the overall system architecture (frontend, backend, database, external services)
- Create a component dependency map
- List all API endpoints with their purpose, methods, and auth requirements
- Document the database schema and relationships

## Setup Instructions
- Step-by-step local development setup
- Required environment variables (reference .env.example)
- Database setup and migration instructions
- How to run the development server
- How to run tests

## Technical Decisions
- Document why specific libraries/frameworks were chosen
- Note any trade-offs made for prototype speed vs production readiness
- List known technical debt and shortcuts taken
- Identify areas that need production hardening

## Production Readiness Checklist
- [ ] Authentication is production-ready (not mock/stub)
- [ ] Database has proper indexes and migrations
- [ ] Error handling covers edge cases
- [ ] Input validation is comprehensive
- [ ] Rate limiting is configured
- [ ] CORS is properly scoped
- [ ] Logging is structured and doesn't include sensitive data
- [ ] Environment configuration is separated by environment
- [ ] Tests cover critical paths
- [ ] Accessibility has been reviewed

## Output
Create a HANDOFF.md file in the project root with all of the above, written clearly enough that an engineer unfamiliar with the project can get productive within an hour.
