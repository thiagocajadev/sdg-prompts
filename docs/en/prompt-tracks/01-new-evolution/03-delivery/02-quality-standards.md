# 02 - Quality Standards

## What Does Quality Mean to Us?

- Code without obvious technical debt.
- Tests that actually test business rules.

## Minimum Coverage

- [e.g., 80% in business logic]

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Quality Standards

## What is Quality

Having few bugs and pretty code.

## Minimum Coverage

10%.
```

> **Rationale**: "Few bugs" and "pretty" are subjective. 10% coverage is insignificant and dangerous.

### ✅ Good Example

```markdown
# 02 - Quality Standards

## What is Quality

Code that follows SOLID principles and 100% of critical payment flows with E2E test coverage.

## Minimum Coverage

80% line coverage in `/internal/domain`.
```

> **Rationale**: Defines concrete principles (SOLID) and aggressive testing goals for critical areas.
