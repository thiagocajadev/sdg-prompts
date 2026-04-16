# 07 - Observability (Logs, Metrics, and Traces)

## System and Business Metrics

- Which critical systemic metrics will be monitored (CPU, RAM usage, RPS, P99 Latency)?
- Which business metrics (KPIs) will be extracted from the transactional system (Sales Balance, Registration Errors)?

## Centralization and Log Standard

- What log aggregation and search tool will be used (e.g., Grafana Loki, ELK Stack, Datadog)?
- What structured format will be used for log ingestion (e.g., JSON)?
- What will NEVER be logged (Sensitive Data/PII, Passwords)?

## Distributed Tracing

- Will the project adopt multi-service request tracking (OpenTelemetry, Jaeger)?
- How will the `CorrelationID` or `TraceID` be propagated in HTTP Headers and Messaging Queues?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 07 - Observability

## Metrics

We'll check the server to see if it doesn't go down.

## Logs

Send `console.log()` to the terminal and we'll read the server file if there's an error.

## Tracing

Create a random ID there.
```

> **Rationale**: Absence of proactive metrics. Waiting for it to "go down" to check the server is unacceptable at a professional level. Loose logs in the terminal are not searchable and violate compliance.

### ✅ Good Example

```markdown
# 07 - Observability

## System and Business Metrics

- **Infra**: P95 Latency < 200ms and Memory Usage on the Grafana dashboard.
- **Business**: Monitoring `OrderCreated` volume in the sales module via Prometheus.

## Logs

- **Standard**: Structured JSON in `Standard Output`.
- **Aggregation**: Datadog (with 15-day retention).
- **Security**: Tax IDs (CPFs) and Credit Cards will be masked at the source (Logger Library).

## Distributed Tracing

- **Propagation**: W3C Trace Context headers throughout the stack.
- **Tool**: OpenTelemetry Collector exporting to Datadog APM.
```

> **Rationale**: Unambiguous definitions that allow for creating real-time alerts. The team will know about the error before the customer opens a ticket. Sensitive data protected by design.
