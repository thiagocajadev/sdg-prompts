# 05 - Engineering Culture & Code Hostage (Anti-Silos)

Knowledge silos destroy the productivity and scalability of a technical team. "Hero Culture" _(Single Point of Failure / Bus Factor = 1)_ — where only one developer knows how to handle the payment system or the deployment — is an unacceptable operational risk at the Staff Engineering level.

## Code Ownership Principles

- The code belongs to the organization, not to the person who wrote it. No one is the absolute "owner" of a service.
- The code must be written in such a way that a newly hired Mid-level Developer can understand and maintain it without having to call the original author in the middle of the night.

## Practical Anti-Code-Hostage Measures

- **Mandatory Code Review:** No one pushes code directly to the `Main` branch (exception for regulated _hotfixes_). Mandatory `Approve` from at least 1 developer who was NOT the author of the task.
- **Domain Rotation (Pairing):** If the Squad is going to do a major refactoring of module X, the Senior Dev who masters the subject MUST pair (Pair Programming) with another developer, focusing on knowledge dilution.
- **Systemic Permissions:** Master access to the Production Database or the AWS Deployment key is never in the hands of one and only one person. Systemic "Hostage-taking" is not allowed. (Use Vaults or IAM Roles).

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Culture

- Pedro handles the Sales table because he knows it. We don't even touch it.
- If the database freezes, call him on his cell in the middle of the night.
```

> **Rationale**: Chronic Hero Culture. The project stops running during Pedro's vacation or becomes a hostage if he leaves the company. Furthermore, Pedro himself becomes overwhelmed (technical burnout).

### ✅ Good Example

```markdown
# Technical Culture and Continuity

- Every new API related to `Billing` must have mandatory pairing of 1 Senior Dev + 1 Mid-level Dev.
- **Bus Factor Check:** At the end of each quarter (Quarter), the Tech Lead ensures that at least 3 devs from the Chapter are comfortable performing a Manual Deploy of the Critical module in Production.
- CI/CD automatically blocks _Pull Requests_ of any `.config` file if the reviewer is not from another squad (Cross-review to avoid configuration silos).
```

> **Rationale**: We transform the "goodwill" to teach into a Management Metric (Quarterly Bus Factor) and an automatic technical restriction in the CI/CD. No one takes the codebase hostage, and the team sleeps in peace.
