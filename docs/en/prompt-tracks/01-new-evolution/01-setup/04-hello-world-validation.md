# 04 - Hello World Validation

## What Was Validated?

- [ ] The app is running.
- [ ] The first endpoint has been exposed.
- [ ] The first test is passing.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 04 - Hello World Validation

## What Was Validated?

Everything is fine, the app started locally.
```

> **Rationale**: How do you prove success? Where is the healthcheck log?

### ✅ Good Example

```markdown
# 04 - Hello World Validation

## What Was Validated?

- [x] 200 OK response on the `/health` endpoint.
- [x] Startup log displays "Server listening on port 8080".
- [x] The `npm test` command successfully executed the first basic test.
```

> **Rationale**: Provides concrete and traceable evidence of successful initialization.
