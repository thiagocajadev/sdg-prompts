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
# 03 - Security and Access

## Authentication and Authorization

- **Authn**: JWT with RSA-256 and 15min expiration time.
- **Authz**: Platform-native RBAC (Role-Based Access Control).

## Data Protection

- **Rest**: AES-256 for the Tax ID (CPF) field in the database.
- **Secrets**: Injected via AWS Secrets Manager at runtime.

## Audit

Mutation logs sent to CloudWatch Logs with 2-year retention for compliance.
```

> **Rationale**: Defines algorithms (RSA-256, AES-256), specific tools, and compliance policies (2-year log retention).
