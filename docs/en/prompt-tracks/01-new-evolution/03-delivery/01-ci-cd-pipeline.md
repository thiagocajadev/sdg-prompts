# 01 - CI/CD Pipeline

## Deploy Flow

- What are the pipeline steps? (e.g., `LINT -> TEST -> BUILD -> DEPLOY`)
- What tool do we use? (e.g., GitHub Actions, GitLab CI)

## Approval Requirements (PR)

- [ ] Linter without errors.
- [ ] Tests passing.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 01 - CI/CD Pipeline

## Deploy Flow

Git Push and Docker.

## Approval Requirements

Whoever the creator wants.
```

> **Rationale**: "Git Push" is not a pipeline. "Whoever the creator wants" invalidates technical governance.

### ✅ Good Example

```markdown
# 01 - CI/CD Pipeline

## Deploy Flow

GitHub Actions: `LINT` -> `UNIT-TEST` -> `SAST` -> `DOCKER-BUILD` -> `AWS-DEPLOY`.

## Approval Requirements

- [x] Linter passing.
- [x] 100% of unit tests green.
- [x] 0 critical vulnerabilities in SonarQube.
```

> **Rationale**: Defines technologies (GitHub Actions, SonarQube), clear steps, and rigid requirements for the PR.
