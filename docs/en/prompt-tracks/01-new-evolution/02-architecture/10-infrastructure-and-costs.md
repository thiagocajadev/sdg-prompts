# 09 - Infrastructure and Costs (FinOps)

Staff-level architecture understands that code costs money to run. Designing a cloud microservices system without understanding the underlying economics and its _Unit Economics_ is a serious architectural failure.

## Unit Economics and Sizing

- **Cost per Transaction:** How much does it cost, in terms of infrastructure, for the company to process 1 new Order/Customer in this module?
- **Scale Estimation:** Given the expected traffic for the next 12 months, what is the estimated monthly _TCO (Total Cost of Ownership)_ in BRL/USD?
- **Managed Dependencies:** Will we use an expensive managed database (e.g., RDS Aurora) or something fixed (e.g., EC2 + Docker)? Does the SLA justify the premium price paid?

## Budget Protection

- **Billing Alarms:** What are the upper thresholds defined in the cloud? (e.g., If the queue bottlenecks and climbs to $1,000 in a day of uncontrolled lambdas, who is notified via Slack?)
- **Hidden Costs:** Was there an accounting for Network Outbound Traffic (Data Transfer Out), storage of giant Logs, and daily Database Snapshots?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Infrastructure

We'll use AWS K8S (EKS) because the team is already familiar with it and it's the current industry standard. It handles everything we need to send.
```

> **Rationale**: Wasteful. They don't even mention what "Everything we need" is. An EKS cluster costs > $70/month just for the _Control Plane_ while empty. Building on it to process 10 requests per day is financial amateurism disguised as scalability.

### ✅ Good Example

```markdown
# Infrastructure: Invoice Generation Module (FinOps)

- **Calculated Unit Cost:** We will use AWS Lambda. Each invoice (1 req + 2 database connections + s3) will last 800ms at 512MB RAM. Estimated at $0.0005 per invoice.
- **Estimated Monthly TCO:** For 1 million expected invoices/month in Q4, the bill for this feature will be approx. $15 USD (Serverless).
- **Budget Protection:** A $50/month Billing Alarm created on the `feature:invoice` tag. If it exceeds this, it's a sign of a bug in the infinite retry code. It will notify `#dev-alerts`.
```

> **Rationale**: Executive perfection. The developer proved they sized things, understood the demand-based Serverless payment model, and already prepared the safeguard against billing anomalies before spending a single cent of the company's money.
