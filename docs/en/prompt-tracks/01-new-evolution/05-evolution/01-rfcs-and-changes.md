# 01 - Request for Comments (RFC) & Architecture Changes

## Problem and Motivation for Change

- What motivated the evolution of this architecture in an already live system (e.g., performance bottleneck in the relational database forcing the use of NoSQL, or a Cloud Provider change)?
- What is the impact of _Doing Nothing_ (Status Quo) compared to the effort of the change?

## Alternatives Considered

- What were "Paths B and C" that the team rejected before proposing "Path A"?
- Why is the chosen option the most suitable today (Cost x Return)?

## Execution and Rollback Plan

- How will the current code base be migrated to the new foundation without _Downtime_?
- What is the acceptable error threshold to abort the change and revert to the previous state?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 01 - RFC: Change Database

## Motivation

MongoDB is slow.

## Alternatives

PostgreSQL is better.

## Execution

We'll do a script on Saturday.
```

> **Rationale**: RFC with zero scientific basis. It disregards that there is no "silver bullet" and attempts to inflict a radical change on the structure without analyzing the cost of data migration and _downtime_.

### ✅ Good Example

```markdown
# 01 - RFC: Decouple Notification Module to Messaging (RabbitMQ)

## Motivation

**Problem**: Current synchronous Email requests via API cause _Timeouts_ (5s) during peak hours (Black Friday), freezing Main App threads.

## Alternatives Considered

1. **Pay for larger instances (Scale Up)**: Rejected for not being financially scalable in the long term.
2. **AWS SQS (Serverless)**: Rejected because the budget is locked and we already have an idle bare-metal server in the infra.
3. **RabbitMQ (Chosen)**: Ensures asynchronicity with zero license cost.

## Execution

- **Shadow**: In the 1st week, RabbitMQ will be enabled but will publish invisible logs while the synchronous code remains active, just to check data consistency.
- **Rollback**: If `AckRate < 99.9%`, we flip the `UseAsyncNotifications` _Feature Flag_ to `false` in the remote dashboard in real-time, without the need for a _Deploy_.
```

> **Rationale**: Mature approach, evaluating financial costs and ensuring that the plan does not cause panic for product managers by having real-time security _Feature Flags_.
