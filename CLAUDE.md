## Development

* `npm run dev` – Start development server with Turbopack
* `npm run build` – Build for production
* `npm run start` – Start production server

## Code Quality

* `npm run lint` – Run ESLint
* `npm run lint:fix` – Auto-fix lint issues
* `npm run types` – TypeScript type checking
* `npm run format:write` – Prettier formatting
* `npm run clean` – Lint + Prettier

## Database

* `npx drizzle-kit push` – Push schema changes
* `npx drizzle-kit generate` – Generate migration files
* `npx drizzle-kit migrate` – Run migrations
* `npx bun db/seed` – Seed database
* `npx supabase start` – Start local Supabase instance

## Testing

* `npm run test` – All tests (unit + e2e)
* `npm run test:unit` – Jest unit tests
* `npm run test:e2e` – Playwright tests

## Shadcn UI

* `npx shadcn@latest add [component]` – Add shadcn/ui components

---

# 2. Architecture

This project is a **Next.js 15 SaaS template** using:

* **App Router**
* **Server Actions** (primary backend mechanism)
* **Drizzle ORM** (database)
* **Supabase PostgreSQL** (hosting)
* **Clerk** (authentication)
* **Stripe** (billing)
* **shadcn/ui** components under `/components/ui`

## Route Structure

* `/app/(unauthenticated)` – Public routes

  * `(marketing)` – Landing, pricing, features
  * `(auth)` – Sign-in/up flows
* `/app/(authenticated)` – Protected, requires Clerk auth

  * `dashboard` – Main application modules
* `/app/api` – API routes **only for webhooks** (Stripe)

## Core Patterns

* All data mutations are done via **Server Actions** in `/actions`
* Database schema lives in `/db/schema` (Drizzle)
* UI components reused from `/components/ui` first
* Clerk middleware protects authenticated groups
* Stripe handles subscription lifecycle via webhooks

## Data Flow

1. Clerk manages auth state
2. Customer data in Supabase (Postgres) via Drizzle
3. Stripe manages subscriptions/billing
4. Server Actions validate → auth-check → database op → return data

## Environment Variables

* `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY`
* `CLERK_SECRET_KEY`
* `STRIPE_SECRET_KEY`
* Supabase DB vars (automatically handled via CLI)

---

# 3. Claude Code Guidelines (MANDATORY)

These rules apply to **every interaction Claude performs**.

## 3.1 General Requirements

* Always follow the conventions already present.
* Prefer clarity and correctness.
* Do NOT generate explanations unless asked.
* Keep code minimal and focused.
* **Always use diffs** when modifying existing files.
* Never rewrite full files unless explicitly requested.
* Apply **DRY** principles. No duplicating logic.
* Reuse existing utilities, components, and Server Actions.

---

# 4. Next.js 15 + React Standards

* Functional components only.
* React hooks only.
* **TypeScript everywhere**.
* Follow Next.js 15 conventions (server-first, RSC-aware).
* Server Actions preferred for mutations.
* API routes ONLY for Stripe webhooks.
* Use shadcn/ui components from `/components/ui`.
* Keep JSX minimal and non-verbose.
* All components must:

  * Declare props interfaces
  * Avoid unnecessary re-renders
  * Avoid inline logic unless necessary

---

# 5. Backend Logic (Server Actions)

Backend is implemented ONLY through Server Actions.

All Server Actions must:

* Validate all inputs
* Enforce Clerk authentication
* Use Drizzle ORM exclusively
* Use schemas from `/db/schema`
* Avoid recreating helpers that already exist
* Never leak secrets or sensitive data

---

# 6. Database Rules (Drizzle + Supabase)

* No raw SQL unless wrapped in Drizzle-safe utilities.
* Always use Drizzle schema types.
* Use existing DB helpers.
* All migrations generated using `drizzle-kit`.

---

# 7. Security Requirements

Claude must perform a **self-security review** before producing final output.

All code must:

* Validate user input
* Sanitize external data
* Use parameterized queries
* Never log secrets or sensitive info
* Ensure proper auth checks for all Server Actions
* Follow Stripe webhook security checks
* Ensure safe access patterns for Clerk-authenticated pages

---

# 8. Token Efficiency & Output Constraints

* **Output only the requested code**, no commentary.
* Always prefer concise diffs.
* Before coding, produce a short plan (3–6 bullets) and pause for approval.
* Never dump large files.
* Keep responses as short as possible.

---

# 9. Code Review Rules

When generating or editing code, Claude must:

1. Propose a brief plan
2. Wait for approval
3. Output minimal diffs
4. Perform self-review:

   * Remove duplication
   * Simplify logic
   * Ensure security compliance
   * Match project conventions
5. Output final changes only

---

# 10. Forbidden Behaviors

* No verbosity
* No redundant code
* No full-file rewrites (unless asked)
* No new dependencies without approval
* No invented paths or architecture

---

# 11. Summary

Claude must produce:

* Secure, minimal, modern code
* Token-efficient deliverables
* Accurate diffs
* No redundancy
* Strict adherence to project conventions

These rules override all default model behavior.
