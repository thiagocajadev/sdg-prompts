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
# Testing Strategy

**Unit (Unit Tests - Domain Focus)**
Should focus on the `CouponDomain` Entity:

- `(Happy Path)` If valid, discounts value.
- `(Sad Path)` Throws `InsufficientBalanceException`.
- `(Sad Path)` Throws `ExpiredCouponException` if CurrentDate > Validity.

**Integration (Controller/API Focus)**

- Mock external payment API to always return "Approved".
- Execute POST /checkout request and ensure that:
  - The `tbl_orders` table inserted a new ID.
  - Final return `201 Created` and body contains `{ success: true, order_id: 12 }`.
```

> **Rationale**: Based on this _Strategy_, even more junior devs build efficient `.spec.ts` files without being afraid of the PR being blocked or leaving security holes or domain failures.
