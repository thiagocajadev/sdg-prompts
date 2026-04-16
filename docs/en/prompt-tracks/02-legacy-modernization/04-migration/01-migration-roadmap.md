# 01 - Migration Roadmap

## Migration Steps

1.  [ ] Parallel infrastructure setup.
2.  [ ] Database migration.

## Final Checklist

- [ ] 0 critical bugs in the new system.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 01 - Migration Roadmap

## Steps

Move everything tomorrow and re-test.

## Checklist

App 100% live.
```

> **Rationale**: "Tomorrow" is not a roadmap. "100% live" ignores quality or consistency.

### ✅ Good Example

```markdown
# SPEC-021: Large-Scale RDS Migration

## 1. Context
Migrating core database to a new cloud instance with minimal downtime and data safety.

## 2. Success Metrics
* Downtime under 30 seconds for DNS switch.
* Data Sync lag < 10ms during migration.

## 3. Scope & Scenarios
* **Phase A:** RDS Read Replica configuration.
* **Phase B:** New Cloud Instance DNS redirection.

## 4. Constraints & Business Rules
* 100% user migration verified via redirection counters.
* Zero data loss during the replica-to-master promotion.

## 5. Out of Scope
* Switching from RDS to a different database engine (e.g., NoSQL).
* Modernizing the SQL schema during migration.

## 6. Definition of Done
- [ ] Replica lag verified under 10ms.
- [ ] Successful DNS switch in the production environment.
```

> **Rationale**: Defines technologies (RDS, DNS) and technical success metrics (latency and users).
