# 04 - Audit and Threat Modeling

## Threat Modeling

- What are the main attack vectors identified (e.g., OWASP Top 10)?
- How do we mitigate "Supply Chain" and dependency attacks?

## Audit Plan

- Who will perform the audit (Internal team, Pentest company)?
- How often (Every major release, annually)?
- Which automated security tools (SAST/DAST) will be integrated?

## Resilience and Response

- How does the system behave under attack (Fail-safe)?
- What is the response plan for security incidents?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 04 - Audit and Threat Modeling

## Threat Modeling

The system will be secure against hackers.

## Audit Plan

We'll do a test before launching.

## Resilience

If it goes down, we'll bring it back up.
```

> **Rationale**: "Secure against hackers" is an aspiration, not a specification. It doesn't define tools or concrete plans.

### ✅ Good Example

```markdown
# 04 - Audit and Threat Modeling

## Threat Modeling

- Focus on avoiding Broken Access Control (OWASP #1) through forced auditing in API interceptors.
- Supply Chain mitigation via dependency scanner (Snyk) blocking the CI in case of critical failures.

## Audit Plan

- Bi-weekly DAST scan via OWASP ZAP in Staging environment.
- Annual external Pentest performed by a CREST-certified company.

## Resilience

- Aggressive Rate Limit (100 req/min/IP) to prevent Brute Force.
- Transparent Circuit Breaker: if the Authentication service fails, all accesses are denied (Fail-closed).
```

> **Rationale**: Defines specific attacks (Broken Access Control), tools (Snyk, OWASP ZAP), frequency, and failure behaviors (`Fail-closed`).
