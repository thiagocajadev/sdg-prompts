# 05 - Design System and UX

## Platforms and Devices

- Which devices will be supported (Web, Desktop, Mobile)?
- Is there a need for a PWA (Progressive Web App)?

## Design System (Tokens)

- **Colors**: 60/30/10 Rule definition (Primary, Secondary, and Contrast).
- **Typography**: Chosen fonts for readability (e.g., Inter, Roboto).

## Accessibility (A11y)

- Does the system meet WCAG compliance (Level AA)?
- How do we ensure contrast and keyboard navigation?

## Micro-interactions

- What animations and visual feedbacks will be standard (Hover, Loading)?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 05 - Design System and UX

## Platforms

Web only for now.

## Design System

Nice colors (Orange and Blue).

## Accessibility

We'll look into it later.
```

> **Rationale**: Vague and neglects accessibility, which is a compliance requirement. "Nice colors" is not a technical definition of tokens.

### ✅ Good Example

```markdown
# 05 - Design System and UX

## Platforms and Devices

PWA for mobile devices and Web Desktop (Responsive First).

## Design System (Tokens)

- **60%**: Neutral Gray (#F8F9FA) - Main background.
- **30%**: Brand Blue (#0056B3) - Buttons and headers.
- **10%**: Contrast Amber (#FFC107) - CTAs and alerts.
- **Font**: Inter (Sans-serif) for body, Montserrat for headings.

## Accessibility (A11y)

- Minimum contrast of 4.5:1 on all text (WCAG AA).
- Full keyboard (Tab) navigation and labels for Screen Readers on all inputs.

## Micro-interactions

Glassmorphism effect on modals with a smooth 0.2s transition (`ease-in-out`).
```

> **Rationale**: Defines specific color tokens (HEX), robust typography, technical accessibility criteria, and interface states.
