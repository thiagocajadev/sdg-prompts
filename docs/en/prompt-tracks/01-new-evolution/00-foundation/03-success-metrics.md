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
# SPEC-011: Checkout Performance Baseline

## 1. Context
Establishing measurable goals for the checkout completion and API performance.

## 2. Success Metrics
* Increase checkout completion rate from 65% to 90%.
* API Response < 500ms P95.

## 3. Scope & Scenarios
* **Baseline:** Current completion is 65%.
* **Target:** 90% within 3 months post-launch.

## 4. Constraints & Business Rules
* 100% of business flows must be covered by integration tests.
* Metrics must be measured during peak load times.

## 5. Out of Scope
* Improving UI load times (focus on API/Backend only).
* Third-party gateway latency metrics.

## 6. Definition of Done
- [ ] K6 performance tests passing.
- [ ] Integration test suite verified.
```

> **Rationale**: Provides a target number (90%), a baseline value (65%), a timeframe (3 months), and clear technical criteria.
