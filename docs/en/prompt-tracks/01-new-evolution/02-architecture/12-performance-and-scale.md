# 11 - Performance and Scale SLAs (Operations)

Distributed systems that do not anticipate traffic contention will suffer "Cascading" unavailability (Timeout Avalanche). The architect needs to define the pain thresholds of their system in the contract.

## Resilience Levers

- **Rate Limiting:** Will the API block clients that call more than `100 req/min`? (Protect your database).
- **Circuit Breakers:** If the partner microservice goes down (e.g., Payment Gateway), how long will our service continue waiting for a response before opening the circuit (e.g., fail-fast < 500ms)?
- **Target Latency (SLOs - Service Level Objectives):** The strict p95 percentile must be `< 250ms`.

## Structural Tactics (Cache vs Sync)

- Will the reading be heavy? What goes to Cache (`Redis/Memcached`) and what will seek Primary Storage directly? Will we use asynchronous queues (Kafka/SQS) for the write model (CQRS)?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Scalability

It will hold up during Black Friday because our cloud is elastic (Autoscaling).
```

> **Rationale**: Failed promise. Scaling up 1,000 Frontend instances to hit a single stressed database will only exhaust the database's connection pool faster (Internal DDoS).

### ✅ Good Example

```markdown
# Performance: Cart Module V2

## P95 Latency (Target)

- List Cart (GET): `< 150ms`.
- Pay Cart (POST): `< 850ms` (Due to external acquirer latency).

## Anti-Avalanche Measures

- Redis Cache for the top 50 best-selling items (10m TTL).
- Stripe HTTP connection will have a **strict 3-second timeout**. If Stripe does not return, the code throws a `PaymentGatewayTimeoutException` saving it to the database as Pending.
- **Rate Limit (API Gateway):** 30 Requests per IP per Minute.
```

> **Rationale**: Defines strict rules and thresholds. The Sysadmin only needs to read this document to correctly configure the Nginx `Rate Limiting` firewall; the back-end developer won't forget to configure the Timeout in their HTTP Client!
