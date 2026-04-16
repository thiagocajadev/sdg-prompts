# 03 - Architecture Decision Record (ADR)

This standard template must be used to document any and all structuring architectural decisions throughout the project's life. An ADR ensures that the historical context of the decision (Why didn't we use tool X?) will be preserved forever.

## Context and Problem

- **Status:** [Proposed | Accepted | Rejected | Obsolete]
- **What is the current technical pain?** What motivated the team to seek a new architectural solution or insert a new heavy dependency?

## Options Considered

- Option 1: [Name and Brief Description] (Pros and Cons)
- Option 2: [Name and Brief Description] (Pros and Cons)

## Decision (What we will do)

- Option X was chosen because [Rationale].

## Consequences and Trade-offs

- What do we lose with this decision? (e.g., +Cost, steeper learning curve).
- What do we gain? (e.g., +Scalability, -Latency).

---

## Learn by Examples

### ❌ Bad Example

```markdown
# ADR: Migrate to Postgres

**Status:** Done
We chose PostgreSQL because MySQL was slow and the CTO ordered it. We will gain speed.
```

> **Rationale**: Lacks metrics. "Was slow" is not a metric. What were the evaluated trade-offs? Which versions of PG vs. MySQL operated under stress? Anyone who inherits this in the future will not know the _real_ weight of the technical decision.

### ✅ Good Example

```markdown
# ADR: Migrate RabbitMQ Queue to AWS SQS

**Status:** Accepted

## Context

We have 1M jobs/day and the on-premise RabbitMQ cluster managed by us consumes 20h/month of DevOps just in patches and OOM (Out-of-memory) monitoring.

## Options Considered

- 1. **Paid RabbitMQ Cloud**: Cost $500/month. Preserves our existing code.
- 2. **AWS SQS**: Estimated cost $8/month thanks to low throughput; requires rewriting the backend's IMessageQueue interface.

## Decision

Option 2 (SQS) was chosen due to unbeatable long-term cost margins and being fully serverless.

## Consequences

- Gains: Zero hours in infrastructure maintenance, cost reduced from $500 to $8.
- Losses: Estimated 1-sprint refactor (~12 points) in the Backend to switch libraries.
- Risk: Partial lock-in to the AWS cloud.
```

> **Rationale**: Perfect history. Someone 3 years in the future reads this document and perfectly understands the cost and operational pressures of the time. No one will debate and reignite the desire to return to RabbitMQ without a more solid argument.
