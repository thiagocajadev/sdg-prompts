# 03 - Success Metrics

## KPIs (Indicators)

- Which metric will be moved (e.g., response time, conversion rate)?
- What is the current baseline and what is the target?

## Success Checklist

- [ ] Feature X running in production.
- [ ] Automated tests with 80%+ coverage.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 03 - Success Metrics

## KPIs

The system must be very fast and easy to use.

## Success Checklist

- [ ] Everything ready.
```

> **Rationale**: How do you test "easy"? Without numbers, success is a subjective opinion.

### ✅ Good Example

```markdown
# 03 - Success Metrics

## KPIs

Increase the checkout completion rate from 65% to 90% in the first 3 months after launch.

## Success Checklist

- [x] Response < 500ms P95 across all APIs.
- [x] 100% of business flows covered by integration tests.
```

> **Rationale**: Provides a target number (90%), a baseline value (65%), a timeframe (3 months), and clear technical criteria.
