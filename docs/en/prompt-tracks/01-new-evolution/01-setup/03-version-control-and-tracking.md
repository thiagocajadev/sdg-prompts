# 03 - Version Control and Management

## Branch Strategy (Versioning)

- What standard flow will be adopted (GitHub Flow, GitFlow, Trunk-Based)?
- What are the naming rules for creating new branches?

## Commit Standard

- Will the project adopt _Conventional Commits_?
- Will there be passive protection (**Developer review**) or active protection (Husky/Commitlint before push)?

## Traceability and Task Management

- What is the official tracking tool (Jira, Linear, Azure DevOps)?
- How does the PR (Pull Request) link to the business task described in the specification?
- What is the status transition rule for cards when the code is merged?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 03 - Version Control and Management

## Branch Strategy

We'll use basic Git. Create a branch with the functionality and then throw it into master.

## Commit Standard

Write something understandable, e.g., "uploading login screen fixes" and "wip".

## Traceability

When the task is finished, notify management on Slack and move the Trello card to Done.
```

> **Rationale**: Total lack of governance and traceability. In a short time, the repository will have severe integration conflicts, impossibility of generating automatic _Changelogs_, and management will not know which code in production belongs to which specification.

### ✅ Good Example

```markdown
# 03 - Version Control and Management

## Branch Strategy (Versioning)

- **Flow**: GitHub Flow (Simplified Trunk-Based).
- **Naming**: Mandatory to follow the pattern and the spec ID (e.g., `feat/AUTH-102-implement-oauth`, `fix/AUTH-105-token-timeout`).

## Commit Standard

- **Standard**: Strict compliance with _Conventional Commits_ (`feat:`, `fix:`, `chore:`, `refactor:`).
- **Guarantee**: Use of `Husky` + `Commitlint` blocking non-standard commits via _pre-commit_.

## Traceability and Task Management

- **Tracking**: Linear (Issue Tracker).
- **Linking**: Every PR must contain the tracking ID in the title (e.g., "[AUTH-102] Implement OAuth via Google").
- **Workflow**: GitHub integration with Linear moves tickets to `In Review` when the PR is opened and to `Done` upon _Merge_.
```

> **Rationale**: Creates a perfect audit trail (_End-to-End_). Every line of code changed is linked to a business decision and PR approval. Furthermore, semantic releases can be published 100% automatically by the CI/CD based on _Conventional Commits_.
