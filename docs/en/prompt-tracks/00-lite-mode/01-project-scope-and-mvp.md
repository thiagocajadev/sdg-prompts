# 01 - Scope and MVP (The Agile Contract / SPEC)

For short, fast-paced projects (MVPs) or Landing Pages, the biggest risk for the Freelancer or lean Squad is not technology, it is **Scope Creep** (the client asking for _just one more little thing_ at the end, consuming your profit margin).

This document establishes the exact boundaries of what will be - and what will NOT be - delivered in the paid project.

## What We Will Do (In-Scope / MVP)

- Executive summary: What problem does the client want to solve? (e.g., "Create a page to collect emails for a digital product launch").
- Raw list of Features:
  - Homepage with static copy.
  - Form capturing Name and Email integrated with Mailchimp.
- Which Screens (UI) will actually be designed? (Page sizes).

## Out-of-Scope

- What will be left for V2/V3 and charged separately in the future? (This shields you against falsely agreed-upon hours).
  - Ex: "We will not build an Admin/Login system for the page right now."
  - Ex: "We will not integrate automatic SMS sending at this time."

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Scope

Build the institutional website for the dental clinic.
```

> **Rationale**: Terrible. In the final week of delivery, the dentist asks: "What about the system to schedule patients on WhatsApp via the website like the competitor has? Didn't you build it?". Since the scope didn't exclude this (Out-of-Scope), the client thinks you failed or will do it for free.

### ✅ Good Example

```markdown
# SPEC-005: Happy Smile Clinic Launch

## 1. Context
The clinic needs a digital presence to run Google Ads campaigns and collect initial consultation leads.

## 2. Success Metrics
* 20% increase in monthly consultation inquiries.
* Lead capture rate > 5% for landing page visitors.

## 3. Scope & Scenarios (User Stories)
* **Scenario A:** Visitor arrives, views services, and fills the WhatsApp/Email lead form.
* **User Story:** As a new patient, I want to contact the clinic via WhatsApp so I can schedule my first visit easily.

## 4. Constraints & Business Rules
* Responsive One-page design.
* WhatsApp links must include pre-filled messages for the receptionist.

## 5. Out of Scope
* Patient management database or login system.
* CMS for changing content/photos.
* Third-party scheduling software integration.

## 6. Definition of Done
- [ ] Landing page deployed to Netlify.
- [ ] Working contact form (Resend/Mailchimp integration).
- [ ] WhatsApp redirection logic.
```

> **Rationale**: Absolute defense. The agency knows they will only need to use Netlify and Email. When the client brings up the Scheduling integration, it will be a new budget.
