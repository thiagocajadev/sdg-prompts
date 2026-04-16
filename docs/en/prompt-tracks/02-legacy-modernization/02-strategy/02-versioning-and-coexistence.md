# 02 - Versioning and Coexistence Strategy

## Versioning and Code Freeze

- What will be the repository strategy? (Create a NEW repository from scratch or create a `modernization` branch in the current repository?)
- Will there be a `Code Freeze` (pause on new features) in the legacy system during modernization? If not, how will new legacy features sync with the new architecture?

## Traffic Routing (Strangler Fig)

- How will users access the new system? (Gradually via **Feature Flags**, or a overnight **Big Bang** migration)?
- Will the **API Gateway** or **Load Balancer** be configured to direct specific calls (e.g., `/api/v2/orders`) to the new system and the rest to the legacy one?

## User Interface (Micro-frontends / iFrames)

- If the interface also changes, will the new interface screen coexist in the legacy window via `<iframe>`, Federated Modules (Webpack), or will the user transition between tabs/domains (e.g., `legacy.app.com` -> `app.com`)?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Versioning and Coexistence

## Versioning

We'll write the code in a separate repository. The maintenance team continues in the other one.

## Routing

Once finished, we switch the DNS to the new server on a Saturday night.
```

> **Rationale**: The famous "Big Bang." Statistically, the chance of a Big Bang failure is massive, resulting in the classic "Rollback Sunday." Two teams running in parallel without a bridge causes divergence of rules in production.

### ✅ Good Example

```markdown
# 02 - Versioning and Coexistence

## Versioning and Code Freeze

- Separate repositories.
- **No Code Freeze**: However, the maintenance team _must_ notify the modernization squad if any Legacy DB Model undergoes an `.alter table`.

## Routing (Strangler Fig)

- **Strangler Fig Pattern** standard with proxy (NGINX/Kong).
- Traffic will be transferred endpoint-by-endpoint. Once `v2/sales` in the new language is completed, Kong starts routing 15% of that sales traffic to the new server while keeping the rest (85%) of the traffic on PHP.

## Coexistence

- The user will feel as if they are in the same system. The Legacy portal header will have the "Sales" button pointing to the new micro-frontend via Cloudfront.
```

> **Rationale**: "Thin Slices" approach. Failure risk is isolated to smaller endpoints, allowing modernization to deliver value in the first week of deployment rather than only in 6 months during a single event.
