# 02 - Incident Post-Mortems (Outage Analysis)

## Timeline and Impact

- What was the exact timeline from the start of the systemic failure to full recovery (_Time to Recovery_)?
- How many users or transactions were impacted by the downtime? Were there alerts covering this specific type of failure?

## Root Cause Analysis ("The 5 Whys")

- How did the system break? (Avoid pointing fingers at individuals _"Someone messed up"_; focus on the process _"The pipeline let it through"_).
- What was the "hidden trigger" that didn't appear in the _Staging / Homogenization_ environment?

## Action Plan (Action Items)

- What does the team **need to implement** in the code, infrastructure, or CI/CD so that this failure **never** happens again structurally in the future?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Post-Mortem: Database Down

## Impact

It was bad in the afternoon, and customers complained.

## Root Cause

John ran the wrong migration command in production.

## Action Items

John will be more careful and take a SQL course.
```

> **Rationale**: Classic blame culture. Condemning the developer does not resolve systemic fragility. In 6 months, "Joseph" will run the wrong command again because the pipeline remains loose.

### ✅ Good Example

```markdown
# 02 - Post-Mortem: Master Database Down (DB-Outage)

## Timeline

- `14:02 PM`: PostgreSQL CPU usage hits 100%.
- `14:05 PM`: Gateway starts returning Status 504 in the App for ~4,500 connected users.
- `14:14 PM`: Datadog alarm goes off in the Ops Slack. Escalation triggered.
- `14:26 PM`: Manual rollback of the _Target Group_, restored to normality. Duration of **24 min**.

## Root Cause Analysis

1. **Why did the CPU explode?** N+1 query from a heavy report uploaded this morning.
2. **Why did it pass the CI?** Lack of data volume metrics in the _Load Test_ pipeline.

## Action Items

- **[Tomorrow]**: Add a mandatory global pagination limit `limit(50)` in the Base API.
- **[By Friday]**: Integrate `k6` into the CI with a cloned database at 10% volume, blocking any query `> 500ms`.
```

> **Rationale**: Professionalized the failure. Without a witch hunt, the failure becomes the genetic seed of automated protection in the company's future infrastructure.
