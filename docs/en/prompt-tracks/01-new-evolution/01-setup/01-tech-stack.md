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
# 01 - Tech Stack

## Chosen Technologies

Go 1.21, PostgreSQL 15, Redis 7.

## Choice Rationale

Go was chosen for its concurrency performance (Goroutines) required for processing 5k RPS, and PostgreSQL for ACID consistency in critical financial transactions.

## Version Management (LTS)

- **Runtimes**: Only even versions of Node.js (e.g., v20) and Go in its supported versions.
- **Automated Updates**: Dependabot configured via `.github/dependabot.yml` for weekly automatic patch updates.
```

> **Rationale**: Justifies the choice based on non-functional requirements (concurrency and consistency).
