# Design Guidelines — <PROJECT NAME>

> Copy this file into the project root during process step 4, fill in every `<placeholder>`, and refer back to it on every section. This is the single source of truth the whole build must match. Delete this quote block when done.
>
> The **Dark Navy Glass** preset is pre-filled as a worked example — overwrite it with your actual theme.

## 0. Dictated by the user (binding — never silently substitute)

Record every constraint the user stated verbatim. These override defaults, presets, and your taste. If one cannot be met (font unlicensed, library incompatible, asset missing), stop and raise it with the user — do not swap in an easier choice. Re-check this ledger in every section's self-review.

| # | Dictated | Where it applies | Honored? |
|---|---|---|---|
| 1 | <e.g. "bright blues, white + silver accents"> | palette | ☐ |
| 2 | <e.g. "Avant Garde headings, SF Pro body"> | typography | ☐ |
| 3 | <e.g. "use Aceternity components"> | component sources | ☐ |
| 4 | <e.g. "Three.js hero motif"> | signature visual | ☐ |

## Decisions the user made at intake (Gate 2)

- **Component sources:** <libraries (Aceternity, …) vs hand-rolled — as chosen>
- **3D / signature visual:** <R3F motif / light accent / none>
- **Fonts & sourcing:** <exact faces + how sourced: licensed files / CDN / system stack>
- **Copy:** <provided by user / labeled placeholder>

## 1. Brand identity & tone

- **What this is:** <one line — what the product/site is>
- **Audience:** <who>
- **Tone:** <e.g. premium, calm, confident — 3 adjectives>
- **Named style:** Dark Navy Glass
- **Primary mode:** dark

## 2. Color tokens

| Role | Token | Value | Notes |
|---|---|---|---|
| Dominant / bg | `--navy` | `#001639` | page background |
| Surface | `--navy-mid` | `#001e5b` | cards, raised |
| Deep well | `--navy-deep` | `#00112e` | |
| Accent | `--accent` | `#0b9dda` | primary action, links |
| Accent-light | `--accent-light` | `#90d0fe` | hover, highlight |
| Text (body) | `--text` | `#e6f0ff` | ≥4.5:1 on bg — verify |
| Text (muted) | `--text-muted` | ~70–80% of body | metadata |
| Border | `--glass-border` | `rgba(255,255,255,0.1)` | 0.2 on hover |
| Success / Warning / Error / Info | | `<green>` / `<amber>` / `<red>` / `<blue>` | never color alone |

*Build 9-shade ramps (100–900) for dominant + accent, not just these hexes — see `design-fundamentals.md`.*

## 3. Typography

- **Heading font:** `avantgardeitcdemi` (referenced, not bundled — supply a licensed copy)
- **Body font:** SF Pro / system sans
- **Scale ratio:** 1.25 · base 16px → <list computed sizes: 16 / 20 / 25 / 31 / 39 …>
- **Line-height:** body 1.5 · headings 1.15
- **Weights in use:** 400 body / 500 UI / 700 heading
- **Line length:** max 60–70ch on text blocks

## 4. Layout, spacing, max-widths

- **Spacing scale (8px):** 4 / 8 / 16 / 24 / 32 / 48 / 64 / 96
- **Grid:** 12-col, 24px gutters
- **Max content widths:** reading 720px · marketing 1280px · forms 560px
- **Radius ladder:** `--radius: 0.625rem` — sm ×.6 / md ×.8 / lg ×1 / xl ×1.4 / 2xl ×1.8. Nested radius = outer − gap.

## 5. Component specs

- **Buttons:** family sm/md/lg; rounded; solid (primary) or glass (secondary); real hover; 150–300ms ease-out transition. No ghost primaries.
- **Cards:** family sm/md/lg; `bg` = surface, subtle border + layered shadow; no cards-in-cards.
- **Inputs:** labels above; single column; focus-visible ring 2–4px; correct input types.
- **Badges/pills:** only for genuine categorization; no eyebrow-on-every-section.

## 6. Motion

- **Easing:** ease-out entrances `cubic-bezier(0,0,0.2,1)`
- **Durations:** 150–200ms UI · 200–300ms overlays · ≤500ms large
- **Animate:** transform / opacity only
- **Idle motion:** none (no float/pulse/bounce) — this is a product UI, not a kiosk
- **Reduced motion:** honored via `prefers-reduced-motion`

## 7. Iconography

- **Set:** Lucide · stroke 1.75px · sizes 16/20/24/32/48
- **Color:** on-theme, used for hierarchy. No emoji. No sparkle.

## 8. Page & section map

Name every page and its sections; build and self-review one section at a time.

- **<Page: Home>** — <hero · logo strip · three-feature row · pricing · FAQ · footer>
- **<Page: …>** — <sections…>

## 9. Self-review & gate

- [ ] Ran the Gate 2 intake before writing code; the user's decisions above are recorded, not assumed.
- [ ] Every constraint in the section-0 dictation ledger is honored in every section (no silent substitution).
- [ ] Each section passed the `design-rules.md` checklist (readable, no clipping, on-scale spacing, size-family conformance, no orphan cards, varied rhythm, states present, on-theme, motion sane, responsive).
- [ ] Ran `npx impeccable` critique/audit; reconciled with its `DESIGN.md`; fixed findings. (Clean detector = necessary, not sufficient — judgment still applies.)
- [ ] Ran the anti-pattern pass and the Three-Question Test (`anti-patterns.md`).
