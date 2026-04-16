# 02 - Legacy Security Audit

## Current Vulnerabilities Identification

- Are there CVEs (known vulnerabilities) in obsolete libraries?
- Were secrets (passwords, API keys) found hardcoded in the code?

## Attack Surface Mapping

- Which ports and services are unnecessarily exposed?
- Which insecure protocols (e.g., HTTP, SSL v2/v3) are still permitted?

## Compliance Audit (LGPD/GDPR)

- What sensitive data is handled without encryption or anonymization?
- Does the current system meet the minimum legal privacy requirements?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Legacy Security Audit

## Current Vulnerabilities

The system is old but has never been hacked.

## Attack Surface

Normal internet.

## Compliance Audit

I think everything is fine with LGPD.
```

> **Rationale**: "Never been hacked" is not a guarantee of security. "Normal internet" and "I think it's fine" are unacceptable answers for a staff engineer.

### ✅ Good Example

```markdown
# 02 - Legacy Security Audit

## Current Vulnerabilities

- 45 critical vulnerabilities (CVE-2021-xxxx) in the Django 1.8 framework.
- AWS Production API key found in the `settings.py` file.

## Attack Surface

- Port 21 (FTP) open on the application server, allowing anonymous access.
- Support for TLS 1.0 and 1.1 still active (vulnerable to BEAST/POODLE).

## Compliance Audit

- Patient health data stored in plain text in the database.
- Absence of user consent logs (LGPD non-compliance).
```

> **Rationale**: Identifies specific vulnerabilities, insecure open ports, and serious legal compliance failures.
