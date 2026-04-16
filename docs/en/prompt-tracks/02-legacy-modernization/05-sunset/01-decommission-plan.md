# 01 - Decommissioning Plan (Sunset Plan)

The Sunset Plan is the final stage of modernizing a legacy (Brownfield) system. Once 100% of routes and data are in the new system, the old one MUST be deactivated. Unmaintained code left online becomes the primary gateway for security failures in the company.

## Phase 1: Isolation and Read-Only Modes

- **Redirection:** Is all legacy domain traffic now (via proxy/DNS) traveling strictly to the new software?
- **Freezing:** Was the legacy database locked as `Read-Only` to prevent forgotten users or routines from continuing to create technical trash?

## Phase 2: Termination and Physical Decommissioning

- **Orphan Dependencies:** Did we delete all crons and scheduled routines (background jobs)?
- **The End:** Official shutdown of the legacy virtual machine (EC2), cluster, or app service.
- **Data Retention & Backups:** Was the legacy database dump stored in cold storage (e.g., Amazon S3 Glacier) for the legal retention period before deleting the hot database in the cloud?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Shutdown

The new software launched last week. We stopped using the old one. At the end of the year, the sysadmin deletes the server.
```

> **Rationale**: Extremely dangerous. What ensures that no B2B customer continues using the old backend API? If the old dashboard has vulnerabilities and continues running without maintenance until the end of the year, hackers will use this bridge to steal data (Shadow IT).

### ✅ Good Example

```markdown
# SPEC-022: Legacy Sales Module Sunset

## 1. Context
Final deactivation of the Sales Module V1 to eliminate security risks and reduce cloud TCO by $850/month.

## 2. Success Metrics
* 100% of traffic successfully redirected to V2.
* Saving of $10,200 annually in cloud infrastructure costs.

## 3. Scope & Scenarios
* **Phase Isolation:** 301 Redirect for `/v1/sales`.
* **Phase Termination:** Shutdown of EC2 `env:legacy-sales`.

## 4. Constraints & Business Rules
* Legacy DB must operate as `read-only` for 15 days before shutdown.
* Mandatory S3 Deep Glacier dump for 5-year legal retention.

## 5. Out of Scope
* Decommissioning the internal CRM (planned for next quarter).
* Deleting backups older than 5 years.

## 6. Definition of Done
- [ ] Nginx redirects verified.
- [ ] Full DB dump confirmed in Glacier.
- [ ] Legacy RDS instance dropped.
```

> **Rationale**: Pure professionalism. Shutting down software is as technically considered as building it. We mitigate failures, handle accounting data retention, and celebrate the exact savings in infrastructure dollars.
