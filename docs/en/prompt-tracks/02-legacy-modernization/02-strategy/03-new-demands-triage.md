# 03 - New Demands Triage (Triage Matrix)

A legacy modernization creates a "Tug of War" between the team migrating the system and the Product (PMs) / Sales area that keeps requesting _new features (New Buttons)_ all the time. The Decision Tree below shields the system to avoid building eternal "trash" on the old platform.

## Decision Support Tree (Where to Develop)

For each new "Epic" requested during the migration, the Tech Lead must apply the following questionnaire:

1. **Does the requested feature touch modules that will be decommissioned in less than 6 months?**
   - **Yes:** Reject in the Legacy system, unless it is Critical/Legal Compliance (Bugfix/Tax). Only perform workarounds or advance the schedule in the New Architecture.
2. **Is it a functionality completely independent of the current core?** (e.g., A new SMS sending module)
   - **Yes:** Build **100% in the New Ecosystem** (Microservice or V2) and integrate via API Bridge/Strangler Fig so that Legacy screens can call it without cluttering the internal logic.
3. **Does the Cost x Benefit require it to be in the Legacy system?**
   - Injecting into the spaghetti code will take X hours, but we'll refactor it regardless. How can we deliver quickly _now_ without blocking future database migrations? (e.g., Add-only table extension).

---

## Learn by Examples

### ❌ Bad Example

```markdown
# Matrix

Every new button goes into the new system, and the old system only gets bug fixes.
```

> **Rationale**: Too simplistic. How will the user use something in the "new" system if Single Sign-On hasn't been created yet? An automatic "no" will generate unsustainable friction with the PM, who will demand it go into the Legacy system to serve the customer tomorrow.

### ✅ Good Example

```markdown
# Feature Triage: "Loyalty and Cashback Module"

- **Request:** Massive new module.
- **Legacy Analysis:** The PHP 5 Legacy system will make complex calls to calculate cashback.
- **Decision (Strangler Fig):** The Cashback calculation will be built in the NEW architecture (Python V2) as an isolated endpoint (`/api/v2/cashback`).
- **Integration:** We will add 20 lines in the old PHP just to perform the HTTP request passing `{user_id, sale_total}` to the new API. All computational heavy lifting, New Postgres Database, and logic will remain shielded in the new software!
```

> **Rationale**: Resolves the Product Manager's pain point (delivering Sales tomorrow) while protecting the Staff-level architecture. You delivered the tied value to the end customer using the old screens but built the solid, portable "castle" in the new backend.
