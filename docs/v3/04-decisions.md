# Decisions Log

> Permanent record of what was decided, when, and why.
> When a meeting produces a decision, it goes here. The meeting file gets deleted. Git commit = the minutes.
> Never re-litigate a closed decision without a good reason — if you're revisiting, note it as a new entry.

---

## Format

```
### [DECISION-ID] — [Short title]
**Date:** YYYY-MM-DD
**Status:** Closed | Revisiting
**Decision:** What was decided.
**Reasoning:** Why.
**Implications:** What changes as a result.
```

---

## Closed Decisions

### D01 — Delivery not in MVP
**Date:** 2026-02-27
**Status:** Closed
**Decision:** Delivery is not in MVP scope. Physical collection only at launch.
**Reasoning:** Operational complexity is too high with 2 founders and 2 kits. Need to prove the model before adding logistics overhead.
**Implications:** "Flexible logistics" differentiator is framed around pickup/dropoff window separation (which is in MVP), not delivery. Delivery communicated as coming later.

---

### D02 — eKYC not in MVP
**Date:** 2026-02-06
**Status:** Closed
**Decision:** eKYC deferred to post-MVP. MVP uses custom onboarding survey.
**Reasoning:** eKYC requires third-party provider, adds cost, and UX quality varies — some providers are buggy. Not justified at launch scale. Custom survey gives full control over questions and flow.
**Implications:** Revisit eKYC post-MVP when operationally ready. Evaluate Malaysian providers on UX and cost before committing.

---

### D03 — Consultation is customer service, not a product
**Date:** 2026-01-27
**Status:** Closed
**Decision:** We are always open to consult any customer — they can reach us anytime and we actively encourage it. But it is not a core business offering; it's customer service.
**Reasoning:** Seamless self-service is the primary flow. Consultation is the safety net and relationship layer on top. Leading with consultation as a differentiator muddies the positioning.
**Implications:** All external materials frame consultation as part of how we treat customers, not a product or feature we sell.

---

### D04 — Deposit strategy: 25–30% self-insured at launch
**Date:** 2026-02-27
**Status:** Closed
**Decision:** Launch with 25–30% deposits, self-insured. Transition to 10–20% with insurance backing once a partner is secured.
**Reasoning:** Insurance not yet researched. 25–30% is still meaningfully better than market's 50%. Self-insurance fund built from profits.
**Implications:** Insurance research is a pre-launch priority. Phase 2 deposit reduction is contingent on securing insurance.

---

### D05 — Payment: Stripe only
**Date:** 2026-02-06
**Status:** Closed
**Decision:** Single payment gateway: Stripe. Covers cards, FPX (all Malaysian banks), Touch 'n Go, PayLater (Atome).
**Reasoning:** One gateway, all options. Eliminates the manual bank transfer + receipt forwarding pain point of competitors. Simpler to implement and maintain.
**Implications:** No need to evaluate other gateways at MVP. Revisit if Stripe has issues with Malaysian market.

---

### D06 — Shoplot is not a 5-year goal
**Date:** 2026-02-27
**Status:** Closed
**Decision:** The physical shoplot / "Decathlon for rentals" vision is explicitly a long-term endgame, not a 5-year goal.
**Reasoning:** Premature physical location is a capital trap. 5-year goal is top rental service in KL/PJ with strong brand and customer base. Shoplot requires sufficient funds, proven demand, and systematized operations.
**Implications:** Important distinction for investor conversations and internal planning. Don't let the endgame distract from the 5-year goal.

---

### D07 — Adventure gear first, lifestyle gear later
**Date:** 2026-01-27
**Status:** Closed
**Decision:** Phase 1 is adventure gear only (action cameras, dive gear, outdoor kits). Lifestyle gear (gimbals, lighting, audio) is Phase 2.
**Reasoning:** Focused inventory and marketing in early phase. Clear brand identity established first. Different customer segment and kit configurations require established operations.
**Implications:** Lifestyle gear expansion triggered by: adventure business profitable, operations smooth, team has bandwidth. Revisit at Month 4–6 review.

---

### D08 — Kit value assumed RM 2,500 (needs validation)
**Date:** 2026-02-27
**Status:** Open — needs validation
**Decision:** Working assumption: RM 2,500 per kit for deposit calculation purposes.
**Reasoning:** Used in Feb 27 meeting for initial planning.
**Implications:** May be understated — Insta360 X5 body alone is likely RM 2,000+. Full kit with dive case, batteries, mounts, accessories could be RM 3,500–5,000+. **Must confirm actual replacement cost before setting deposit amounts.** Deposit at 25% of RM 3,500 = RM 875, not RM 625.

---

### D09 — MVP capital: RM 10,000 (RM 5k per founder)
**Date:** 2026-02-27
**Status:** Closed
**Decision:** RM 10,000 total capital at launch (RM 5,000 per founder). This covers equipment only.
**Reasoning:** Agreed between founders. Each settles own share.
**Implications:** Full MVP budget (tech, legal, marketing, operations) estimated at RM 23,500–41,000. Gap between RM 10k and full budget needs a plan — either phase the spend, reduce scope, or secure additional capital.

---

### D10 — MVP launch target: March/April 2026
**Date:** 2026-02-27
**Status:** Closed
**Decision:** Target launch March/April 2026.
**Reasoning:** Agreed in Feb 27 meeting.
**Implications:** Pre-launch checklist (see playbook.md) must be completed before this date.

---

## Open Questions Requiring Decisions

These are not yet decided. When a decision is made, move it to Closed Decisions above.

| ID | Question | Priority | Owner | Target Date |
|----|----------|----------|-------|-------------|
| Q01 | Actual replacement cost of full Insta360 X5 kit | HIGH | — | Before launch |
| Q02 | Insurance provider, coverage, and cost in Malaysia | HIGH | — | Before launch |
| Q03 | Onboarding survey questions (finalize 3-part structure) | HIGH | — | Before launch |
| Q04 | "Acceptable wear" visual guide (photo examples) | HIGH | — | Before first rental |
| Q05 | T&Cs and privacy policy (lawyer review) | HIGH | — | Before launch |
| Q06 | Delivery fee structure and logistics cost | MEDIUM | — | Pre-delivery launch |
| Q07 | eKYC provider evaluation (UX + cost) | LOW | — | Post-MVP |
| Q08 | Lifestyle gear expansion trigger and timing | LOW | — | Month 4–6 review |
| Q09 | Frequency threshold where buying beats renting (for loyalty program) | MEDIUM | — | Month 3 |
| Q10 | Credit card authorization hold feasibility (Malaysian payment gateways) | LOW | — | Post-MVP |

---

*Last updated: 02 March 2026*
