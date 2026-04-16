# Specification Pipeline

This directory establishes the technical governance and architectural baseline for the project. The core protocol mandates that **no implementation should precede its corresponding specification**.

> [!TIP]
> **AI Orchestration**: These templates provide high-context engineering standards for AI agents. Proper specification ensures technical density and prevents architectural drift.

---

## Development Tracks

### 00 - Lite Mode (Freelance & MVP)

Standardized flow for rapid iteration on small-scale projects, proofs of concept, and utility tools.

- **Pipeline**: Scope → Stack → Integration.
- **Location**: `.ai/prompts/dev-tracks/00-lite-mode/`

### 01 - New Evolution (Greenfield)

Primary flow for new system features, domain modules, or greenfield project architecture.

- **Pipeline**: Foundation → Setup → Architecture → Security → Delivery → Features → Evolution.
- **Location**: `.ai/prompts/dev-tracks/01-new-evolution/`

### 02 - Legacy Modernization (Brownfield)

Standardized protocol for technical rescue, refactoring, and legacy system migration.

- **Pipeline**: Foundation → Analysis → Strategy → Refactoring → Migration.
- **Location**: `.ai/prompts/dev-tracks/02-legacy-modernization/`

---

## Engineering Principles

1.  **Mandatory Sequential Execution**: Never advance to the next pipeline stage without completing the previous one.
2.  **Logic over Code**: A feature implementation is only permitted after the **Architecture & Data Model** are consolidated.
3.  **Local Numeric Prefixing**: All files maintain sequential numbering within their respective folders to preserve the logical order of each stage.
4.  **Gatekeepers**: Feature development (Phase 04) is only permitted after the Delivery stage (Phase 03) is ready (CI/CD, Linting, and Quality).

---

## Specification Standard (Feature)

Every new functionality in the `04-features` directory follows this standard:

```markdown
# [ID]- [Feature Name]

## Context

- Problem to be solved and expected business/system impact.

## Scope

- Planned deliverables vs. Non-goals (what will NOT be covered).

## Business Rules

- Critical validations, success cases, and exception flows.

## Architecture & Design

- Integration points, API contracts, and Schema changes.

## Implementation Roadmap

- Concrete steps for the AI Agent or Developer to follow.
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
# 04-01 - One-Click Checkout (Stripe)

## Context

Reduce cart abandonment during the final payment stage.
**Success Metric**: 15% increase in conversion for returning users.

## Scope

- Integration with Stripe Vault for saved tokens.
- **Non-Goals**: Full gateway migration or local card storage (PCI Compliance).

## Business Rules

- Only logged-in users with a valid `stripe_customer_id`.
- Synchronous stock check before `PaymentIntent` confirmation.

## Architecture & Design

- **Integration**: `StripeService` + `OrderOrchestrator`.
- **Constraint**: All IDs must follow the `chkt_` prefix for traceability.

## Implementation Roadmap

1. [ ] Create inventory pre-validation webhook.
2. [ ] Implement Stripe Elements in the Guest Checkout flow.

## Testing Strategy

- **Scenario A**: Success with cached card and >0 stock.
- **Scenario B**: Atomic rollback if payment fails after stock reservation.
```

> **Rationale**: Specific objectives, business metrics, clear boundaries, and atomic error handling strategies.
