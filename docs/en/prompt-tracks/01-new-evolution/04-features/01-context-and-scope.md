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
# SPEC-001: Financial Report Exporting

## 1. Context
Currently, shopkeepers spend 4 hours a month taking screenshots for accounting. We need a manual export tool to solve this pain point.

## 2. Success Metrics
* Reduce time spent by shopkeepers (CSAT).
* Decrease CS tickets asking for reports.

## 3. Scope & Scenarios (User Stories)
* **Scenario A:** User exports CSV/PDF from "Financial" tab.
* **User Story:** As a shopkeeper, I want to export reports so I can send them to my accountant easily.

## 4. Constraints & Business Rules
* Export only available for "Financial" tab data.
* Manual triggers only (no scheduling yet).

## 5. Out of Scope
* Automatic scheduling (Cron) of report delivery.
* Legacy sales data from over 2 years ago.

## 6. Definition of Done
- [ ] CSV/PDF generation logic.
- [ ] UI export button.
- [ ] Unit tests for report data extraction.
```

> **Rationale**: Defines the root problem and blocks inappropriate future proposals for the moment (such as automatic scheduling) that would delay delivery.
