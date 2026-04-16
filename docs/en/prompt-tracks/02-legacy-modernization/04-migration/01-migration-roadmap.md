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
# 01 - Migration Roadmap

## Steps

Configure RDS Read Replica -> New Cloud Instance from October 1st to 31st.

## Checklist

- [x] Data Sync < 10ms (replica lag).
- [x] 100% of users migrated via DNS redirection.
```

> **Rationale**: Defines technologies (RDS, DNS) and technical success metrics (latency and users).
