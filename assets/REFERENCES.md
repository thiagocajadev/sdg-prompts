# Origins and References: The SPEC Pattern

This document details the methodological DNA behind the **Standard Product Spec** (or Functional Spec) structure adopted in this guide. Our approach combines best practices from companies that prioritize **writing before execution**.

---

## 🏗️ Pillars of Ambiguity Reduction

The SPEC structure is not just a template; it is a critical thinking framework based on 6 steps:

### 1. Context (The "Why")
*   **Concept**: *Outcome-over-Output*.
*   **Philosophy**: A Spec should not be a task list, but a business argument.
*   **Deep Dive**:
    *   [The Pragmatic Engineer: How Stripe Builds Product (Part 1)](https://newsletter.pragmaticengineer.com/p/stripe)
    *   [The Pragmatic Engineer: How Stripe Builds Product (Part 2)](https://newsletter.pragmaticengineer.com/p/stripe-part-2)
    *   [Lenny's Newsletter: How Linear builds product](https://www.lennysnewsletter.com/p/how-linear-builds-product)

### 2. Success Metrics (The "Impact")
*   **Concept**: Measurability and ROI.
*   **Philosophy**: If there is no clear success metric (e.g., efficiency gains), the Spec is considered "empty".
*   **Deep Dive**:
    *   [Stripe Operating Principles & Writing Culture](https://www.tryexponent.com/blog/stripe-operating-principles)

### 3. Scope & Scenarios (The "What")
*   **Concept**: Evolution of traditional *User Stories* with a focus on *Jobs-to-be-Done* (JTBD).
*   **Philosophy**: Focuses on the real user scenario and the complete journey (POC vs MVP).
*   **Deep Dive**:
    *   [Christensen Institute: Jobs-to-be-Done Theory](https://www.christenseninstitute.org/theory/jobs-to-be-done/)
    *   [Intercom: Jobs-to-be-Done Discussion](https://jobs-to-be-done.com/jobs-to-be-done-discussion-with-intercom-f57987239569)
    *   [Strategyn: History of JTBD](https://strategyn.com/jobs-to-be-done/history-of-jtbd/)
    *   [GoPractice: JTBD Theory and Frameworks](https://gopractice.io/product/jobs-to-be-done-the-theory-and-the-frameworks/)

### 4. Constraints & Business Rules (The "Rules")
*   **Concept**: Logical limits and technical guardrails.
*   **Philosophy**: Establishes the tracks where the solution must run to ensure safety and consistency.
*   **Deep Dive**:
    *   [Stripe Atlas: Scaling Engineering and Decision Making](https://stripe.com/guides/atlas/scaling-eng)

### 5. Out of Scope (The "Boundaries")
*   **Concept**: Scope Management and *Lean Development*.
*   **Philosophy**: Defining what will **NOT** be done avoids wasting energy and prevents *scope creep*.
*   **Deep Dive**:
    *   [Agile Manifesto Principles](https://agilemanifesto.org/principles.html)

### 6. Definition of Done (The "Check-point")
*   **Concept**: Quality Contract.
*   **Philosophy**: A non-negotiable contract that ensures "Done" is technical, functional, and visual.
*   **Deep Dive**:
    *   [Scrum.org: What is the Definition of Done?](https://www.scrum.org/resources/what-definition-done)
    *   [Agile Alliance: Definition of Done Glossary](https://agilealliance.org/glossary/definition-of-done/)
    *   [The Scrum Guide (2020)](https://scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-US.pdf)
