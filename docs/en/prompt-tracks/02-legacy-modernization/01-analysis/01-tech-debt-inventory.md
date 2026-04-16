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
# SPEC-020: Tech Debt Liquidation Plan

## 1. Context
`OrderProcessor` module is highly coupled to `DBContext`, causing a 60% loss in developer productivity due to recurring bugs.

## 2. Success Metrics
* Reduce bug-fixing time by 40% in the core module.
* Prevent $500k in potential regulatory fines.

## 3. Scope & Scenarios
* **Problem:** Inability to unit test the domain logic.
* **Impact:** 60% of sprint time spent on legacy maintenance.

## 4. Constraints & Business Rules
* Refactor must maintain 100% backward compatibility with existing data.
* Mandatory audit logs for all financial mutations.

## 5. Out of Scope
* Improving UI load times for the admin panel.
* Decommissioning non-critical reporting modules.

## 6. Definition of Done
- [ ] Domain logic isolated from `DBContext`.
- [ ] Unit tests reaching 80% coverage in the refactored module.
- [ ] Audit logs verified in production.
```

> **Rationale**: Transforms technical debt into **business numbers**. A 60% loss in productivity and real fines are unbeatable arguments for project approval.
