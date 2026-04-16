# 01 - Tech Stack

## Chosen Technologies

- **Language**: [e.g., Go, TS, C#]
- **Framework**: [e.g., FastAPI, React, Gin]
- **Database**: [e.g., PostgreSQL, Redis]

## Choice Rationale

- Why did we choose these technologies over others?
- What are the pros and cons?

## Version Management (LTS) and Dependencies

- Are the chosen frameworks and runtimes Long Term Support (LTS) versions?
- What is the strategy for continuous updates and vulnerability mitigation (e.g., Dependabot, Renovate)?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 01 - Tech Stack

## Chosen Technologies

Python and MySQL.

## Choice Rationale

Because it's what the team knows how to use and it's popular.

## Version Management (LTS)

We'll use the newest version or whatever works.
```

> **Rationale**: Popularity does not justify critical architecture decisions. Where is the trade-off?

### ✅ Good Example

```markdown
# SPEC-012: Financial Engine Stack

## 1. Context
Choosing the foundation for a financial system requiring high concurrency (5k RPS) and ACID consistency.

## 2. Success Metrics
* Zero consistency errors in financial transactions.
* Maintain 5k RPS with sub-second latency.

## 3. Scope & Scenarios
* **Stack:** Go 1.21 + PostgreSQL 15 + Redis 7.
* **Rational:** Goroutines for concurrency, Postgres for ACID.

## 4. Constraints & Business Rules
* Use only LTS versions of Node.js (v20).
* Weekly automated patch updates via Dependabot.

## 5. Out of Scope
* Using NoSQL databases for core financial records.
* Manual dependency management.

## 6. Definition of Done
- [ ] Go/Postgres service boilerplate complete.
- [ ] `.github/dependabot.yml` configured.
```

> **Rationale**: Justifies the choice based on non-functional requirements (concurrency and consistency).
