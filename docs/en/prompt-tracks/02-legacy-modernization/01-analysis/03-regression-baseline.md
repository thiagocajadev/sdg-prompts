# 03 - Regression Baseline (Security Tests)

## Critical Flow Coverage

- How will we ensure that the refactoring/migration won't break current functionalities?
- What are the "Golden Paths" (most critical business routes) that must have _End-to-End_ (E2E) tests?

## Assertion Tools

- Which tool will be used to record the current behavior of the legacy system before altering it (e.g., Playwright, Cypress, Postman Collections)?
- Is there any load/stress test (e.g., k6) mapped to ensure the new code performs as well as or better than the legacy one?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 03 - Regression Baseline

## Coverage

We'll test it manually before uploading.

## Tools

The QA will use their Postman.
```

> **Rationale**: Refactoring legacy systems without automated regression tests is like jumping out of a plane without a methodological parachute. "Manual testing" creates bias and overlooks _edge cases_.

### ✅ Good Example

```markdown
# 03 - Regression Baseline

## Critical Flow Coverage

- **Mapped Routes**: `POST /checkout` and `GET /invoice/:id`.
- **Strategy**: 100% success coverage on these two flows via E2E tests running in a mirrored Legacy _Staging_ environment.

## Assertion Tools

- **Automated E2E**: Playwright (Scripts in the `qa-legacy-suite` repository).
- **Performance Validation**: k6 script to prove that the new Cart route in Node.js matches the 150ms of the old PHP one.
```

> **Rationale**: Creates a real "electric fence." The developer has the peace of mind to rip out parts of the system knowing that Playwright will immediately notify them if they broke the old business logic.
