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
# 03 - Integrations, APIs, and Communication

## Contracts and Interfaces (Synchronous)

Public exposure via **GraphQL** (using BFF for mobile payload limitation). Internal Service-to-Service communication via **gRPC** ensuring strong typing and low latency.

## Entry Gates and Routing

All external traffic passes through an **API Gateway** responsible for TLS termination, Rate Limiting, and JWT token validation (Auth offloading).

## Asynchronous and Event-Driven

The checkout finalization string will emit an "OrderCreated" event via **RabbitMQ**. The Notification service will act as a subscriber to dispatch emails without blocking the user's HTTP response (temporal decoupling).
```

> **Rationale**: Defines objective protocol choices based on client profile (GraphQL vs gRPC), protects the core domain using API Gateways, and applies Event-Driven Architecture (EDA) for secondary background flows.
