# 03 - Migration Approval

## Artifacts Checklist

- [ ] 01-migration-roadmap.md (Defined)
- [ ] 02-data-sync-strategy.md (Successfully tested n-times)

## Operational Approval

- **SRE / DevOps**: [Signature/Date]
- **Operations / Support Team**: [Signature/Date]

## Definition of Readiness (Ready for Rollout)

- [ ] _Dry-run_ (Shadow Load) of data migration completed successfully.
- [ ] Rollback plan tested and time limit metrics approved (e.g., MTTR < 10min).
- [ ] Maintenance window officially communicated to corporate stakeholders.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 03 - Migration Approval

## Checklist

- [x] Migrate and re-test.

## Definition of Readiness

- [x] Script is on the machine and ready to run and switch the APIs.
```

> **Rationale**: How do you prove that the migration script doesn't corrupt Database B? And worse, if it does, how do you switch the user back to an intact Database A?

### ✅ Good Example

```markdown
# 03 - Migration Approval

## Operational Approval

- **DevOps**: Bruno Costa (Approved on 2026-07-20)

## Definition of Readiness

- [x] 01-migration-roadmap.md (Window set for Saturday 02:00 AM)
- [x] 02-data-sync-strategy.md (Bidirectional Kafka synchronization tested)
- [x] Rollback tested in an isolated environment (DNS router takes 59 seconds to cancel the migration if the new infra health check turns red).
```

> **Rationale**: Showcases high operational maturity evidence. Data synchronization and rollback activation times are metered, converting the chaotic, critical moment of a legacy deployment into a controlled procedure.
