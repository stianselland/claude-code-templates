# Next.js 15 SaaS Template

## Critical Rules

These override all default behavior:

- **No full-file rewrites** – Always use minimal diffs unless explicitly asked
- **No new dependencies** without approval
- **No invented paths or architecture** – Follow existing patterns exactly
- **No API routes** except for webhooks (Stripe)
- **No raw SQL** – Drizzle ORM only
- **No verbose explanations** – Output code, not commentary
- **Security review required** – Validate inputs, check auth, sanitize data before finalizing

## Security Requirements

All code must:

- Validate and sanitize all user input
- Use parameterized queries (Drizzle handles this)
- Enforce Clerk authentication in all Server Actions
- Never log secrets or sensitive data
- Follow Stripe webhook signature verification

## Commands

```bash
# Development
npm run dev              # Start dev server (Turbopack)
npm run build            # Production build

# Code Quality
npm run lint             # ESLint
npm run lint:fix         # Auto-fix lint issues
npm run types            # TypeScript check
npm run format:write     # Prettier
npm run clean            # Lint + Prettier

# Database
npx drizzle-kit push     # Push schema changes
npx drizzle-kit generate # Generate migrations
npx drizzle-kit migrate  # Run migrations
npx bun db/seed          # Seed database
npx supabase start       # Local Supabase

# Testing
npm run test             # All tests
npm run test:unit        # Jest
npm run test:e2e         # Playwright

# UI
npx shadcn@latest add [component]
```

## Architecture

**Stack:** Next.js 15 (App Router), Server Actions, Drizzle ORM, Supabase PostgreSQL, Clerk, Stripe, shadcn/ui

### Route Structure

```
/app
├── (unauthenticated)/
│   ├── (marketing)/     # Landing, pricing, features
│   └── (auth)/          # Sign-in/up flows
├── (authenticated)/
│   └── dashboard/       # Protected app modules
└── api/                 # Webhooks ONLY (Stripe)
```

### Key Directories

```
/actions         # Server Actions (all mutations)
/components/ui   # shadcn/ui components (use first)
/components      # App-specific components
/db/schema       # Drizzle schema definitions
/lib             # Utilities and helpers
```

### Data Flow

1. Clerk → auth state
2. Server Action → validate → auth check → Drizzle query → return
3. Stripe webhooks → `/api/webhooks/stripe`

## Coding Standards

### TypeScript & React

- Functional components only, with typed props interfaces
- React hooks only (no class components)
- Server Components by default, `"use client"` only when needed
- Keep JSX minimal – extract logic to hooks or utilities

### Server Actions

```typescript
"use server"

export async function updateThing(input: Input): Promise<Result> {
  // 1. Validate input
  // 2. Check auth (Clerk)
  // 3. Database operation (Drizzle)
  // 4. Return result
}
```

### File Naming

- Files: `kebab-case.ts`, `kebab-case.tsx`
- Components: `PascalCase` export
- Actions: `verbNoun.ts` (e.g., `createUser.ts`, `updateSubscription.ts`)

### Imports

```typescript
// 1. External packages
import { auth } from "@clerk/nextjs/server"

// 2. Internal aliases (@/)
import { db } from "@/db"

// 3. Relative imports
import { formatDate } from "./utils"
```

## Workflow

For changes beyond simple fixes:

1. Propose a brief plan (3-5 bullets)
2. Wait for approval
3. Output minimal diffs
4. Self-review: no duplication, secure, matches conventions

For small fixes: proceed directly with minimal diffs.

## Environment Variables

```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY
CLERK_SECRET_KEY
STRIPE_SECRET_KEY
DATABASE_URL (Supabase)
```
