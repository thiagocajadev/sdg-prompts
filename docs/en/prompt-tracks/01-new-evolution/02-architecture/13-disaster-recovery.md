# 12 - Disaster Recovery Plan (DR / BCP)

Critical failures in cloud providers occur annually. "DROP TABLE" and _Ransomware_ incidents occur every hour. Designing from an SRE perspective requires us to document how the _software comes back to life_ after losing an entire region.

## Critical Rescue Objectives

- **RTO (Recovery Time Objective):** Promised time to C-Level to bring Core systems back online (e.g., < 4 hours)?
- **RPO (Recovery Point Objective):** How many minutes or hours of sales data the company is willing to "lose" if the Main DB goes down? (Optimal Backup Point).

## Multi-Zone and Cold Redundancy

- How does your infrastructure respond to the failure of an entire _Availability Zone (AZ)_?
- Do the "Terraform Infrastructure as Code (IaC)" have the state to bring up another datacenter in the _US-East-2_ Zone if _US-East-1_ fails permanently (Cold Architecture / Standby)?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Disaster Recovery (DR)

Our MySQL database takes a snapshot on AWS every day at midnight. And we have Terraform done for the K8S Cluster.
```

> **Rationale**: If the region goes down at noon, you've just thrown _12 hours of morning revenue in the trash_ (Unacceptable to the CEO). You're covering the minimum, but how does the team bring up this Terraform when the alert goes off?

### ✅ Good Example

```markdown
# "Transactions V2" Module Recovery

- **RTO (Recovery Target):** `Max 2 Hours` – Aurora database uses Auto-Failover (< 60 seconds). The ECS cluster has Multi-Zonal Autoscaling and will bring up containers in _eu-west-1b_ if _1a_ goes down.
- **RPO (Data Acceptance):** `Max 5 Minutes` – Database has Continuous Backup (AWS PITR - Point-in-Time Recovery). Worst-case scenario, we lose only the transactional logs from the last 4.9 minutes.
- **Chaos Simulations:** Performed annually through "Game Day" by the SRE and documented in `Incident Postmortems`.
```

> **Rationale**: The document reassures investors and C-Level leadership that corporate SLA laws and short RPOs were properly incorporated into the software before it was built and priced.
