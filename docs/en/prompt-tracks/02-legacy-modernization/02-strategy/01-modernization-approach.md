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
# SPEC-008: Legacy Progressive Isolation

## 1. Context
Mainframe/Delphi legacy system needs UI modernization without stopping the operation. We will use an iframe-based isolation strategy.

## 2. Success Metrics
* 30% increase in user speed for core flows in the new UI.
* Zero data loss during legacy-to-modern synchronization.

## 3. Scope & Scenarios (User Stories)
* **Scenario A:** Legacy Delphi screens are gradually replaced by new React views via controlled iframes.
* **Scenario B:** An AI Agent extracts data from non-API invoices via OCR/MCP.

## 4. Constraints & Business Rules
* Use the project's new Design System for all React views.
* Iframe isolation must be controlled via a common authentication layer (SSO).

## 5. Out of Scope
* Complete rewrite of the legacy database schema.
* Modernizing legacy reporting tools that are scheduled for decommission.

## 6. Definition of Done
- [ ] React/Delphi iframe communication protocol defined.
- [ ] Agent MCP integration for invoice data extraction.
- [ ] SSO validation for legacy-iframe bridge.
```

> **Rationale**: Defines interface technologies (React, iframe) and a real AI use case (MCP/OCR) to "save" inefficient legacy processes.
