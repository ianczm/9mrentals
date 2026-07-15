# 9M Rentals — Business Logic

How rentals work, how gear is priced, and how inventory should be tracked. This
is the product/domain reference — technology-agnostic. It is synthesised from the
earlier 9m iterations (the v1 "Adventure Window" plan, the v3 kit-store rebuild,
and the "simplified" MVP funnel) and reconciled against what the current app
actually does.

Two layers are marked throughout:

- **[MVP]** — the rule as the live storefront implements it today (one kit, one
  price, mocked verification and inventory). Source of truth: `apps/storefront/src/lib/site/constants.ts`.
- **[TARGET]** — the fuller model from prior iterations, kept here so the rules
  aren't lost. Not built yet. Wire it up when the catalogue and Medusa backend land.

> Business strategy, brand, and copy live in the separate notes workspace. This
> file is only the operational rental/inventory logic that the software enforces.

---

## 1. What the business rents

9M Rentals rents action-camera gear to people documenting adventures (diving,
hiking, motorsport, travel, events) in the Klang Valley, Malaysia. The promise:
all the gear, zero ownership, minimal friction.

- **[MVP]** A single kit: the **Insta360 X5 Standard Kit**. One kit, one price, one
  decision — pick dates and book. No catalogue, no browsing, no choices to configure.
- **[TARGET]** A catalogue of activity-specific **kits** plus individual cameras and
  add-ons. The kit is still the primary sell; individual gear is the secondary path.

---

## 2. Pricing

### [MVP] — as built

| Constant | Value | Meaning |
|---|---|---|
| `DAILY_RATE` | RM 60 / day | Flat rate for the whole kit |
| `DEPOSIT` | RM 650 | Flat refundable deposit (≈22% of kit MSRP) |
| `KIT_MSRP` | RM 3000 | Kit replacement value, used for damage/loss math |
| `LATE_FEE_PER_DAY` | RM 120 | 2× daily rate, for late return without notice |

- **Rental total** = `DAILY_RATE × days`, where `days` is **inclusive** of both the
  pickup and return day (Mon→Fri = 5 days).
- **Total charged today** = rental total + deposit. There are no add-ons, tiers,
  or discounts. No minimum or maximum rental length.
- The deposit is refundable in full within ~3 days of return, in good condition.

### [TARGET] — multi-item model

- **Cameras and accessories**: priced **per day**.
- **Consumables** (batteries, SD card, charger, carry case): **flat rate** per rental.
- **Kit price** is derived from its components: `sum(component per-day × qty)` plus
  the flat **MAS** (mandatory accessory set) fee for the kit's camera.
- **Deposit** = **25% of the total MSRP** of everything in the order (fully refundable).
- Prices and MSRPs are **snapshotted at order creation** — later price changes never
  affect existing orders.
- Kit pricing is shown to the customer as **one number**; the per-component breakdown
  is back-office only.

---

## 3. Deposit, damage, late & loss policy

Canonical customer-facing wording lives in the Terms page (`app/terms`) and the
notes workspace. The rules the system must enforce:

- **Deposit handling** — charged with the rental. Card = hold; cash = held aside,
  untouched, returned after the rental. Refunded in full within 3–5 days of a clean return.
- **Damage** — gear is inspected together, with photos, at pickup and return. Normal
  wear is **never** charged. When there is chargeable damage:
  - add-on / peripheral parts → up to **half** replacement price
  - camera / core body → up to **full** replacement price
  - **the deposit is applied first, and any remainder is invoiced.** Damage and loss
    are **not capped at the deposit**. (Do not reintroduce any "capped at RM 650" copy.)
- **Late return** — without notice, charged per late day (`LATE_FEE_PER_DAY`), deducted
  from the deposit first. Moving to open dates ahead of time is always free.
- **Lost / stolen** — lost = full MSRP; stolen with police report = 70%; never
  returned = full MSRP. Deposit applied first, remainder invoiced within 14 days.
- **Cancellation** — 90% refund within 24h of booking; 50% more than a week before the
  rental; nothing less than a week before; **full** refund if 9M cancels (gear
  unavailable or found damaged).

### [TARGET] extras (from v1, not in MVP)
- Optional **damage waiver** add-on (flat fee, caps accidental damage; excludes loss/theft/intent).
- Automated late-fee charging (off-session), with customer consent captured at checkout.

---

## 4. Inventory model  [TARGET]

The MVP tracks no real inventory — availability is a deterministic mock (see §7). The
model below is how inventory *should* be tracked once the catalogue and backend exist.

### Three concepts

- **Product** — a physical item that exists in stock.
  - `subtype`: `camera` | `accessory` | `consumable`
  - cameras/accessories priced per day; consumables flat-rate (one price field is always zero)
  - `msrp` for deposit math; `compatibleCameraIds` (empty = universal)
- **Kit** — a named **recipe** of products with quantities. Has **no stock of its own**;
  availability is derived from its components. Belongs to an activity. Components are fixed
  (customers can't remove them) but optional add-ons can be appended.
- **MAS (Mandatory Accessory Set)** — the minimum consumables a given camera needs to be
  rentable (batteries, SD card, charger, case), configured per camera model. Never shown as
  a customer-facing product; checked silently in availability; billed as one flat "accessories
  kit" fee alongside the camera.

### Shared pool

All physical units live in **one shared pool**. Booking any kit reserves one unit of each
component (× its quantity), which reduces availability for **every other** kit that uses those
same components. No unit is pre-assigned to a kit. Customers may freely mix components across
kit recipes in one order.

### Availability formula

Everything is a **recipe** — a list of `{ productId, quantity }`. A camera rented on its own
uses the recipe `{camera ×1} + MAS(camera)`; a kit uses `kit.components + MAS(cameraId)`. One
formula covers both:

```
freeUnits(product, from, to)
  = stockedQuantity
  - units reserved by any rental that overlaps [from, to]  (status pending/active/confirmed)

recipeAvailable(recipe, from, to)
  = min over each { productId, qty } in recipe of
        floor( freeUnits(productId, from, to) / qty )
```

`floor(free / qty)` is essential for multi-unit components: a kit needing `2× battery` from a
pool of 5 batteries can be assembled only `floor(5/2) = 2` times. The MAS check is folded into
every camera/kit calculation and is **silent** — if the MAS can't be assembled, the item simply
shows 0 available, with no MAS-specific message.

### Displaying availability

- **No dates set** → show the pool count (`stocked − currently reserved`, no date filter). A
  useful signal even before dates are chosen.
- **Dates set** → show the date-filtered count. Cards always show a count; unavailable items are
  **greyed out** ("unavailable for your dates"), never hidden. Never let a customer reach a
  commit point only to discover unavailability.

### Overlap rule
Date overlap uses **inclusive** bounds: a reservation for Jun 6–8 covers Jun 8. A valid rental
requires stock on **every** day in the range; a range may not cross a fully-booked day.

---

## 5. Reservations  [TARGET]

```
[dates set, item available]
   → add to cart  ⇒ soft reservation, 10-minute TTL, customer sees a countdown
                     (item now unavailable to others; first-to-server wins)
   → checkout completes ⇒ soft reservation becomes a confirmed reservation + Rental record
   → TTL expires / abandoned ⇒ reservation released back to the pool
   → order cancelled ⇒ reservation released
```

- **Dates gate the cart.** Nothing can be added without dates. Hard rule.
- Conflict on the last unit: the first write to the server wins; the second gets an immediate
  "just taken" error.
- The **server is the source of truth** — it computes availability, prices, and reservations,
  and validates `freeUnits > 0` for every day at cart-add. The client enforces the same rules
  for UX only.

**[MVP]** The funnel simulates none of this yet: there is no cart and no hold. Dates are carried
in the URL and the booking is written to `sessionStorage` on submit (see §7).

---

## 6. Identity verification & data  [mostly TARGET]

- **[MVP]** The "Verify & pay" action is **mocked**: it routes to `/verify/callback`, which
  auto-approves after a moment and forwards to the confirmation page. Declined / in-review states
  are reachable via `?outcome=declined` / `?outcome=review`. IC/passport format is validated
  client-side; a reserved IC (`880808-08-8888`) always fails a simulated name-match check.
- **[TARGET]** Real eKYC via **Didit** (hosted redirect):
  - **Layer 1** — for Malaysian ICs, a silent name-match pre-check against the national registry
    on field blur; a mismatch blocks progress inline. Passport holders skip this.
  - **Layer 2** — full hosted KYC session (ID photo + liveness selfie) after "Verify & pay".
    Returning, previously-approved customers skip it.
  - Outcomes: Approved → payment; Declined → retry or contact; In Review → manual follow-up on
    WhatsApp, no dead end.
- **PDPA** — IC/passport numbers are personal data. Collect only with a visible notice, use only
  for verification, store **encrypted**, set a retention period (~12 months), and honour
  access/deletion requests. A privacy policy must be live before launch.
- **Eligibility** — 15+; under-18 needs parental approval. Non-Malaysians allowed if their
  passport verifies. The verified person must collect and sign.

---

## 7. Booking flow — as built  [MVP]

The live storefront is a four-screen funnel; all data is mocked.

```
/                       pick dates on the calendar → booking summary → "Book these dates"
/book?from=&to=         email → details → trip → review → "Verify & pay"
/verify/callback        waiting → approved (auto) → forward to confirmation
/booking/:ref           confirmation + trip prep
```

- **Dates** travel between screens via URL search params (`?from=YYYY-MM-DD&to=YYYY-MM-DD`).
- **Customer lookup** is mocked: any email is a new customer except `returning@example.com`,
  which pre-fills a profile and skips to review.
- **Calendar availability** is a deterministic per-month mock (~60% available, clustered 2–4 day
  bookings with 3–6 day gaps) — see `lib/site/dates.ts`. Blocked and past days aren't selectable.
- On submit, the booking is written to `sessionStorage` (`lib/site/booking-store.ts`) so it
  survives navigation to the confirmation page; the confirmation falls back to realistic example
  data if the store is empty (e.g. after a refresh).
- **Payment** is not implemented — approval forwards straight to the confirmation.

---

## 8. Pickup, delivery & contact

- **[MVP]** Pickup only, coordinated over WhatsApp; exact address (Petaling Jaya —
  `PICKUP_LOCATION`) is shown in the booking confirmation. Delivery is not automated but can be
  arranged on request via WhatsApp. Separate pickup/return days (outside the rental period) are
  part of the concept so customers aren't rushed.
- **[TARGET]** Optional delivery with zone-based fees across the Klang Valley; a pickup/delivery
  toggle appears before the form. Time-slot selection for pickup and return.
- **Contact** — WhatsApp is the primary channel (`WHATSAPP` / `WHATSAPP_URL`); email is
  secondary. All phone links point to WhatsApp, never `tel:`.

---

## 9. What's deferred (not in scope now)

Payment (Stripe/FPX/TnG), real eKYC (Didit), the multi-kit catalogue, the shared-pool inventory
and reservation engine, Medusa custom modules (Kit / Rental), delivery logistics, magic-link
return-customer login, transactional emails, and a loyalty program. All are described above under
**[TARGET]** so the intent survives; none is wired up yet. The Medusa backend is currently a clean
scaffold, and `apps/storefront/src/lib/data/*` + `lib/config.ts` are the vendored SDK seam kept for
that future integration.
