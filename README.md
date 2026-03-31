# Kiro Guardrails — Organizational Standards for Non-Developer Prototyping

A ready-to-use `.kiro` configuration that turns Kiro into a governed prototyping environment. Designed for organizations that want to empower non-developers (product managers, designers, analysts, business users) to build working prototypes while automatically enforcing security, accessibility, and coding standards.

## The Problem

AI-powered IDEs like Kiro make it possible for anyone to build software by describing what they want in plain language. But without guardrails, this creates risk:

- Hardcoded secrets and API keys committed to repositories
- Insecure authentication patterns or no authentication at all
- Unapproved dependencies with known vulnerabilities
- Inaccessible UIs that exclude users with disabilities
- Code that's impossible for engineering teams to maintain or extend
- No consistency across prototypes built by different people

## The Solution

This configuration uses every layer of Kiro's capability stack to create an invisible safety net:

| Layer | What It Does | Count |
|-------|-------------|-------|
| Steering | Persistent rules Kiro follows for every interaction | 7 files |
| Hooks | Automated checks that run on file events and agent actions | 9 hooks |
| Skills | On-demand workflows invoked via `/` commands or auto-activated | 5 skills |
| Custom Agents | Specialized sub-agents with tailored personas and expertise | 4 agents |

The result: non-developers describe what they want, Kiro builds it, and the guardrails ensure the output meets organizational standards — without the user needing to know what those standards are.

## Quick Start

### Option 1: Add to an existing project

Copy the `.kiro` folder into your project root:

```
your-project/
  .kiro/
    hooks/
    skills/
    steering/
  src/
  package.json
  ...
```

### Option 2: Clone this repo as a template

```bash
git clone <this-repo-url> my-prototype
cd my-prototype
```

### After installation

1. Open the project in Kiro
2. Steering files activate immediately — Kiro will follow the standards in every conversation
3. Restart Kiro once to activate all hooks
4. Skills are available via `/` commands in chat or activate automatically based on context

## What's Included

### Steering Files (`.kiro/steering/`)

Steering files give Kiro persistent knowledge about your organization's standards. They're loaded into every conversation automatically, so the user never needs to remember or reference them.

| File | Purpose | Inclusion |
|------|---------|-----------|
| `project-context.md` | Explains who this is for and how to get started | Always |
| `security-standards.md` | OWASP Top 10 based security rules, secrets management, auth patterns | Always |
| `ui-framework-standards.md` | Approved UI stack, component patterns, accessibility requirements | Always |
| `backend-standards.md` | API design, database patterns, error handling, environment config | Always |
| `coding-standards.md` | TypeScript standards, naming conventions, file structure, git practices | Always |
| `testing-standards.md` | Testing tools, coverage expectations, test file conventions | Always |
| `infrastructure-standards.md` | AWS CDK, deployment safety, cost awareness | File match (infra files only) |

### Hooks (`.kiro/hooks/`)

Hooks run automatically when events happen in the IDE. Users don't need to trigger them — they fire in the background and fix issues or flag problems.

| Hook | Trigger | What It Does |
|------|---------|-------------|
| `security-scan-new` | File created | Scans new files for hardcoded secrets, API keys, credentials |
| `security-scan-edit` | File edited | Checks edited files for security regressions |
| `write-guard` | Before any write | Validates content against standards before Kiro writes a file |
| `api-route-guard` | API file created | Ensures auth middleware, input validation, error handling |
| `accessibility-check` | Component created | Checks semantic HTML, ARIA attributes, keyboard navigation |
| `dependency-guard` | package.json edited | Flags unapproved packages and unpinned versions |
| `env-file-guard` | .env file created | Prevents real secrets, ensures .gitignore coverage |
| `database-schema-guard` | Schema edited | Validates soft deletes, indexes, timestamps, encryption |
| `change-summary` | Agent stops | Generates a plain-language summary of what changed |

### Skills (`.kiro/skills/`)

Skills are on-demand workflows that users can invoke via `/` slash commands in chat, or that Kiro activates automatically when the context matches.

| Skill | What It Does |
|-------|-------------|
| `/scaffold-feature` | Builds a new feature end-to-end: data model, API, UI, tests — all following standards |
| `/security-review` | Full OWASP-based security audit with severity ratings and fix recommendations |
| `/project-health-check` | Report card across code quality, security, accessibility, testing, documentation |
| `/handoff-package` | Generates a complete engineering handoff document for prototype-to-production transition |
| `/explain-codebase` | Creates a plain-language guide to the codebase for non-technical stakeholders |

### Custom Agents (`.kiro/agents/`)

Custom agents are specialized sub-agents with tailored personas, expertise, and communication styles. Kiro automatically selects the right agent based on what the user is asking, or users can invoke them explicitly.

| Agent | When It Activates | What It Does |
|-------|-------------------|-------------|
| `prototype-builder` | User describes a feature to build, asks for a page/form/dashboard | Translates plain-language requests into standards-compliant code with friendly explanations |
| `code-reviewer` | User asks for code review or quality check | Systematic review against all org standards with A-F ratings per category |
| `security-auditor` | User asks about security, vulnerabilities, or auth | File-by-file OWASP-based security audit with severity ratings and plain-language fixes |
| `onboarding-guide` | User is new, confused, or asks for help getting started | Patient walkthrough of Kiro, the workspace, and how to build their first prototype |

These agents are designed with non-developer users in mind — they explain everything in plain language, use analogies, and never assume technical knowledge.

## How It Works — The Four Layers

### Layer 1: Steering (Passive Guidance)

Steering files are markdown documents in `.kiro/steering/` that Kiro reads before every interaction. They act like a persistent system prompt that encodes your organization's standards. The user never sees them, but Kiro always follows them.

For example, when a user says "build me a login page", Kiro will automatically:
- Use NextAuth.js (not a custom auth implementation)
- Hash passwords with bcrypt (12+ rounds)
- Validate inputs with Zod
- Use shadcn/ui components with proper accessibility
- Store secrets in environment variables

The user didn't need to ask for any of this — the steering files made it happen.

### Layer 2: Hooks (Active Enforcement)

Hooks are automated checks that trigger on IDE events. They catch issues that might slip through steering — either because the user manually edited a file, or because the AI made a mistake.

The hook system operates at three levels:
- **Pre-write guard**: Checks content BEFORE Kiro writes it (catches issues at the source)
- **Post-creation checks**: Scans files after creation for security, accessibility, and standards compliance
- **Post-edit checks**: Re-scans files after edits to catch regressions

If a hook finds an issue, it either fixes it automatically or flags it for the user in plain language.

### Layer 3: Skills (On-Demand Workflows)

Skills are structured workflows that users can invoke when they need them. They're particularly useful for:
- Non-developers who want to run a security check before sharing their prototype
- Product managers preparing a handoff to engineering
- Anyone who wants to understand what the codebase does without reading code

## Customizing for Your Organization

### Changing the approved tech stack

Edit the steering files to match your organization's approved technologies:
- `ui-framework-standards.md` — Change the approved UI framework, component library, etc.
- `backend-standards.md` — Change the approved backend runtime, database, ORM, etc.
- `security-standards.md` — Add organization-specific security requirements

### Adding approved packages to the dependency guard

Edit the `dependency-guard` hook file in `.kiro/hooks/` and update the approved packages list in the prompt.

### Adding new hooks

Use the Kiro IDE hook UI (Command Palette > "Open Kiro Hook UI") or create `.kiro.hook` files directly in `.kiro/hooks/`.

### Adding conditional steering

For standards that only apply to certain file types, use the `fileMatch` inclusion mode:

```markdown
---
inclusion: fileMatch
fileMatchPattern: "**/*.test.ts"
---

# Test-Specific Standards
...
```

### Adding manual steering

For standards that users opt into via `#` context in chat:

```markdown
---
inclusion: manual
---

# Advanced Deployment Guide
...
```

## Architecture Decisions

### Why steering over a single rules file?

Splitting standards across multiple focused steering files means:
- Each file stays small and focused (better for AI context windows)
- Teams can customize individual areas without touching others
- Conditional inclusion (like infrastructure standards) reduces noise for non-infra work

### Why pre-write hooks?

The `write-guard` hook catches issues before they hit the filesystem. This is more effective than post-write scanning because:
- Issues are caught at the source, not after the fact
- The agent can fix problems in the same operation
- Users never see non-compliant code in their files

### Why skills for health checks?

Skills give non-developers a simple way to validate their work without understanding what "security review" or "accessibility audit" means technically. They just type `/security-review` and get a plain-language report.

### Layer 4: Custom Agents (Specialized Personas)

Custom agents bring specialized expertise and communication styles to different tasks. Unlike steering (which applies to all interactions) or hooks (which trigger on events), agents are selected based on what the user is trying to do.

The key design choice: every agent is built for non-developer users. The prototype-builder explains what it's building in plain language. The security-auditor reports findings with severity levels and simple explanations. The onboarding-guide never assumes technical knowledge.

Kiro selects the right agent automatically based on the user's request, but users can also switch agents explicitly if they want a specific perspective (e.g., switching to the security-auditor before sharing a prototype).

## FAQ

**Q: Will this slow down Kiro?**
A: Steering files add minimal overhead — they're just context. Hooks add a small check on file events, but the trade-off for automated compliance is worth it. The pre-write guard adds one validation step before each file write.

**Q: Can users override the guardrails?**
A: Steering files are guidance, not hard blocks — a determined user could ask Kiro to ignore them. The hooks provide harder enforcement since they trigger automatically. For maximum control, use Kiro's enterprise features to lock down configurations.

**Q: What if my org uses Vue/Angular instead of React?**
A: Edit `ui-framework-standards.md` to replace the React-specific guidance with your framework. The security, backend, and coding standards are largely framework-agnostic.

**Q: How do I add new approved packages?**
A: Update the approved list in both `ui-framework-standards.md` (or `backend-standards.md`) and the `dependency-guard` hook prompt.

**Q: Can I use this with Kiro CLI too?**
A: The steering files and skills work with both Kiro IDE and CLI. Hooks are IDE-specific. For CLI, you'd use the equivalent CLI hook configuration.

## Contributing

1. Fork this repository
2. Make your changes to the `.kiro` configuration
3. Test by opening a project with the configuration in Kiro
4. Verify hooks trigger correctly and steering guidance is followed
5. Submit a pull request with a description of what you changed and why

## License

MIT — use this however you like. Customize it for your organization and share it with your teams.
