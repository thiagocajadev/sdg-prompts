# 04 - Testing Strategy (Testing Strategy)

## TDD / BDD Approach

- Which key behaviors described in the `02-business-rules.md` file must be covered by **Unit Tests**? (e.g., Testing the exception thrown when weight is negative).
- Which routes described in the `03-architecture-and-design.md` file will require **Integration Tests** simulating real requests using Mocks/Stubs for the Database/External Dependencies?

## Extreme Cases (Smoke & Performance)

- Does the feature involve heavy data? Will a load testing script (K6, JMeter) be necessary?
- How to validate if integrations with third-party applications fail gracefully (e.g., banking API timeout)?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Strategy

Create tests with Jest/XUnit.
Run in the CI.
```

> **Rationale**: Too generic. Every squad will run tests in the CI, but WHAT needs to be tested so that we can validate even before the first "If" is programmed?

### ✅ Good Example

```markdown
# SPEC-004: Coupon System Testing Strategy

## 1. Context
Validation plan to ensure the Advanced Coupon System (SPEC-002) is resilient and accurate.

## 2. Success Metrics
* 100% test coverage for domain-level discount logic.
* Zero race condition bugs during single-use coupon redemption.

## 3. Scope & Scenarios (User Stories)
* **Unit Tests:** `CouponDomain` entity (Validates status, balance, and expiration).
* **Integration Tests:** `POST /checkout` flow with mock payment provider.

## 4. Constraints & Business Rules
* Use Jest/Vitest for unit testing.
* Mock external APIs to ensure test reliability.

## 5. Out of Scope
* Performance testing for over 100k concurrent users.
* Manual UI testing for cross-browser CSS issues.

## 6. Definition of Done
- [ ] Unit tests for `InsufficientBalance` and `ExpiredCoupon` exceptions.
- [ ] Integration test verifying `tbl_orders` insertion and `201 Created` response.
```

> **Rationale**: Based on this _Strategy_, even more junior devs build efficient `.spec.ts` files without being afraid of the PR being blocked or leaving security holes or domain failures.
