# 6. Contradictions & Open Questions

> Part of the [Reference Extract](../extract/) series. This file documents points that conflict across source documents, and questions that remain unresolved. These need active decisions before they affect operations or planning.

---

## Contradictions to Resolve

### C1 — Delivery at MVP: Equal Option vs. Not Doing Yet

~~**Severity: HIGH**~~  `[RESOLVED]`

**Decision:** Delivery is not in MVP scope. To be figured out and introduced in a later phase.

Earlier sessions assumed delivery would be available from launch, but the Feb 27 meeting correctly deferred it given the operational complexity of running 2 kits with 2 founders.

**Implication for messaging:** The "flexible logistics" differentiator should be framed around the pickup/dropoff window separation (which is in MVP scope), not delivery. Delivery can be communicated as coming later without undermining the core value prop.

---

### C2 — eKYC: Preferred vs. Not Best Experience

~~**Severity: MEDIUM**~~  `[RESOLVED]`

**Decision:** eKYC is not in MVP scope. Start with a custom survey for verification, enhance with eKYC later when there's time to properly evaluate providers.

**Reasoning:**
- eKYC requires a third-party provider and adds cost — not justified at MVP stage
- Provider quality varies; some are buggy and create a worse experience than a simple survey
- The UX comparison is nuanced: eKYC is better for customers who don't have an NRIC photo handy, but for customers who do, a survey upload is equally fine (or worse if the eKYC flow is buggy)
- Custom survey gives us full control over the questions and flow from day one

**MVP verification approach:** Custom onboarding survey (customer profile + risk/reliability + marketing fit). Revisit eKYC when operationally ready and after evaluating specific Malaysian providers on UX and cost.

---

### C3 — Kit Replacement Value: RM 2,500 May Be Understated

**Severity: MEDIUM** — directly affects deposit calculation and self-insurance exposure.

| Source | Position |
|---|---|
| `minutes-27022026.md` | Kit value = RM 2,500 → deposit = RM 625 (25%) |
| `market-research.md` | "RM 10,000–15,000 investment" for 3–5 kits → implies RM 2,000–5,000/kit |
| Equipment spec | Insta360 X5 + dive case + batteries + mounts + accessories |

**The conflict:** RM 2,500 may only cover the camera body. A full kit with dive case, multiple batteries, mounts, and accessories could be RM 3,500–5,000+. If so, the deposit at 25% should be RM 875–1,250, not RM 625.

**What needs deciding:**
- What is the actual replacement cost of a complete kit (camera + all accessories)?
- Should deposit be calculated on camera body value only, or full kit value?
- Does undervaluing the kit create meaningful financial exposure in Phase 1?

**Suggested resolution path:** Price out a complete Insta360 X5 kit (body + dive case + batteries + mounts + memory cards) and use that as the deposit basis. `[ACTION]`

---

### C4 — Consultation: Core Model vs. Support Feature

~~**Severity: LOW**~~  `[RESOLVED]`

**Decision:** We are always open to consult any customer — they can reach us anytime and we actively encourage it. But it is not a core business offering; it's customer service.

**Framing for all external materials:** Consultation is part of how we treat customers, not a product or feature we sell. It lives under customer service, not the product offering. The door is always open — we just don't lead with it as a differentiator.

This is distinct from the "seamless self-service" experience being the primary flow. Consultation is the safety net and relationship layer on top.

---

## Open Questions

These are unresolved questions that need answers before or shortly after launch.

### Operational

| Question | Priority | Notes |
|---|---|---|
| What is the actual replacement cost of a full Insta360 X5 kit? | HIGH | Affects deposit amount and self-insurance exposure |
| What are the costs and coverage options for equipment rental insurance in Malaysia? | HIGH | Critical to Phase 2 deposit reduction strategy |
| What are the survey questions for customer onboarding (profile, risk, marketing fit)? | HIGH | Needed before launch — MVP verification method |
| What can we maintain/repair ourselves vs. what needs professional service? | MEDIUM | Affects turnaround time and operating costs |
| What is the delivery logistics cost (Lalamove, Grab, dedicated courier)? | LOW | Needed before delivery is introduced post-MVP |
| Which eKYC providers in Malaysia are worth evaluating (UX + cost)? | LOW | Post-MVP — revisit when operationally ready |

### Pricing & Economics

| Question | Priority | Notes |
|---|---|---|
| At what rental frequency does buying become more economical than renting? | MEDIUM | Needed for loyalty program design and honest customer guidance |
| Is 25–30% deposit low enough to meaningfully drive conversions vs. competitors? | MEDIUM | Validate with customer interviews |
| Will customers pay a delivery fee, and how much? | MEDIUM | Test with early customers |
| What's the right early bird discount / last-minute surcharge structure? | LOW | Indiahikes model as reference |

### Product & Operations

| Question | Priority | Notes |
|---|---|---|
| How do we define "acceptable wear" with visual documentation? | HIGH | Must be defined before first rental to avoid disputes |
| What are the survey questions for customer onboarding (profile, risk, marketing fit)? | HIGH | Needed before launch |
| What are the T&Cs, and how do we make them clear without being intimidating? | HIGH | Legal + trust design |
| When is the right time to add lifestyle gear? | LOW | Demand-driven — revisit at Month 4–6 review |

### Growth & Brand

| Question | Priority | Notes |
|---|---|---|
| How do we measure community impact (indirect benefits)? | LOW | Useful for long-term brand tracking |
| What's the trigger for geographic expansion beyond KL/PJ? | LOW | Revisit at Year 1 review |
| How do we maintain culture and quality as we scale? | LOW | Important but not urgent at MVP stage |

---

## Ideas to Explore (Not Yet Decided)

These came up in brainstorming but haven't been committed to:

| Idea | Source | Notes |
|---|---|---|
| Retailer partnership / affiliate fees for referrals to buy | brainstorm-archive | Interesting loyalty mechanic |
| Loyalty program: rent X times, get discount to buy | brainstorm-archive | Needs frequency threshold defined first |
| Credit card authorization hold (zero deposit option) | brainstorm-archive, meeting-notes | Proven model, but excludes non-card holders |
| Premium onboarding materials (cheat sheets, QR codes, email series) | brainstorm-archive | High-value, relatively low-cost |
| Community champions / volunteer ambassadors | brainstorm-archive | Year 2+ idea |
| Seasonal adventure challenges (gamified engagement) | brainstorm-archive | Year 2+ idea |
| Corporate partnerships (team building, bulk rentals) | brainstorm-archive | Untested segment |
| Second-hand sales of retired rental equipment | brainstorm-archive | Natural inventory lifecycle play |
| Eco-friendly / sustainability angle (refurbish equipment) | minutes-10022026 | Indiahikes sustainability as reference |
| Place rentals at adventure locations (hiking stations, dive shops) | minutes-10022026 | Interesting distribution idea — needs validation |
