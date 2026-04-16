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
# Happy Smile API Integrations

## Transactional Emails (Form to the Clinic)

- **Provider:** We will use the [Resend API](https://resend.com) on the client's domain `docs@sorrisofeliz.com`.
- **Secure Magic Routes:** We created a Serverless endpoint (Edge API On Vercel) at the `POST /api/leads` route. The React client form calls this endpoint without any tokens. The underlying Node.js will consume the shielded token via Vercel's `.env` and inject it into Resend: `RESEND_API_KEY`.

## Checkout (Planned)

- **Gateway:** When clients pay for direct consultations (Stripe Hosted Checkout), the publishable variables will be inserted into NEXT*PUBLIC_PUBLISHABLE_KEY, but \_webhooks* will return with cryptographic signature `STRIPE_WEBHOOK_SECRET` validated at `/api/stripe-webhook`.
```

> **Rationale**: Maps exactly which third-party fronts are used, how the keys will be called, and protects the Freelancer against chronic Cybersecurity flaws that could ruin the MVP.
