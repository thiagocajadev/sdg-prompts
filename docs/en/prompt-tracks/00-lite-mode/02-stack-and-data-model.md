# 02 - Technical Stack and Essential Data

In fast-paced projects, you should not waste time justifying complex ADRs. Use whatever allows you to deliver quickly and document here only how the next programmer can run the code.

## Main Technologies

- Frontend Framework / SSR: (Ex: Next.js, Vite + React).
- Styling: (Ex: TailwindCSS V3, Radix UI).
- CMS / Backend-As-A-Service (If applicable): (Ex: Supabase, Strapi, Sanity).

## How to Run the Project (Developer Experience - DX)

1. Install package `X`.
2. Include `.env` (where to get a development one?).
3. Run `npm run dev`.

## Minimum Viable Data Model (DB Schema)

- If there's a database, paste only a minimalist Schema or text describing the essential collections so developers don't have to "fish blindfolded".
- If there's a _Headless_ CMS behind it, map the most critical _Types_.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Stack

Using React. To turn it on run npm start.
The database has a `leads` table.
```

> **Rationale**: Omits dozens of secret libraries. A junior dev clones it, runs npm start, and the screen blinks white because they didn't set the Supabase `.env` and didn't even know you used Vercel.

### ✅ Good Example

```markdown
# SPEC-006: Lite Stack & DX Setup

## 1. Context
Standardizing the local environment and technical stack for the Happy Smile Clinic project to ensure fast onboarding.

## 2. Success Metrics
* Onboarding time for new developers under 15 minutes.
* 100% environment parity between local and production (Vercel).

## 3. Scope & Scenarios
* **Scenario A:** New developer clones repo, sets up `.env`, and runs the project.
* **Stack:** Next.js (Pages Router) + TailwindCSS + Supabase.

## 4. Constraints & Business Rules
* Use Node.js `v18.x`.
* Forms must be implemented using `React Hook Form`.
* Database table: `leads (id, name, email, whatsapp, created_at)`.

## 5. Out of Scope
* Setting up CI/CD pipelines (handled by Vercel auto-deploy).
* Provisioning production database instances (manual setup only).

## 6. Definition of Done
- [ ] `.env.example` file updated.
- [ ] `leads` table schema documented.
- [ ] `npm run dev` verified on port 3000.
```

> **Rationale**: Straight to the point and practical. A second Frontend dev will enter the project, clone it, understand the forms, and run it in less than 10 minutes of reading.
