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
# Stack and Environment: Happy Smile LP

## Local Setup

1. `git clone` followed by `npm ci` (we are using `v18.x` in nvm).
2. Request access to DevSupabase in the slack group.
3. Copy the `.env.example` file to `.env.local` and run `npm run dev` on port 3000.
   **Frontend:** Next.js (Pages Router) + TailwindCSS. Form built with `React Hook Form`.

## Supabase Minimal Entities

To strictly focus on contacts, we have only 1 table managed in the Development Supabase Cloud:

- `leads (id: UUID, name: string, email: string, whatsapp: string, created_at: timestamp)`
```

> **Rationale**: Straight to the point and practical. A second Frontend dev will enter the project, clone it, understand the forms, and run it in less than 10 minutes of reading.
