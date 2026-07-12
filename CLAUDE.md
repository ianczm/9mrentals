# 9mrentals — Business & Strategy

Adventure gear rental startup in Klang Valley, Malaysia. Target launch March/April 2026.

The steering files below are always active — they define brand, copy, and visual rules.

@.kiro/steering/business-context.md
@.kiro/steering/copy-strategy.md
@.kiro/steering/design-system.md

<!-- market-research.md is inclusion: manual — load it only when doing competitive analysis -->

## Doc Structure

All current business docs live in `docs/v3/`. `docs/v1/` and `docs/v2/` are archived — ignore them.

| File | Purpose |
|------|---------|
| `docs/v3/01-pitch.md` | Investor/partner narrative — derived, always updated last |
| `docs/v3/02-playbook.md` | Source of truth for MVP operations |
| `docs/v3/03-vision.md` | Long-term direction, not current operations |
| `docs/v3/04-decisions.md` | Permanent log of what was decided and why |
| `docs/v3/05-competitors.md` | Competitor landscape |
| `docs/v3/06-community.md` | Community strategy |
| `docs/v3/07-growth.md` | Growth and marketing strategy |
| `docs/v3/meetings/` | Temporary meeting notes — absorb then delete |
| `docs/v3/research/` | Sandbox — not authoritative until absorbed into a core doc |
| `docs/v3/operations/` | Operational docs (onboarding survey, T&Cs) |

**Routing rule:** operational detail → `02-playbook.md`. Resolved decisions → `04-decisions.md`. Long-term direction → `03-vision.md`. `01-pitch.md` is always updated last — it's derived, not primary.

## Research Workflow

`docs/v3/research/` is a sandbox. Files there are exploratory — nothing is authoritative until explicitly absorbed into a core doc with an inline citation:

```
(see research/2026-05-copy-strategy.md)
```

One-shot research files get deleted after absorption. Recurring reference files stay and get linked from the relevant core doc.

When doing competitive analysis, load `.kiro/steering/market-research.md` first — it defines the research protocol and approved/blocked sources.
