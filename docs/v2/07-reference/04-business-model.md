# 4. Business Model & Unit Economics

> Part of the [Reference Extract](../extract/) series. Tags: `[STAT]` hard data · `[VALIDATE]` needs verification · `[ASSUMPTION]` untested · `[CORE]` supports business model · `[RISK]` vulnerability · `[CONTRADICTION]` conflicts with another point · `[ACTION]` next step · `[INSPIRATION]` brand/philosophy · `[RESOLVED]` decided tension

---

## MVP Model (Months 1–4)

*Source: minutes-27022026 — most recent and most detailed operational plan*

### Equipment

| Item | Detail |
|---|---|
| Capital required | RM 10,000 |
| Kits at launch | 2 |
| Kit spec | Insta360 X5 + batteries, stick, dive case, mounts, accessories |
| Kit value (assumed) | RM 2,500 per kit |

`[VALIDATE]` RM 2,500 kit value may be understated — Insta360 X5 alone is likely RM 2,000+. Accessories push total higher. Confirm actual replacement cost before setting deposit amounts.

---

### Pricing Model

| Component | Amount |
|---|---|
| Daily rental rate | RM 70–80/day (market rate for X5) |
| Delivery fee | RM 5–10 (TBD — see contradiction below) |
| Deposit | RM 625 (25% of RM 2,500 kit value) |
| Example: 5-day rental | RM 360 rental + RM 625 deposit = RM 985 total paid upfront |
| What we actually earn | RM 360 |
| What we return | RM 625 |

`[CONTRADICTION]` Delivery fee and delivery availability are disputed — see `06-contradictions.md`.

---

### Unit Economics

| Metric | Figure | Basis |
|---|---|---|
| Break-even per kit | ~50 rental days | At RM 70–80/day |
| Monthly rental days at 30% utilization | ~9 days/month | 30 days × 30% |
| Break-even timeline at 30% utilization | ~5–6 months per kit | 50 days ÷ 9 days/month |
| Year 1 revenue target (SOM) | RM 80K–240K | 200–400 transactions at RM 200–300 AOV |

`[ASSUMPTION]` 30% utilization is a working assumption for planning. Actual utilization depends on demand, marketing, and seasonality. `[VALIDATE]` once live.

`[RISK]` New gear releases annually — rental prices drop as models age. Factor depreciation into long-term unit economics.

---

### Deposit Strategy

| Phase | Deposit % | Mechanism | Trigger |
|---|---|---|---|
| Phase 1 (now) | 25–30% | Self-insured | Launch |
| Phase 2 | 10–20% | Insurance-backed | Once insurance partner secured |

`[CORE]` Lower deposits are a key differentiator vs. market standard of 50%+. `[ACTION]` Research and get quotes from equipment rental insurance providers in Malaysia — this is critical to Phase 2.

**Credit card authorization hold** — could eliminate deposits entirely for card holders (proven model: hotels, car rentals). `[VALIDATE]` Feasibility with Malaysian payment gateways. `[RISK]` Excludes customers without credit cards — potentially large segment in Malaysia.

---

### Multi-Day Pricing (Recommended)

| Duration | Discount |
|---|---|
| 3–5 days | 10% off daily rate |
| 6–10 days | 15% off daily rate |
| 11+ days | 20% off daily rate |

`[CORE]` Multi-day discounts increase rental duration → better utilization → faster break-even.

---

### Delivery Fees (Recommended)

| Scenario | Fee |
|---|---|
| Orders above RM 200, within 10km | Free |
| Within Klang Valley | RM 20–30 |
| Outside Klang Valley | RM 50+ (case-by-case) |

`[CONTRADICTION]` Whether delivery is offered at MVP stage is unresolved — see `06-contradictions.md`.

---

## Operational Flow (MVP)

1. Customer discovers via Instagram → visits website
2. Browses available options, clicks to book
3. Registers + completes survey (customer profile, risk/reliability, marketing fit)
4. Checkout — pays rental fee + 25% deposit
5. Founders reach out via WhatsApp to confirm pickup/delivery
6. Founders and customer meet up and exchange gear
7. Customer goes on trip
8. Customer returns gear on agreed date/time
9. Visual inspection together
10. Deposit returned to customer
11. Founders take 1-day buffer for inspection, cleaning, QC

`[CORE]` Customer should be able to reach founders via WhatsApp at any point. `[ACTION]` Define SOP for response time expectations.

---

### What We're NOT Doing in MVP

- Delivery `[RESOLVED]` — deferred post-MVP
- Lifestyle gear (gimbals, lighting, audio)
- Loyalty program
- Paid advertising
- Physical shopfront

*(Source: minutes-27022026)*

### MVP Launch Timeline (March/April 2026)

- Prepare cash flow projections
- Prepare terms and conditions
- Prepare registration and booking survey questions
- Get feedback on business model (e.g. when applying for loans)
- Get capital — RM 5k investment per partner, each settles own share
- Buy the equipment
- Create informative videos on how to use equipment

### Pre-Live Growth (Month 1–4)

- Reach out to friends — word-of-mouth rentals, use it ourselves
- Generate initial content
- Get brand inspiration finalised
- Soft launch on socials

---

## Payment Infrastructure

- Single payment gateway: **Stripe**
- Covers: card payments, FPX (all Malaysian banks), Touch 'n Go, PayLater (Atome)
- `[CORE]` One gateway, all options — eliminates the manual bank transfer + receipt forwarding pain point of competitors

*(Source: minutes-06022026)*

---

## Verification & Trust

| Method | Status | Notes |
|---|---|---|
| NRIC collection | Market standard | Scare tactic — can report to police. Invasive. |
| eKYC | Post-MVP | `[RESOLVED]` — not in MVP scope. Revisit later. See `06-contradictions-and-open-questions.md`. |
| Credit card auth hold | Idea to explore | Eliminates deposit but excludes non-card holders |
| Pre-rental survey | MVP approach | 3 parts: customer profile, risk/reliability, marketing fit/"our people" rating |
| Equipment documentation | Required | Photos before and after every rental — non-negotiable |

`[CORE]` Pre-rental survey serves dual purpose: risk screening AND marketing segmentation.

**Verification promotion idea:** "Get verified and receive RM 20 off your first RM 100+ rental" — lowers friction for completing verification. *(Source: minutes-06022026)*

**Transparency over exclusivity:** The survey introduces a friction point — balance is needed. Being too exclusive contradicts accessibility. The survey should feel like onboarding, not gatekeeping. *(Source: minutes-06022026)*

**We want to be the opposite of this:** [Camera stores to avoid in KL — r/malaysia](https://www.reddit.com/r/malaysia/comments/48q7p0/camera_stores_to_avoid_in_kl_i_am_a_tourist/) — a direct reference for what bad customer experience looks like in this market. *(Source: minutes-06022026)*

---

## Kit Customization Philosophy

| Customer Type | Approach |
|---|---|
| Beginners | Pre-configured kits curated by activity/niche (diving, hiking, travel vlog) |
| Pros | Customizable — flexibility to build their own kit |

- Kits organized by activity/niche, not just experience level
- Operationally complex — affects inventory management and pricing `[RISK]`
- This is a core differentiator but needs careful implementation to avoid complexity creep

`[CORE]` *(Source: brainstorm-archive)*

---

## Inventory Management

- Build custom inventory tracking system `[ACTION]`
- Start with 3–5 kits, scale based on utilization data
- 1-day buffer between rentals standard (inspection, cleaning, QC)
- Self-maintenance capability important — reduces turnaround time and costs `[ACTION]` Learn what we can fix vs. what needs professional service

---

## Turnaround Time Model

- Customers select **usage dates** (what they pay for)
- We add buffer days around usage for pickup/delivery/dropoff logistics
- Clear cutoff times — no negotiation, but flexible windows agreed with customer
- Customers feel they're only paying for actual usage time

`[CORE]` `[RESOLVED]` This is the "flexible logistics" differentiator — rental period ≠ pickup/dropoff period.

---

## Phase 2 Expansion (Months 7–12)

| Item | Detail |
|---|---|
| Inventory expansion | Add 5–10 more kits based on demand patterns |
| Lifestyle gear | Studio lighting, gimbals, audio equipment |
| Insurance | Reduce deposits to 10–20% with insurance backing |
| Community features | User stories, adventure sharing, social proof |
| Geographic expansion | Extend delivery radius, consider Penang/JB |
| Partnerships | Dive shops, adventure tour operators, travel agencies |

**Success targets:**
- 200–400 rentals in Year 1
- RM 80K–240K revenue
- 70%+ utilization rate
- 30%+ repeat customer rate
- 1,000+ social media followers

`[ASSUMPTION]` All Year 1 targets are projections. `[VALIDATE]` against actual data at Month 3–4 review.

---

## Long-Term Vision

- **5-year goal:** Top rental service in KL/PJ, solid presence, strong customer base, potentially physical location
- **Endgame (not 5-year):** Physical shoplot — "Decathlon for rentals" — multiple brand arms (adventure, lifestyle, merch, studio), systematic process, customers constantly in/out

`[RESOLVED]` The shoplot vision is explicitly NOT a 5-year goal — it's a long-term dream. Distinction matters for planning and investor conversations.

### Future Brand Arms (Endgame)

| Arm | Description |
|---|---|
| Adventure rentals | Core business |
| Lifestyle rentals | Creative equipment (gimbals, lighting, audio) |
| Studio space | Rentable studio with all equipment — clients charge their own clients |
| Merchandise | Branded apparel, accessories |

---

## Open Financial Questions

| Question | Status |
|---|---|
| Actual insurance cost and coverage in Malaysia | `[VALIDATE]` `[ACTION]` — critical |
| Frequency threshold where buying beats renting (for customers) | `[ACTION]` — define for loyalty program |
| Optimal deposit amount (self-insured vs. insurance-backed) | `[VALIDATE]` |
| Delivery logistics cost (Lalamove, Grab, dedicated courier) | `[VALIDATE]` `[ACTION]` |
| Actual kit replacement cost (Insta360 X5 + full accessories) | `[VALIDATE]` — affects deposit calculation |
