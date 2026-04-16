# Spec-Driven Development Guide (5-Phase Task Cycle)

The **Spec-Driven Guide (SDG)** enforces a standardized lifecycle for every task, ensuring that code is only written after the intent and implementation plan are fully approved.

The cycle follows five mandatory phases: **SPEC → PLAN → CODE → TEST → END**.

> [!TIP]
> **Theoretical DNA**: Want to understand the origins of the SPEC pattern? Read our [**Methodology & References**](../assets/REFERENCES.md) for a breakdown of the core pillars and architectural source material.

---

## 1. Phase: SPEC (The Contract)

**Goal:** Define the implementation contract and verification criteria.

- **Process**: The agent analyzes the request (e.g., via `feat:` or `fix:`) and produces a formal specification.
- **Mandatory Structure (6 Steps)**:
  1. **Context**: Why this is being built and for whom.
  2. **Success Metrics**: Quantifiable results or expected business impact.
  3. **Scope & Scenarios**: User stories and explicit behavior scenarios.
  4. **Constraints & Business Rules**: Eligibility, deadlines, and technical limits.
  5. **Out of Scope**: Explicitly what will NOT be handled to prevent scope creep.
  6. **Definition of Done (DoD)**: Final verification checklist for the task.
- **Mandate**: The agent must halt for explicit Developer approval of the Spec before moving to the Plan.

### Gold Standard Example:
```markdown
# SPEC-001: Subscription Cancellation System (Self-Service)

## 1. Context
Currently, cancellation is handled via chat, leading to high support load. This spec automates the flow via the user panel.

## 2. Success Metrics
* 40% reduction in support tickets.
* 10% retention via downgrade offers.

## 3. Scope & Scenarios
* **Scenario A:** User cancels and loses access at cycle end.
* **Scenario B:** User accepts a discount to stay.

## 4. Constraints
* Only "Premium/Standard" plans. "Enterprise" follows manual flow.

## 5. Out of Scope
* Automatic refunds (processed manually).

## 6. Definition of Done
- [ ] Stripe API integration.
- [ ] Confirmation email sent.
```

---

## 2. Phase: PLAN (The Strategy)

**Goal:** Sequence the Spec into atomic, executable tasks.

- **Process**: The agent drafts a logical roadmap based on the approved Spec.
- **Standards**:
  - Produce a numbered task list.
  - Use the Action Verb + Object pattern (e.g., "1. Create User domain type").
  - **Task Decomposition**: Split complex tasks into sub-tasks to maintain vertical density and prevent context exhaustion.
- **Mandate**: The agent must halt for explicit Developer approval of the Plan.
- **Reasoning Exception**: Autonomous models with built-in reasoning may proceed to Code after validating that the plan reflects the project's engineering rules.

---

## 3. Phase: CODE (The Execution)

**Goal:** Implement the plan following architectural standards.

- **Process**: The agent performs the implementation tasks.
- **Standards**:
  - Follow the **Narrative Cascade** (callers above callees).
  - Adhere to the project's flavor (Vertical Slice, MVC, etc.).
  - Implement only according to the approved Plan (YAGNI).
  - Surface blockers immediately; do not work around them.

---

## 4. Phase: TEST (The Verification)

**Goal:** Ensure the implementation matches the Spec's Verification Checklist.

- **What happens:** The Agent runs/writes tests and verifies each item on the checklist.
- **Agent Behavior:**
  - Writes new tests if the checklist items aren't covered by existing ones.
  - Reports PASS/FAIL for every checklist item.
  - **Refactor Loop:** If a test fails, the agent refactors the code and tries again (up to 3 times before stopping to report a blocker).

---

## 5. Phase: END (The Delivery)

**Goal:** Finalize the task, document changes, and prepare for version control.

- **What happens:** The Agent summarizes the work and updates project logs.
- **Agent Behavior:**
  - Summarizes what was implemented (linking to PLAN tasks).
  - Appends entries to `CHANGELOG.md` following the [Keep a Changelog](https://keepachangelog.com/) standard (`### Added` for features, `### Fixed` for bugs).
  - Proposes a semantic git commit message (e.g., `feat: ...` or `fix: ...`).
  - Offers next steps (Push, Deploy, or start a new task).

---

> [!IMPORTANT]
> The agent only writes code after SPEC and PLAN are approved. This is the mechanism that keeps changes traceable to an explicit decision, not a guess.
