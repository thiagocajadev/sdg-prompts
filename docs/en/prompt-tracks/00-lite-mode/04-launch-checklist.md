# 04 - Launch Checklist

Launching an MVP/Landing Page quickly doesn't mean just throwing files onto the server. Your client expects polish, speed, and impeccable SEO on WhatsApp. This is the final gateway, your personal one-day Quality Assurance.

## Domain Setup and Security

- [ ] Is the custom domain linked on Vercel/Netlify/Cloudflare?
- [ ] Is SSL (HTTPS) active (Green Padlock)?
- [ ] Did you try accessing without 'www' (e.g., `happy-smile.com`) and was the traffic correctly redirected to prevent Google penalties (Duplicate Content)?
- [ ] Reference: # 01 - Scope and MVP (The Agile Contract / SPEC)

## SEO and Social Sharing (OpenGraph)

- [ ] Have basic `Meta Tags` (Title, Description) been declared for Google?
- [ ] Are `Og:Image` images hosted so that when the link is posted on WhatsApp or Instagram, the "site thumbnail" appears beautiful and resized?
- [ ] Is there a real `Favicon` or did you forget the default Vercel logo orbiting?

## Live Integrations & Core Web Vitals Performance

- [ ] Have the Google Analytics (GA4) and Meta Pixel (Facebook) tags been injected so Marketing doesn't complain later?
- [ ] Does the Chrome Lighthouse score hit 90+ in Performance and Accessibility in a cold Mobile audit? (Use WebP, cut massive JS).
- [ ] Did the test with real form data ("Mr. John Smith, john@gmail.com") actually land in the client's inbox without a SPAM flag?

---

> **Rationale**: Executing this checklist crowns the relentless quality of the Freelancer/Agency. Your project is only complete when all the boxes above have been checked positively. Nothing sells a fast sprint better than a link without loose error edges and a thumbnail that creates visual pride for the client.
