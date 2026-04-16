# 03 - Architecture and Technical Design (Architecture & Design)

## API-First (Contracts and Envelopes)

- **Exposed Endpoints:** Routes, Verbs (GET/POST/PUT/PATCH/DELETE), or gRPC methods.
- **Request Payload:** Expected input format.
- **Response Schemas (Envelopes):** The unified success format and, crucially, the unified standard for **Business Error** or Validation messages.

## Data Modeling (Data Models / Persistence)

- **Entities and Relationships:** Which tables/collections should be created/altered? (ER Diagram or Mermaid).
- **Migration Strategy:** Will we need to migrate data from legacy or just insert columns (Add-only)? What about indexes for read queries?

## External Integrations (Third-parties)

- **Suppliers/Vendors:** Does the feature call AWS S3, Stripe, Slack, etc.?
- **Rate Limits & Fallback:** How does the feature handle the failure of this third-party API?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# API and DB

Create a POST /upload route.
Save the PDF in the Docs table.
```

> **Rationale**: Vague and subject to free interpretation (every Dev will do it differently). It doesn't show possible HTTP statuses or where the actual large binaries will live.

### ✅ Good Example

```markdown
# SPEC-003: Workspace Report API

## 1. Context
Backend foundation for the Financial Report Exporting feature. Provides endpoints for generating and fetching reports.

## 2. Success Metrics
* 99.9% API uptime for the report creation flow.
* Report generation latency under 2 seconds for 90% of requests.

## 3. Scope & Scenarios (User Stories)
* **Scenario A:** Agent triggers POST request to generate report.
* **User Story:** As a developer, I want a standard error format ([RFC 7807](https://datatracker.ietf.org/doc/html/rfc7807)) for easy troubleshooting.

## 4. Constraints & Business Rules
* **Schema:** `reports (id, type, target_month, status, file_url)`.
* **Constraint:** `UNIQUE (workspace_id, target_month)` to prevent duplicates.
* **Storage:** Physical files stored in S3 Bucket.

## 5. Out of Scope
* Report deletion or archival API.
* Direct SQL injection/modification of report status.

## 6. Definition of Done
- [ ] POST endpoint implemented with RFC 7807 validation.
- [ ] S3 streaming logic.
- [ ] Table unique constraints applied.
```

> **Rationale**: Puts an end to endless PR discussions. The Front-End Dev knows exactly what payload to expect (even if the backend hasn't coded anything yet). The DBA understands the indexes that will be generated.
