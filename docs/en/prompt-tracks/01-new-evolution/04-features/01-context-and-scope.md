# 01 - Context and Scope (Context & Scope)

## Problem and Impact (What and Why)

- **Business Problem:** Which customer or operational "pain point" are we solving?
- **Affected Metrics:** What do we expect to improve? (e.g., +Conversion, -Response Time, +Retention).
- **Target Audience:** Does it affect all users, admins, or just a specific role?

## Scope (Scope Boundaries)

- **In-Scope (Goals):** What **MUST** be delivered as part of this feature.
- **Out-of-Scope (Non-Goals):** What we **WILL NOT** do now (fundamental to protect against _Scope Creep_).

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Context

We need to add an export to PDF button.

# Scope

Make the export work.
```

> **Rationale**: Does not say "Why". Exporting to PDF is the solution, not the problem. What if the problem is "the accountant needs the monthly report"? Perhaps a CSV silently sent by email would be better than a slow button on the UI.

### ✅ Good Example

```markdown
# Context

**Problem:** Currently, our shopkeepers spend 4 hours a month taking screenshots of sales screens to send to accounting.
**Metrics:** Reduce time spent by shopkeepers (CSAT) and decrease CS tickets asking for reports.

# Scope

**In-Scope:** UI-based export of CSV and PDF reports from the "Financial" tab.
**Out-of-Scope:** Automatic scheduling (Cron) of report delivery. We will only perform manual exports for now.
```

> **Rationale**: Defines the root problem and blocks inappropriate future proposals for the moment (such as automatic scheduling) that would delay delivery.
