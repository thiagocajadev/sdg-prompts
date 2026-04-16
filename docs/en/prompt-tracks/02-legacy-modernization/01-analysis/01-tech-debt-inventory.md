# 01 - Technical Debt Inventory

## Risk Mapping

- Which modules are the most fragile?
- Where are the biggest performance bottlenecks?

## Obsolete Technologies

- Unsupported libraries (e.g., Python 2.7, .NET 4.5).
- Runtime versions (End-of-Life).

## Cost of Inertia (Inertia vs. Migration)

- **Financial Risk**: What is the estimated cost of a compliance fine or a data leak?
- **Operational Cost**: How much time does the team lose "extinguishing fires" in the legacy system?
- **Opportunity Cost**: Which new features are we failing to launch?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 01 - Technical Debt Inventory

## Risk Mapping

The code is confusing and full of if-statements.

## Cost of Inertia

We're losing time cleaning the code.
```

> **Rationale**: "Confusing" and "losing time" are sentimental metrics, not executive ones. They do not justify the investment of a migration.

### ✅ Good Example

```markdown
# 01 - Technical Debt Inventory

## Risk Mapping

`OrderProcessor` module is highly coupled to `DBContext`, making unit testing impossible.

## Cost of Inertia

- **Operational**: The team spends 60% of the sprint fixing recurring bugs in the legacy system.
- **Economic**: Monthly maintenance of the legacy server costs 3x more than a modern serverless instance.
- **Risk**: Potential $500k fine due to the lack of audit logs required by the new banking regulation.
```

> **Rationale**: Transforms technical debt into **business numbers**. A 60% loss in productivity and real fines are unbeatable arguments for project approval.
