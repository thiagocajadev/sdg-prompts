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
# 01 - Folder Structure

## Repository Layout

We've adopted the `Standard Go Project Layout` to separate entrypoints from internal logic.

## Main Folders

- `/cmd`: Application binaries.
- `/internal/domain`: Entities and business logic.
- `/internal/infra`: DB implementation and API clients.
```

> **Rationale**: Follows industry standards (Go Standard Layout) and explicitly separates domain from infrastructure.
