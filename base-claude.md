# Project Name

## Critical Rules

These override all default behavior:

- **No full-file rewrites** – Always use minimal diffs unless explicitly asked
- **No new dependencies** without approval
- **No invented paths or architecture** – Follow existing patterns exactly
- **No duplicate code** – Reuse existing utilities, helpers, and components
- **No verbose code** – Keep implementations minimal and focused; no over-engineering
- **No verbose explanations** – Output code, not commentary
- **Follow language best practices** – Use idiomatic patterns for the language/framework
- **Security review required** – Validate inputs, check auth, sanitize data before finalizing

## Security Requirements

All code must:

- Validate and sanitize all user input
- Use parameterized queries for database operations
- Enforce authentication checks before sensitive operations
- Never log secrets, tokens, or sensitive data
- Never commit secrets to version control

## Commands

```bash
# Development
# [Add project-specific dev command]

# Build
# [Add project-specific build command]

# Code Quality
# [Add lint, format, type-check commands]

# Testing
# [Add test commands]
```

## Architecture

**Stack:** [List primary technologies]

### Directory Structure

```
# [Add project-specific directory tree]
```

### Key Patterns

- [Describe primary architectural pattern]
- [Describe data flow]
- [Describe state management approach]

## Coding Standards

### General

- Use static typing where available
- Prefer composition over inheritance
- Keep functions small and single-purpose
- Use meaningful variable and function names

### File Naming

- Use consistent naming conventions per language
- Classes/Components: `PascalCase`
- Keep names descriptive and concise

### Imports

- Group imports logically (external → internal → relative)
- Remove unused imports

### Error Handling

- Handle errors at appropriate boundaries
- Return structured results where appropriate
- Never swallow errors silently

## Workflow

For changes beyond simple fixes:

1. Propose a brief plan (3-5 bullets)
2. Wait for approval
3. Output minimal diffs
4. Self-review: no duplication, secure, matches conventions

For small fixes: proceed directly with minimal diffs.

## Environment Variables

```
# [List required environment variables]
```
