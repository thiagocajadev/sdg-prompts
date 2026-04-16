# 02 - Local Environment

## Prerequisites

- What does the developer need to have installed (e.g., Docker, Taskfile, Make)?
- Minimum version of the tools.

## How to Run

1.  [ ] Clone the repo.
2.  [ ] Install dependencies.
3.  [ ] Start the containers.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Local Environment

## Prerequisites

Docker and Python.

## How to Run

Run docker-compose up.
```

> **Rationale**: What if Docker Compose fails? Where are the necessary environment variables (.env)?

### ✅ Good Example

```markdown
# SPEC-013: Local Developer Experience (DX)

## 1. Context
Standardizing the local environment to eliminate "works on my machine" syndrome.

## 2. Success Metrics
* Developer setup time reduced to under 10 minutes.
* 100% consistency for shared Docker images.

## 3. Scope & Scenarios
* **Action:** Copy `.env.example`, run `make setup`, verify at `localhost:8080`.
* **Prerequisites:** Docker 24+, Python 3.11, Make 4.3+.

## 4. Constraints & Business Rules
* All environment variables must have defaults in `.env.example`.
* Use `make` targets instead of long script commands.

## 5. Out of Scope
* Setting up external Cloud provider credentials.
* CI/CD runners setup.

## 6. Definition of Done
- [ ] `Makefile` setup target verified.
- [ ] Health check endpoint access confirmed.
```

> **Rationale**: Provides minimum versions, clear initial configuration steps (.env), and a final verification test.
