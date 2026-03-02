# Research

> Sandbox for analysis and exploration. Free to be messy here — nothing in this folder is authoritative until it's absorbed into a core doc.

## What Goes Here

- Market trend analysis
- Competitor deep-dives
- Pricing research
- Customer segment studies
- Any exploratory thinking that needs space before it's ready to commit

## Lifecycle

Research files have two possible endings:

**One-shot** (e.g. a specific pricing check, a quick market size estimate): absorb findings into the relevant core doc, add a citation, delete the file. The git diff is the record.

**Recurring / reference-worthy** (e.g. competitor landscape deep-dive you'll revisit quarterly): keep the file, link to it from the relevant core doc.

When in doubt, delete. If it mattered, it's in the core doc now.

## Workflow

1. Create `YYYY-MM-topic.md` in this folder
2. Do your research and analysis freely — no structure required
3. When ready, ask Kiro to:
   - Identify what's worth absorbing into core docs
   - Draft the updates with inline citations back to this file
   - Flag anything that contradicts existing decisions
4. Review and confirm the updates
5. Delete the file if it's one-shot, keep it if it's reference-worthy
6. Commit

## Citations in Core Docs

When research informs a core doc, add a lightweight inline reference:

```
(see research/2026-03-market-trends.md)
```

Keep the core doc clean and authoritative. The citation is just a breadcrumb — the core doc should stand on its own.

## Template

```markdown
# Research — YYYY-MM-topic

**Date:** YYYY-MM-DD
**Question / Goal:** [what are you trying to find out or decide?]
**Sources:** [links, documents, conversations]

## Findings

[raw notes, data, analysis — no structure required]

## So What?

[what does this mean for the business? what should change, if anything?]

## Absorption Candidates

- [ ] [finding] → [which core doc]
```
