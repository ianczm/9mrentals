---
inclusion: always
---

# Design System

> Authoritative reference for all visual decisions — colours, typography, spacing, components.
> When writing or reviewing any frontend code for 9mrentals, this document takes precedence.
> Implemented as CSS custom properties in `apps/storefront/src/styles/globals.css`.

---

## Colours

### Backgrounds

Three surface levels. No other dark values.

| Token | Value | Usage |
|---|---|---|
| `--bg-base` | `#0A0A0A` | Primary surface — hero, gear section, how it works, FAQ, footer |
| `--bg-raised` | `#111111` | Secondary surface — why us, social proof, alternating sections |
| `--bg-warm` | `#0D0909` | Brand statement close only — warm near-black |

Do not introduce new background values. If a component needs a surface, use one of these three.

### Text

Six opacity levels. No values between these steps.

| Token | Value | Usage |
|---|---|---|
| `--text-full` | `#F5F5F5` | Primary text, active states, headlines |
| `--text-high` | `rgba(245,245,245,0.75)` | Secondary text, inactive nav, body copy |
| `--text-mid` | `rgba(245,245,245,0.5)` | Supporting text, subtitles, explainers |
| `--text-low` | `rgba(245,245,245,0.3)` | Dimmed text, ghost headers, eyebrows |
| `--text-ghost` | `rgba(245,245,245,0.15)` | Decorative text, marquee, scroll cue |
| `--text-faint` | `rgba(245,245,245,0.07)` | Decorative overlays only — not readable copy |

**Minimum for readable copy:** `--text-mid` (`0.5`). Never use `--text-low` or below for body text, explainers, or FAQ answers.

### Accents

| Token | Value | Usage |
|---|---|---|
| `--accent-red` | `#E8001D` | Brand accent — hero second line, section header accents, CTA buttons, hover states |
| `--accent-red-dim` | `rgba(232,0,29,0.5)` | Dimmed red — mono numbers, footer icons, top-rule accents |
| `--accent-red-glow` | `rgba(232,0,29,0.08)` | Atmospheric glow only |
| `--accent-gold` | `#C9A84C` | Trust signals — stars, review borders, "Real people" header. Testimonials section only. |
| `--accent-gold-dim` | `rgba(201,168,76,0.15)` | Gold backgrounds — review card fills |
| `--accent-gold-border` | `rgba(201,168,76,0.2)` | Gold borders — review cards |

**Red is for brand energy and emphasis. Gold is reserved for testimonials and trust signals. Never use gold outside the social proof section.**

### Heat indicators (availability)

| Token | Value | Usage |
|---|---|---|
| `--heat-open` | `#0D9488` | Available — calendar dots, gear picker dots |
| `--heat-tight` | `#D97706` | Limited availability |
| `--heat-full` | `#E8001D` | Fully booked — reuses accent red intentionally |

### Borders and rules

Three levels. No values between these steps.

| Token | Value | Usage |
|---|---|---|
| `--border-subtle` | `rgba(255,255,255,0.05)` | Section borders, dividers between sections |
| `--border-standard` | `rgba(255,255,255,0.08)` | Card borders, separators within sections |
| `--border-visible` | `rgba(255,255,255,0.12)` | Gear list separators, active/hover borders |

---

## Typography

### Fonts

| Variable | Font | Usage |
|---|---|---|
| `--font-display` | ZalandoSans (variable) | All headers — h1, h2, section headers, display text |
| `--font-body` | ZalandoSans (variable) | All body copy, UI labels, buttons, nav |
| `--font-mono` | DM Mono | Numbers, prices, stats, tags, mono labels |

Both `--font-display` and `--font-body` use the same font file. The distinction is in `fontVariationSettings`.

### Type scale

| Level | Role | Font | `fontVariationSettings` | Size | Tracking | Case |
|---|---|---|---|---|---|---|
| Display / H1 | Hero headline | `--font-display` | `'wdth' 112.5, 'wght' 800` | `clamp(2.25rem, 5.5vw, 5rem)` | `-0.02em` | UPPER |
| H2 | Section headers | `--font-display` | `'wdth' 112.5, 'wght' 700` | `clamp(1.5rem, 3vw, 2.25rem)` | `0.02em` | UPPER |
| H3 | Card/panel titles (e.g. DIVING) | `--font-display` | `'wdth' 112.5, 'wght' 800` | `clamp(2.5rem, 5vw, 4rem)` | `-0.025em` | UPPER |
| Card header | Why Us word headers | `--font-display` | `'wdth' 112.5, 'wght' 700` | `clamp(1.25rem, 2vw, 1.75rem)` | `0.02em` | UPPER |
| Eyebrow | Section labels | `--font-body` | `'wdth' 100, 'wght' 600` | `0.6875rem` | `0.12em` | UPPER |
| Body-lg | Sub-copy, intros | `--font-body` | `'wdth' 100, 'wght' 400` | `1rem` | `0` | mixed |
| Body | Descriptions, details | `--font-body` | `'wdth' 100, 'wght' 400` | `0.875rem` | `0` | mixed |
| Body-sm | Small labels, captions | `--font-body` | `'wdth' 100, 'wght' 400` | `0.8125rem` | `0` | mixed |
| Mono | Numbers, prices, stats | `--font-mono` | — | `0.75rem–0.875rem` | `0.04em` | mixed |

### Header structure rules

- All h1 and h2 use `--font-display` with `wdth 112.5` (SemiExpanded). Never use `--font-body` for headers.
- Multi-line headers use `display: flex; flexDirection: column` with each line as a `<span>`.
- No punctuation in headers. Line breaks replace full stops.
- Second line of a two-line header typically carries the accent colour (`--accent-red`).
- Dimmed secondary lines use `--text-low` (`rgba(245,245,245,0.3)`).

---

## Spacing

Section padding follows a consistent rhythm:

| Context | Padding |
|---|---|
| Full sections (standard) | `56px 0 64px` |
| Full sections (generous) | `72px 0 80px` |
| Full sections (tight) | `40px 0 48px` |
| Inner content max-width | `maxWidth: 1440px, padding: 0 32px` |
| Section header margin-bottom | `36px–48px` |

---

## Component patterns

### Section header pattern

Every section follows this structure:
```
eyebrow (--font-body, 0.6875rem, --text-low, 0.12em tracking, UPPER)
h2 (--font-display, wdth 112.5, wght 700, clamp(1.5rem,3vw,2.25rem), 0.02em, UPPER)
  └── line 1: --text-full or --text-high
  └── line 2: --accent-red (the punch) or --text-low (the qualifier)
```

### Red accent rule

One red accent per section. The red marks the most important element — the word that carries the meaning, the line that lands the punch. Never use red for de-emphasis.

### Hover states

Interactive elements use a left `2px solid --accent-red` border on hover, with `rgba(255,255,255,0.018)` background. Number/icon colours transition to `--accent-red` on hover.

---

## What not to do

- Do not introduce background values outside the three defined surfaces
- Do not use opacity values between the six defined text levels
- Do not use gold outside the social proof / testimonials section
- Do not use red for body copy or de-emphasis
- Do not use `--font-body` for h1 or h2 elements
- Do not use negative letter-spacing on body text
- Do not add punctuation to headers

---

*Last updated: May 2026*
