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
# Decommissioning Plan: Sales Module V1

## Phase 1: Isolation

- The `/v1/sales` routes were configured via Nginx to trigger a `301 Redirect` to the new `/v2/sales`.
- The Legacy MySQL DB had its `writer` password revoked, operating only as a `read-only replica`. It will remain this way for 15 days (Smoke Monitoring Period).

## Phase 2: Physical Decommissioning (2026-08-20)

- Shutdown of all V1 EC2 instances identified under the AWS Tag `env:legacy-sales`.
- Full dump generated and sent to **S3 Deep Glacier** with a Lifecycle rule for definitive purge in 5 years (Tax/Legal Compliance).
- Definitive Drop of the legacy RDS database, resulting in a saving of $850/month of Cloud TCO.
```

> **Rationale**: Pure professionalism. Shutting down software is as technically considered as building it. We mitigate failures, handle accounting data retention, and celebrate the exact savings in infrastructure dollars.
