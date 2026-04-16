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
# 02 - Architectural Styles and Design Patterns

## Architectural Style (Macro)

**Modular Monolith**. We will start bundled to reduce network costs and DevOps complexity, separating contexts via strict internal packages.

## Chosen Patterns

Hexagonal Architecture with Vertical Slices for modules. Business logic via Result Pattern.

## Implementation Patterns

Errors will be handled via the Envelope Pattern (Result<T>), avoiding pure exceptions for business flow control.
```

> **Rationale**: Explicitly addresses the macro trade-off (Modular Monolith vs Microservices) and defines specific, testable code choices.
