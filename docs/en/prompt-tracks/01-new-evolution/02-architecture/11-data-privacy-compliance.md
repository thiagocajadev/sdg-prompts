# 10 - Data Privacy and Compliance (LGPD/GDPR)

Data protection laws are not just bureaucratic requirements; they require native architectures to support them. If a system is designed in an intertwined way, meeting a user's Right-to-be-Forgotten securely is almost impossible.

## PII (Personally Identifiable Information) Mapping

- Which columns in the new database store sensitive data (Name, Tax ID/CPF, Email, Card)?
- What is the **Masking** strategy for this data when mirrored to Quality environments (Staging/QA) or sent to application logs (e.g., Datadog)?

## Deletion and Retention

- **Right to be Forgotten:** Can the system destroy `UserId=123` and maintain relational consistency? (e.g., order records become anonymous and linked to a `deleted_user` UUID).
- **Retention Time:** What data _cannot_ be deleted at the user's request due to tax compliance, and for how long (e.g., invoices in Glacier)?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# LGPD Security

We use TLS 1.2 on the site for LGPD. The database uses disk encryption, so LGPD is covered against hackers.
```

> **Rationale**: Naive. Encrypting the disk and using SSL prevents hacker breaches and unauthorized listening, but it doesn't solve real internal compliance (LGPD/GDPR) regarding the use and deletion of information by the data subject themselves if they request it tomorrow.

### ✅ Good Example

```markdown
# Privacy By Design: Profile Module V2

- **PII Mapped (`Users` table):** The `cpf`, `phone`, and `email` columns are classified as level A PII.
- **Log Masking:** Our `pino-logger` library has been natively configured to obfuscate these keys (replacing the string with `***`). They will NEVER appear in the clear in Datadog.
- **Deletion (GDPR/LGPD):** If the `DELETE /account` route is triggered:
  1.  Real PII data in the `Users` table undergoes a _Hard Delete_.
  2.  History in `Sales` remains (Legal/Tax Requirement), but its Foreign Key is mapped to an internal `anon-ledger` system, blocking primary identification.
```

> **Rationale**: The architecture is born legally shielded from million-dollar fines. Database IDs are designed anticipating the loss of parent data without crashing the Frontend in the future.
