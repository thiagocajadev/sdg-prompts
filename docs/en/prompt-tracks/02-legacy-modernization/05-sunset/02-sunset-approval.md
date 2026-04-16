# 02 - Approval: Sunset and Final Decommissioning

## Artifacts Checklist

- [ ] 01-decommission-plan.md (Evidence of Read-Only applied and DNS redirections).

## Executive Approval (The Farewell)

- **Migration Tech Lead**: [Signature/Date]
- **Cost/Finance Team (FinOps)**: [Signature/Date]
- **Product Owner (PM)**: [Signature/Date]

## Modernization Completion Definition

- [ ] Legacy domain no longer routes active traffic (0 status usage in API Gateway).
- [ ] Final backup exported for retention (Cold Storage).
- [ ] Invoices (Billing) confirm that legacy instances have been removed from the cloud cost.
- [ ] Old DNS officially pointing 100% to the New Ingress Controller.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Sunset Approval

## Checklist

- [x] We turned everything off.

## Completion Definition

- [x] The system stopped billing.
```

> **Rationale**: Turned everything off "when" and "how"? What about the 5 years of backups required by law? The migration failed at a quiet point.

### ✅ Good Example

```markdown
# Sunset Approval: Complete Extinction

## Final Approvals

- **Tech Lead**: Renato Vanes (2026-09-20) confirmed via Datadog 0 RPS in the Legacy Node for 30 uninterrupted days.
- **FinOps**: Claire River (2026-09-21) proved the removal of the old AKS cluster and the T3 RDS database in the Cost panel. ~$2,500 reduction validated!

## Completion Definition (The Trophy)

- [x] Glacier retention approved by the Chief Legal Officer.
- [x] Legacy CNAME DNS changed to ALB v2.

## Project Completion Ceremony

Modernization officially Closed. The legacy GitHub repository `vendas-delphi-legacy` has been Archived. 🚀
```

> **Rationale**: Monumental closing of Staff-level work. No loose ends, official cost reduction with FinOps endorsing the project's ROI, dead files secured, and repo "Archived." Everyone celebrates a shielded transition.
