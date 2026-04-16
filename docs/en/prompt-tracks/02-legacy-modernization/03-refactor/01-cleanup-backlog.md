# 01 - Refactoring Backlog

## Priority Cleanups

- Which files/modules will be cleaned first?

## Patterns to Apply

- [ ] Interface extraction.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 01 - Refactoring Backlog

## Priority Cleanups

Sales and Database Module.

## Patterns to Apply

Clean Code.
```

> **Rationale**: "Sales" is too broad. "Clean Code" is not a specific refactoring pattern.

### ✅ Good Example

```markdown
# 01 - Refactoring Backlog

## Priority Cleanups

SQL Repository in `infra/repository/order.sql`.

## Patterns to Apply

Dependency Injection and Interface Extraction to enable Mocks in tests.
```

> **Rationale**: Focuses on real technical improvements (Mocks/Testing) and components that can be isolated.
