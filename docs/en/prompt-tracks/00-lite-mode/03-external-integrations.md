# 03 - Third-Party Integrations and Sensitive Keys

Third-party APIs and services are the magical bricks that solve 80% of the business logic in Lite products. Instead of reinventing an email sending server or building a billing system in Java, the Landing Page or MVP will consume ready-made APIs (like Resend, Mailchimp, and Stripe).

## Project Connectors and Environment Variables

- Will you send emails? Which provider? And how will React on Vercel call the API without leaking access data on the Frontend? (Hint: Next.js API Routes).
- Payment and Checkout: Which Gateway will we use that doesn't demand PCI compliance scope?
- Is Auth proprietary (e.g., Supabase, Auth0) or will we have Google Login?

## Credentials Mapping (Vault/Env)

- Do NOT store or hardcode ANYTHING in Git. Integrations must use and declare the expected `.env` taxonomy for the project.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Integration

We fire the form to the company's mailchimp. The Front-end does a fetch with the token.
```

> **Rationale**: Severe security danger and lack of maturity. Frontends should not carry Mailchimp keys on the Client-side, otherwise any visitor could grab your Newsletter token and freely delete your customer base.

### ✅ Good Example

```markdown
# SPEC-007: Resend & Stripe Integration

## 1. Context
Integrating transactional emails and payment checkout for the Happy Smile project while maintaining high security.

## 2. Success Metrics
* Zero leaks of API keys in the client-side bundle.
* 100% success rate for webhook signature validation.

## 3. Scope & Scenarios (User Stories)
* **Scenario A (Emails):** User submits contact form, Resend sends email via Serverless endpoint.
* **Scenario B (Checkout):** User pays via Stripe Hosted Checkout, system validates webhook.

## 4. Constraints & Business Rules
* Use Resend API for domain `docs@sorrisofeliz.com`.
* All API keys must be stored in Vercel's `.env` and accessed via API routes.
* Stripe webhooks must validate the `STRIPE_WEBHOOK_SECRET`.

## 5. Out of Scope
* Custom email template builder for the client.
* Direct integration with PayPal or other payment gateways.

## 6. Definition of Done
- [ ] `POST /api/leads` endpoint implemented with Resend.
- [ ] `STRIPE_WEBHOOK_SECRET` validation logic at `/api/stripe-webhook`.
- [ ] Environment variables documented in `.env.example`.
```

> **Rationale**: Maps exactly which third-party fronts are used, how the keys will be called, and protects the Freelancer against chronic Cybersecurity flaws that could ruin the MVP.
