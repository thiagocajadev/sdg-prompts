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
# SPEC-002: Advanced Coupon System

## 1. Context
We need to implement a flexible discount system to improve marketing campaign efficiency and sales conversion.

## 2. Success Metrics
* 15% increase in conversion during promotional periods.
* Zero negative balance orders due to improper discounting.

## 3. Scope & Scenarios (User Stories)
* **Scenario A:** Shopkeeper creates a coupon with validity dates and product restrictions.
* **Scenario B:** System validates a coupon in real-time before applying discount.
* **Scenario C (Concurrency):** Multiple users try to use a single-use coupon at the same time.

## 4. Constraints & Business Rules
* **Max Discount:** Coupon value cannot exceed the price of the cheapest item in the cart.
* **Concurrency:** Coupons with usage limits must use Optimistic Locking.

## 5. Out of Scope
* Automatic coupon recommendations for users.
* Tiered discounts based on user loyalty rank.

## 6. Definition of Done
- [ ] Schema for Coupon entity.
- [ ] Real-time validation logic.
- [ ] Locking mechanism for usage limits.
```

> **Rationale**: The developer will read this and IMMEDIATELY remember to shield the entity against "negative values" and apply a database lock when debiting the coupon.
