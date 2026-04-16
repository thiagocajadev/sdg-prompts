# 01 - Folder Structure

## Repository Layout

- Why organize it this way?
- Where does everything go?

## Main Folders

- `/cmd`: Entrypoints.
- `/internal`: Private application code.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 01 - Folder Structure

## Repository Layout

Let's put everything in the root to make it easier to find.

## Main Folders

- `/src`: All code goes here.
```

> **Rationale**: "Everything in the root" fails miserably in projects that scale. A generic `/src` doesn't separate responsibilities.

### ✅ Good Example

```markdown
# SPEC-014: Standard Project Layout

## 1. Context
Organizing the repository to ensure high maintainability and clear separation of concerns as the project scales.

## 2. Success Metrics
* Zero accidental circular dependencies between packages.
* Onboarding speed: A dev can find any logic within 30 seconds.

## 3. Scope & Scenarios
* **Structure:** Adopting Standard Go Project Layout.
* **Mapping:** `/cmd` (Entrypoints), `/internal/domain` (Logic).

## 4. Constraints & Business Rules
* The `/internal` folder must contain all private code.
* Business logic must be technology-agnostic (Domain-driven).

## 5. Out of Scope
* Defining frontend component folder structure (Web focus only).
* Setting up monorepo tooling like Nx or Turborepo.

## 6. Definition of Done
- [ ] Base folder structure created.
- [ ] Initial project boilerplate following layout.
```

> **Rationale**: Follows industry standards (Go Standard Layout) and explicitly separates domain from infrastructure.
