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
# SPEC-010: Cash Closing Optimization

## 1. Context
Current cash closing takes 40 minutes daily per store. We need to automate this to reduce errors and frustration.

## 2. Success Metrics
* Reduce closing time from 40 min to under 5 min.
* Operational cost reduction estimated at $2.5M annually.

## 3. Scope & Scenarios
* **Scenario A:** Automated data sync between POS and ERP.
* **Risks:** Handling PII (1M customers) and PCI-DSS audit requirements.

## 4. Constraints & Business Rules
* Must be compliant with LGPD/GDPR.
* API keys must be moved to secure Vault (Secret Management).

## 5. Out of Scope
* Automatic dispute resolution for banking errors.
* Integration with legacy POS systems older than v5.0.

## 6. Definition of Done
- [ ] PCI-DSS audit passed.
- [ ] Sensitive data encryption verified.
- [ ] Closing time verified in staging.
```

> **Rationale**: Defines clear security risks, legally protected data, and financial impacts of compliance.
