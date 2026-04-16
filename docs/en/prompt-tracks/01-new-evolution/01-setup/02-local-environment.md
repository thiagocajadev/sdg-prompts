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
# 02 - Local Environment

## Prerequisites

Docker 24+, Python 3.11, Make 4.3+.

## How to Run

1. Copy .env.example to .env.
2. Run `make setup` to download images and run migrations.
3. Test access at `localhost:8080/health`.
```

> **Rationale**: Provides minimum versions, clear initial configuration steps (.env), and a final verification test.
