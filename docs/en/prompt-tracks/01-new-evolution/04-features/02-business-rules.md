# 02 - Business Rules

## Logic and Behavior

- **Main Flow (Happy Path):** What is the ideal path for the entity or user? (Use Clear User Stories or Flowcharts).
- **Domain Constraints:** Logical limits of the application. (e.g., "An order cannot move from 'Shipped' back to 'Pending'").

## Edge Cases & Validations (Sad Path)

- **Edge Scenarios:** What happens when parameters are invalid? (e.g., "Age < 18 on a blocked purchase").
- **Concurrency (Race Conditions):** What if 2 users access the same resource simultaneously? (e.g., buying the last ticket).
- **Partial Resilience:** If something external fails, do we block everything or offer a fallback?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Rules

- The user submits the form and it's saved in the 'tbl_users' database.
- If it fails, return 500.
```

> **Rationale**: It's coupled to the database and technical errors (500). Business rules should be described in a technology-agnostic way, focusing on _behavior_ rather than _implementation_.

### ✅ Good Example

```markdown
# Rules

- **Happy Path:** The shopkeeper creates a Coupon and defines its validity. The system allows its use on listed products.
- **Constraints:** The coupon discount value can never be greater than the price of the lowest-priced item in the cart (To avoid negative order balances).
- **Concurrency (Race Condition):** A coupon with `use_limit = 1` must use Optimistic Locking; if two users attempt checkout in the same millisecond, one will receive a "Coupon Exhausted" error.
```

> **Rationale**: The developer will read this and IMMEDIATELY remember to shield the entity against "negative values" and apply a database lock when debiting the coupon.
