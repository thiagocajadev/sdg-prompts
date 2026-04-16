# 08 - Technical Documentation and Contracts

## API Contracts (Public Specs)

- How will endpoints and integrations be documented (Swagger, OpenAPI 3.0, GraphQL Schema)?
- Will the documentation be generated dynamically via code (Annotations) or manually (separate YAML files)?

## Architectural Decision Records (ADRs)

- Does the project use Architectural Decision Records (ADRs) to record the "why" behind each technological choice that should not be altered (Immutable)?
- In which directory will the ADRs live (e.g., `docs/adrs/`)?

## Operation Guides and Runbooks

- Where will the _Runbook_ on how to start the project live (Initial setup for new Devs)?
- Are there _Playbooks_ on what to do if the main database goes down or if an external service is offline (Operational Resilience)?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 08 - Technical Documentation

## Contracts

The backend API will have a Postman collection that we'll share on Slack.

## Decisions

We always decide orally in the Daily.

## Guides

Just read the code; it's "self-documenting".
```

> **Rationale**: Code does not document obsolete business rules or external contracts. Relying on temporary Slack messages is anti-architecture.

### ✅ Good Example

```markdown
# 08 - Technical Documentation

## API Contracts

- **Standard**: OpenAPI 3.1
- **Generation Engine**: Swaggo (Go annotations) auto-generated in the build pipeline and served at `/swagger/index.html`.
- **Automatic Validation**: _Spectral Linter_ will run in the CI ensuring the use of HTTPS and error payload description.

## Architectural Decision Records (ADRs)

- **Location**: Dedicated folder `docs/decisions/`.
- **Workflow**: No central library (ORM, Gateway) or new database should be added without a PR completing the corresponding ADR.

## Operational Guides (Runbooks)

- **Main Document**: `/README.md` with local script (`docker compose up`) and documented environment variables.
- **Troubleshooting**: `docs/runbooks/db-failover.md` describing database restoration and health check commands.
```

> **Rationale**: Prepares the project for team scalability, smooth _Onboarding_, and is forget-proof. The auto-generated Swagger engine does not suffer from synchronization issues with commits.
