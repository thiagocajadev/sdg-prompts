# Specification Pipeline

This directory establishes the technical governance and architectural baseline for the project. The core protocol mandates that **no implementation should precede its corresponding specification**.

> [!TIP]
> **AI Orchestration**: These templates provide high-context engineering standards for AI agents. Proper specification ensures technical density and prevents architectural drift.

---

## Development Tracks

### 00 - Lite Mode (Freelance & MVP)

Standardized flow for rapid iteration on small-scale projects, proofs of concept, and utility tools.

- **Pipeline**: Scope → Stack → Integration.

### 01 - New Evolution (Greenfield)

Primary flow for new system features, domain modules, or greenfield project architecture.

- **Pipeline**: Foundation → Setup → Architecture → Security → Delivery → Features → Evolution.

### 02 - Legacy Modernization (Brownfield)

Standardized protocol for technical rescue, refactoring, and legacy system migration.

- **Pipeline**: Foundation → Analysis → Strategy → Refactoring → Migration.

---

## Engineering Principles

1.  **Mandatory Sequential Execution**: Never advance to the next pipeline stage without completing the previous one.
2.  **Logic over Code**: A feature implementation is only permitted after the **Architecture & Data Model** are consolidated.
3.  **Local Numeric Prefixing**: All files maintain sequential numbering within their respective folders to preserve the logical order of each stage.
4.  **Gatekeepers**: Feature development (Phase 04) is only permitted after the Delivery stage (Phase 03) is ready (CI/CD, Linting, and Quality).

---

## Specification Standard (SPEC)

Every new functionality in the `04-features` directory must follow this mandatory 6-step standard:

```markdown
# SPEC-XXX: [Title]

## 1. Context
[Why this is being built, the problem it solves, and the target audience.]

## 2. Success Metrics
* [Measurable outcome A]
* [Measurable outcome B]

## 3. Scope & Scenarios (User Stories)
* [Detailed scenarios and user stories.]

## 4. Constraints & Business Rules
* [Logical limits and mandatory behaviors.]

## 5. Out of Scope
* [What will NOT be delivered in this task.]

## 6. Definition of Done
- [ ] [Verification steps and completion criteria.]
```

---

## Staff Engineering Examples

### ❌ Bad Example (AI Slop / Generic)

```markdown
# 04-01 - System Improvement

## Context

Improve the system for users and increase sales.

## Scope

Everything to make it good. No non-goals.

## Business Rules

Fast system. Users can buy things.

## Architecture & Design

Market best practices. DB integration.

## Implementation Roadmap

1. [ ] Code it. 2. [ ] Test it.

## Testing Strategy

Test everything.
```

> **Rationale**: Vague, lacks metrics, no technical definitions, and no clear acceptance criteria. Pure "AI slop".

### ✅ Good Example (Staff Quality)

```markdown
# SPEC-001: One-Click Checkout (Stripe)

## 1. Context
Reduce cart abandonment during the final payment stage by simplifying the checkout flow for returning users.

## 2. Success Metrics
* 15% increase in conversion rate for returning users.
* Average checkout time under 10 seconds.

## 3. Scope & Scenarios (User Stories)
* **Scenario A:** Success with cached card and >0 stock.
* **Scenario B:** Atomic rollback if payment fails after stock reservation.
* **User Story:** As a returning customer, I want to pay with one click so I don't have to re-enter my card details.

## 4. Constraints & Business Rules
* Only logged-in users with a valid `stripe_customer_id`.
* Synchronous stock check before `PaymentIntent` confirmation.
* All transaction IDs must follow the `chkt_` prefix for traceability.

## 5. Out of Scope
* Full gateway migration or alternative payment methods (e.g., Crypto).
* Local storage of credit card numbers (PCI Compliance limit).

## 6. Definition of Done
- [ ] Stripe Vault integration verified.
- [ ] Inventory pre-validation webhook implemented.
- [ ] 100% of e2e payment scenarios automated.
```

> **Rationale**: Specific objectives, business metrics, clear boundaries, and atomic error handling strategies following the mandatory 6-step SPEC protocol.
