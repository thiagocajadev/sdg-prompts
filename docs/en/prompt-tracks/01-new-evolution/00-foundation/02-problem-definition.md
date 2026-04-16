# 02 - Problem Definition

## The Current Problem

- What is broken or inefficient today?
- What is the primary pain point for the user or the business?

## Risks and Compliance

- Are there sensitive data (LGPD/GDPR)?
- What are the security risks (leakage, unauthorized access)?
- Are there any legal or industry compliance requirements?

## Why solve it now?

- What is the cost of not solving this problem?
- What opportunities are we missing?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Problem Definition

## The Current Problem

The system is slow and users are complaining about constant crashes.

## Risks and Compliance

We haven't identified any risks yet.

## Why solve it now?

So that users don't get angry.
```

> **Rationale**: Ignores security and compliance risks, treating them as "non-existent" due to lack of analysis.

### ✅ Good Example

```markdown
# 02 - Problem Definition

## The Current Problem

The cash closing process takes 40 minutes daily in 80% of stores, causing frustration and financial errors.

## Risks and Compliance

- **Data**: Tax ID (CPF) and purchase data of 1M customers (LGPD).
- **Risk**: Payment gateway API keys exposed in the code.
- **Compliance**: PCI-DSS audit required for the new flow.

## Why solve it now?

The annual operational cost is $2.5M. Additionally, an LGPD fine for a data leak could exceed $50M.
```

> **Rationale**: Defines clear security risks, legally protected data, and financial impacts of compliance.
