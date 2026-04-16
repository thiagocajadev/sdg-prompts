# 01 - Modernization Approach

## Chosen Strategy

- [ ] Rehost, [ ] Refactor, [ ] Rearchitect, etc.

## Coexistence Pattern

- How will the legacy system talk to the new one?

## Security in Transition

- How will credentials be shared (Single Sign-On)?
- How do we ensure that the weaker system (Legacy) does not compromise the new one?

## Interface Modernization (UX/UI)

- Will we keep the legacy UI or migrate to a new Design System?
- How will the visual transition be for the end user?

## AI Opportunities in Legacy

- How can AI automate manual processes of the old system?
- Data extraction (OCR/LLM) from legacy documents.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 01 - Modernization Approach

## Interface Modernization

Make the frontend more modern.

## AI Opportunities

Put a chat in the old system.
```

> **Rationale**: "Modern" is subjective. "Chat in the old system" might be an error if the backend is not stable enough to provide reliable data to the AI.

### ✅ Good Example

```markdown
# 01 - Modernization Approach

## Interface Modernization (UX/UI)

Migration to the new Design System in React, replacing Delphi screens via controlled iframe (Progressive Isolation).

## AI Opportunities

Implement an Agent via MCP for automated data extraction from old invoices that do not have an API.
```

> **Rationale**: Defines interface technologies (React, iframe) and a real AI use case (MCP/OCR) to "save" inefficient legacy processes.
