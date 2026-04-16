# 03 - Integrations, APIs, and Communication

## Contracts and Interfaces (Synchronous)

- **External APIs**: [e.g., REST for Web, GraphQL for Mobile/Complex UIs]
- **Internal Communication (Service-to-Service)**: [e.g., gRPC via Protobuf, isolated REST calls]

## Entry Gates and Routing

- **API Gateways / BFF**: [e.g., AWS API Gateway for Rate Limiting and Central Auth, BFF for aggregating mobile payload]

## Asynchronous and Event-Driven

- **Message Brokers**: [e.g., RabbitMQ, AWS SQS, Apache Kafka]
- **Asynchronous Use Cases**: Which flows shouldn't block the user's main request? (e.g., sending emails, processing payments). Detail the _Publishers_ and _Subscribers_.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 03 - Integrations, APIs, and Communication

## Contracts and Interfaces (Synchronous)

Our API will be REST and services will talk via HTTP.

## Asynchronous and Event-Driven

We will use RabbitMQ for heavy background tasks.
```

> **Rationale**: It doesn't specify why temporal failures in HTTP are acceptable for internal services, nor details the technological reasoning for RabbitMQ. It completely ignores Gateway layer concepts.

### ✅ Good Example

```markdown
# SPEC-016: Unified Communication Strategy

## 1. Context
Defining how internal and external components communicate to ensure security and speed.

## 2. Success Metrics
* Internal latency under 10ms for 95% of service-to-service calls.
* Zero unauthorized access to core APIs.

## 3. Scope & Scenarios
* **Sync:** GraphQL for clients, gRPC for services.
* **Async:** RabbitMQ for "OrderCreated" notifications.

## 4. Constraints & Business Rules
* Mandatory API Gateway for TLS and Rate Limiting.
* Webhook signatures must be validated using cryptographic secrets.

## 5. Out of Scope
* Implementing a custom service mesh like Istio.
* Managing legacy SOAP or XML-based integrations.

## 6. Definition of Done
- [ ] Gateway authentication layer verified.
- [ ] RabbitMQ publisher/subscriber logic scaffolded.
```

> **Rationale**: Defines objective protocol choices based on client profile (GraphQL vs gRPC), protects the core domain using API Gateways, and applies Event-Driven Architecture (EDA) for secondary background flows.
