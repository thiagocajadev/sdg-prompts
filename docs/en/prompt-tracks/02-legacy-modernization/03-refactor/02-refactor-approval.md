# 02 - Refactoring Approval

## Artifacts Checklist

- [ ] 01-cleanup-backlog.md (Prioritized)

## Technical Approval

- **Tech Lead**: [Signature/Date]
- **Development Team**: [Signature/Date]

## Definition of Readiness (Ready for Migration)

- [ ] Critical code extracted into interfaces.
- [ ] Regression tests (Unit/Integration) cover 80% of the changes.
- [ ] The monolith is stable for the final migration.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Refactoring Approval

## Checklist

- [x] We ran the linter.

## Definition of Readiness

- [x] The code is pretty.
```

> **Rationale**: "Pretty code" is not an operational readiness criterion for migration.

### ✅ Good Example

```markdown
# 02 - Refactoring Approval

## Technical Approval

- **Lead**: Mark Oliver (2026-07-10)

## Definition of Readiness

- [x] SQL Repository isolated under a common interface.
- [x] Integration test suite via Docker running in the CI.
```

> **Rationale**: Focuses on technical isolation and test automation to ensure the security of the migration.
