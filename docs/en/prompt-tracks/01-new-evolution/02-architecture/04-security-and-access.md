# 03 - Security and Access

## Authentication and Authorization

- How does the user identify themselves (OAuth2, JWT, SAML)?
- How do we control permissions (RBAC, ABAC)?

## Data Protection

- How do we protect data at rest (Encryption at rest)?
- How do we protect data in transit (TLS/SSL)?
- How do we manage secrets (HashiCorp Vault, AWS Secrets Manager)?

## Audit and Logs

- Which actions are recorded in audit logs?
- Where are these logs securely stored?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 03 - Security and Access

## Authentication and Authorization

User and password in the database.

## Data Protection

We will use HTTPS.

## Audit

Record to the server console.
```

> **Rationale**: Plain text passwords are unacceptable. HTTPS only solves transit, not rest. Console logs disappear on reboot.

### ✅ Good Example

```markdown
# SPEC-017: Security Hardening Protocol

## 1. Context
Establishing security benchmarks for authentication, authorization, and data protection.

## 2. Success Metrics
* Zero plain-text credentials in the entire repository.
* 100% compliance with corporate log retention policies (2 years).

## 3. Scope & Scenarios
* **Auth:** JWT RSA-256 + RBAC.
* **Rest:** AES-256 for Tax ID (CPF) fields.

## 4. Constraints & Business Rules
* 15-minute expiration for all access tokens.
* All secrets MUST be injected via AWS Secrets Manager at runtime.

## 5. Out of Scope
* Implementing biometric authentication in this phase.
* Conducting external penetration testing (audit only).

## 6. Definition of Done
- [ ] JWT signer logic verified.
- [ ] AES-256 encryption helper tested.
- [ ] Audit log retention policy configured.
```

> **Rationale**: Defines algorithms (RSA-256, AES-256), specific tools, and compliance policies (2-year log retention).
