# CLAUDE.md Setup Prompt

Use this prompt when setting up CLAUDE.md for an existing project.

---

## Workflow

1. Replace `CLAUDE.md ` in your project with the content in `base-claude.md`
2. Open Claude Code in the project directory
3. Paste the prompt below
4. Review Claude's output and verify accuracy
5. Ask Claude to make corrections if needed
6. Commit the CLAUDE.md file

---

## Prompt

```
I need you to analyze this codebase and update CLAUDE.md to accurately reflect the project's structure, conventions, and patterns.

## Instructions

### 1. Commands
Scan for command definitions in:
- package.json (scripts)
- pyproject.toml / setup.py
- Makefile
- README.md

Extract and categorize: dev, build, lint, format, test, database commands.

### 2. Architecture
Identify:
- Primary framework and version
- Directory structure (focus on src/, app/, lib/, components/, etc.)
- Key architectural patterns (MVC, component-based, serverless, etc.)
- Data flow (how data moves through the app)

### 3. Coding Conventions
Analyze existing code to detect:
- File naming conventions (kebab-case, snake_case, PascalCase)
- Function/variable naming style
- Import organization pattern
- Export style (named vs default)
- Error handling patterns
- Type usage (TypeScript, Python type hints, etc.)

### 4. Tech Stack
List all major dependencies:
- Framework (Next.js, FastAPI, Express, SvelteKit, etc.)
- Database/ORM (Drizzle, Prisma, SQLAlchemy, etc.)
- Auth (Clerk, Auth.js, custom, etc.)
- UI library (shadcn, Material, Tailwind, etc.)
- Testing (Jest, Pytest, Playwright, etc.)

### 5. Security Patterns
Identify existing security measures:
- Input validation approach
- Auth middleware/decorators
- API protection patterns
- Environment variable usage

### 6. Project-Specific Rules
Look for any existing:
- .eslintrc / eslint.config.js
- .prettierrc
- tsconfig.json strictness
- Custom lint rules or patterns

## Output

Update CLAUDE.md with your findings. Keep the Critical Rules section as-is, but fill in all placeholder sections with accurate project-specific information.

After updating, list any assumptions you made that I should verify.
```

---

## Post-Setup Checklist

After Claude generates the CLAUDE.md, verify:

- [ ] Commands are correct and runnable
- [ ] Directory structure matches actual project
- [ ] Stack list is complete and versions are correct
- [ ] Coding conventions match what the team actually uses
- [ ] No incorrect assumptions about patterns
- [ ] Security requirements are appropriate for this project

---

## Notes

- If the project has unusual patterns, add them to the Critical Rules section
- Remove any sections that don't apply (e.g., Database section for frontend-only projects)
- Add project-specific forbidden behaviors if needed
