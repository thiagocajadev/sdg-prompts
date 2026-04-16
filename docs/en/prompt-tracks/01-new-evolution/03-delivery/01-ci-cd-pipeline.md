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
# SPEC-018: High-Stakes CI/CD Pipeline

## 1. Context
Automating the deployment flow to eliminate manual errors and ensure code quality in production.

## 2. Success Metrics
* Deployment failure rate under 1%.
* Pipeline execution time under 10 minutes.

## 3. Scope & Scenarios
* **Flow:** `LINT` -> `UNIT-TEST` -> `SAST` -> `DOCKER-BUILD` -> `AWS-DEPLOY`.
* **Tool:** GitHub Actions.

## 4. Constraints & Business Rules
* 100% of unit tests must be green for build initiation.
* Zero critical vulnerabilities in SonarQube (SAST).

## 5. Out of Scope
* Automatic rollback logic in this phase (manual rollback only).
* Deploying to regions outside `us-east-1`.

## 6. Definition of Done
- [ ] GitHub Actions workflow file created.
- [ ] SonarQube integration verified.
- [ ] Successful deploy to staging.
```

> **Rationale**: Defines technologies (GitHub Actions, SonarQube), clear steps, and rigid requirements for the PR.
