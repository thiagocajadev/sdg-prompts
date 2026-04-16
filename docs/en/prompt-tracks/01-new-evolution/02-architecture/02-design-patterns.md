# 02 - Architectural Styles and Design Patterns

## Architectural Style (Macro)

- **Chosen Approach**: [e.g., Modular Monolith, Microservices, Serverless]
- **Justification**: Why did we choose this approach? If microservices, why not start with a modular monolith?

## Code Design Patterns (Micro)

- **Software Architecture**: [e.g., Clean Arch, Hexagonal, Vertical Slices]
- **Domain Modeling**: [e.g., DDD, Rich Domain Models, Result Pattern]

## Implementation Patterns

- **Flow Control and Errors**: How do we handle errors? (e.g., `Envelope Pattern`, `if err != nil`)

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Architectural Styles and Design Patterns

## Architectural Style (Macro)

We will use microservices to scale better in the future.

## Chosen Patterns

We will use programming best practices.

## Implementation Patterns

The code will be clean and commented.
```

> **Rationale**: Justifying "microservices" based on future scale is speculative (Premature Optimization). "Best practices" and "clean" are vague and subjective.

### ✅ Good Example

```markdown
# SPEC-015: Modular Monolith Foundation

## 1. Context
Designing the macro and micro architecture for a system requiring speed of delivery and future scalability.

## 2. Success Metrics
* Module decoupling that allows 1-hour "extraction" to microservices.
* 100% adherence to the Result Pattern for error handling.

## 3. Scope & Scenarios
* **Style:** Modular Monolith with Vertical Slices.
* **Pattern:** Hexagonal Architecture (Ports and Adapters).

## 4. Constraints & Business Rules
* No pure exceptions for business flow control (use Result<T>).
* Direct database calls from the UI/Controller are strictly forbidden.

## 5. Out of Scope
* Implementing event sourcing or eventual consistency.
* Designing for multi-region active-active clusters.

## 6. Definition of Done
- [ ] Architecture diagram approved.
- [ ] Result Pattern utility implemented.
```

> **Rationale**: Explicitly addresses the macro trade-off (Modular Monolith vs Microservices) and defines specific, testable code choices.
