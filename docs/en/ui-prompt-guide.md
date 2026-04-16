# UI Specification Guide — Designing Interfaces for AI Agents

> **Audience:** Technical leads and engineers who need to communicate UI requirements through precise technical specifications.
>
> **Core principle:** AI agents operate as execution engines for provided design tokens and layout contracts. Precision in input density directly correlates with output accuracy.

---

## Why UI Specifications Fail

Vague UI requests produce generic outputs. agents default to the most common training patterns when gaps exist in the specification. Standardizing the following inputs prevents architectural drift:

1. **Visual System** — palette (OKLCH), preset, typography
2. **Structural Content** — sections, component hierarchy, data sources
3. **Execution State** — interactions, lifecycle states (loading/empty/error)
4. **Negative Constraints** — explicit exclusions to prevent logic drift

---

## The UI Prompt Template

Copy and fill this template when requesting any UI work (page, component, or screen):

```markdown
## UI Request

### 1. Context

What is this interface for? Who uses it? What problem does it solve?

- Audience: [developers / consumers / internal ops / etc.]
- Purpose: [data entry / data visualization / marketing / onboarding / etc.]

### 2. Visual Identity

- Palette: [Default Zinc+Blue | Custom: primary=___ secondary=___]
  OR: "Match the existing project palette"
- Preset: [BENTO | GLASS | CLEAN | MONO | NEOBRUTALISM | PAPER]
  OR: "Follow the project preset"
- Typography: [Precision/Dev | Premium/SaaS | Editorial | Bold | Corporate | Startup | Luxury]
  OR: "Use project fonts"
- Theme: [Light only | Dark only | Both (default)]

### 3. Sections & Components

List every visible section in order, top to bottom:

- [ ] Section name — brief description of content
- [ ] Section name — brief description of content

### 4. Interactions & States

- What happens on click/hover/focus?
- Which states must be handled? [Loading | Empty | Error | Disabled]
- Any animations? [None | Subtle entry | Explicit: ___]

### 5. Constraints

- What should NOT be included?
- Fixed breakpoints or layout restrictions?
- Any component or library limitations?

### 6. Reference

- Closest existing page/component to derive from: [page name or "none"]
- Visual reference (if any): [URL or description]
```

---

## Learn by Example

### ❌ Weak Specification (Low Density)

```markdown
Create a dashboard for my SaaS app with cards showing metrics and a table.
Make it look modern and professional with a dark theme.
```

> **Rationale for failure:** Missing palette definition forces arbitrary color selection. "Modern" and "professional" are subjective terms that trigger generic training defaults. Lack of section enumeration results in layout invention. Missing state definitions (loading/empty) creates incomplete execution contracts.

---

### ✅ Strong Specification (High Density)

```markdown
## UI Request

### 1. Context

Analytics dashboard for a B2B SaaS tool.
Audience: internal ops team (power users, 8+ hours/day).
Purpose: monitor pipeline health — volume, conversion rate, and blocked deals.

### 2. Visual Identity

- Palette: Default Zinc+Blue
- Preset: BENTO + GLASS
- Typography: Precision/Dev (JetBrains Mono display, Inter body)
- Theme: Both (dark as default)

### 3. Sections & Components

- [ ] Header — app logo left, user avatar + notifications right
- [ ] KPI Row — 3 metric cards: Total Leads, Conversion Rate, Avg Deal Size
- [ ] Pipeline Chart — horizontal bar chart by stage (Bento cell, full width)
- [ ] Deals Table — sortable columns: Deal, Owner, Stage, Value, Last Activity
- [ ] Sidebar — collapsible, nav links: Overview / Deals / Reports / Settings

### 4. Interactions & States

- KPI cards: hover shows sparkline trend (last 30 days)
- Table: row hover highlights, click opens deal detail drawer
- All data sections: skeleton loading state required
- Empty state for table: "No deals match your filters" + clear filters button

### 5. Constraints

- No pie charts — bar and line charts only
- Table must be sticky-header on scroll
- Sidebar collapsed by default on screens < 1280px
- Do not add onboarding tooltips or modals

### 6. Reference

- Derive from existing DashboardPage component
- Visual reference: Linear issue tracker table density
```

> **Rationale for success:** Palette specification ensures correct OKLCH token generation. Preset usage locks the visual language. Enumerated sections prevent layout invention. Explicit state requirements ensure full lifecycle handling. Negative constraints block common drift patterns. Reference gives the execution engine a starting point and a density target.

---

## Visual Identity Map

Correlating UI requirements with technical standards:

| You want...                       | Preset        | Palette suggestion        | Typography      |
| :-------------------------------- | :------------ | :------------------------ | :-------------- |
| Clean B2B SaaS dashboard          | BENTO + CLEAN | Zinc + Blue (H=250)       | Corporate       |
| Polished, layered premium product | BENTO + GLASS | Zinc + Violet (H=290)     | Premium/SaaS    |
| Developer tool or CLI companion   | MONO          | Zinc monochromatic        | Precision/Dev   |
| Bold marketing or landing page    | NEOBRUTALISM  | High Chroma (Orange H=70) | Bold/Expressive |
| Content-heavy editorial or docs   | PAPER         | Zinc + Amber (H=80)       | Editorial       |
| Modern startup / Next.js app vibe | BENTO + CLEAN | Zinc + Blue (H=250)       | Startup/Modern  |
| Luxury product or high-end brand  | GLASS + PAPER | Custom (ask agent)        | Luxury/Refined  |

---

## The 4 Most Common Drift Patterns (and How to Prevent Them)

| Drift                | How it shows up                         | Prevention in prompt                           |
| :------------------- | :-------------------------------------- | :--------------------------------------------- |
| **Palette drift**    | Random colors, poor light/dark contrast | Always specify Palette or say "match project"  |
| **Layout invention** | Agent adds sections you didn't ask for  | List every section explicitly; add Constraints |
| **State omission**   | No loading/empty/error states           | Enumerate states in Interactions section       |
| **Visual pollution** | Border + shadow + bg-color all together | Specify the preset — it constrains decoration  |

---

## Minimal Prompt (When You're in a Hurry)

When speed matters more than precision, provide at minimum:

```markdown
## UI Request (Minimal)

Context: [1 sentence — what and who]
Palette: [Default | Custom H=___]
Preset: [BENTO | GLASS | CLEAN | MONO | NEOBRUTALISM | PAPER]
Sections: [section 1], [section 2], [section 3]
Must-handle states: [Loading | Empty | Error]
Do NOT include: [constraint 1], [constraint 2]
```

> **Rationale:** Palette + Preset are the two inputs that prevent the most common failures. Everything else can be iterated. Never omit these two.

---

> [!TIP]
> **Technical iteration is continuous.** A well-structured specification achieves high-level accuracy in the first pass. Use targeted refinement prompts for specific sections that require higher density.
