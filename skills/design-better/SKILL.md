---
name: design-better
description: "Design and build polished, consistent web UI with a disciplined theme-first process and a house ruleset that avoids 'vibe-coded' tells. TRIGGER when: building or restyling a website/web app/landing page/dashboard, setting up a design system or theme, or when the user asks to make a UI look better/more professional/less AI-generated. DO NOT TRIGGER for: backend-only work, pure copywriting with no UI, or non-web UI (native mobile)."
license: Apache-2.0
metadata:
  version: "0.2.0"
  last_updated: "2026-08-03"
  relatedSkills: ["design-system", "frontend-component-build", "art-direction"]
  externalTools: ["impeccable (npx impeccable)"]
---

# design-better

## Purpose

This skill is a **design process + house ruleset**, not a component library. Coding agents left to their own devices produce UIs that all look the same: purple gradients, glassmorphism everywhere, sparkle emoji, Inter, ghost-button CTAs, generic marketing copy. That "vibe-coded" sameness is the enemy. This skill makes you (1) work theme-first and section-by-section instead of improvising, (2) obey a set of hard-won rules that avoid the AI tells, and (3) run a critique gate before you call anything done.

**This is a framework to invoke and abide by, not a menu of suggestions.** Quality is protected from the first line of code, not patched in at the end. The process is a set of gates: you do not pass a gate until its condition is met. The rules are not a final-exam checklist — they are live checks you apply at every step, and every artifact you produce must fall in line with what the user dictated. If you find yourself building before you have asked, or substituting your own choice for one the user stated, you are off-process — stop and correct it.

## The prime directive: do not one-shot

The single most common failure of this skill is generating a whole page or site in one pass and *then* looking for problems. **Do not.** Building the artifact fast is not progress if it skipped the process. You pause, you plan, you collaborate, you build one section at a time. A running page that ignored the process is a failure, not a deliverable.

## The process (gates — do them in order, do not skip ahead)

**GATE 1 — Set the theme.** Before writing any component, pin down: three colors (dominant / accent / neutral), two fonts (title / body), a named style (e.g. "dark navy glass", "warm organic light"), and whether dark or light is primary. **Never default to purple, and never default to Inter.** If the user has no theme, offer a preset from `references/presets.md` or propose one grounded in their brand. *You may not proceed to build until the theme is decided.*

**GATE 2 — Ask before building. This is a hard stop, not a courtesy.** Do not write code until you have run an intake with the user. Gather: audience, tone, the pages/surface needed, and the actual copy. And explicitly surface the decisions that are the user's to make — never assume them:
- **Component sources** — do they want approved libraries pulled in (e.g. Aceternity UI) or hand-rolled components? (`references/component-sources.md`)
- **3D / signature visual** — do they want a Three.js/R3F motif, a lighter accent, or none?
- **Fonts** — confirm the exact typefaces and how they'll be sourced (licensed files, CDN, system stack).
- **Copy** — get it from the user; if they have none, write a *high-level placeholder* and label it as such. Never invent final marketing copy and present it as real.

Use the AskUserQuestion tool to put concrete options in front of the user. **A rejected or redirected question means ask a better question, not stop asking** — never treat one pushback as license to one-shot the rest. Only infer an answer after a genuine attempt to ask has failed (no channel, or the user says "just decide"), and state the assumption you made.

**GATE 3 — Roadmap by page → section, then confirm it.** Name every page, then every section within each page, explicitly (e.g. "Home: hero, logo strip, three-feature row, pricing, FAQ, footer"). Share the roadmap and the theme decisions before building. Build one section at a time and review it before moving on.

**GATE 4 — Write `design-guidelines.md` into the project.** Copy `assets/design-guidelines.template.md` into the repo, fill it with the theme decisions from Gate 1 **and a "Dictated by the user" ledger** (see below). Refer back to it on every section. This is the single source of truth the rest of the build must match.

**5. Build.** Pull components from approved sources (`references/component-sources.md`) and adapt them to the theme — do not paste them in raw. Obey the core rules below and the fundamentals in `references/design-fundamentals.md`. Watch the performance/layout traps in `references/performance-and-layout.md`.

**6. Self-review each section — rules are checks, applied now, not at the end.** Before moving on, run the section self-review checklist in `references/design-rules.md` AND the dictation check below. Fix drift before the next section; drift compounds.

**7. Critique gate.** Before declaring done, run the `impeccable` critique: `npx impeccable install` then `/impeccable critique` (or `audit`). Fix what it flags. It writes its own `DESIGN.md` — keep that and your `design-guidelines.md` consistent. Then run the anti-pattern pass in `references/anti-patterns.md` and the Three-Question Test on the result. **A clean detector run is necessary but not sufficient** — the detector catches mechanical tells (gradient text, glow, contrast) and defers taste, copy cadence, and layout rhythm to your judgment. Do not let a green scan or a high heuristic score substitute for the eye the rest of this skill trains.

## Honor what the user dictated (non-negotiable)

When the user states a constraint — a font, a color, a library, a layout, a word to avoid — it is binding. **Never silently substitute a different choice because it is easier to wire up.** If you cannot meet a dictated constraint (font unlicensed, library incompatible, asset missing), do not quietly swap it: stop, say so plainly, and offer options. Record every dictated constraint in the `design-guidelines.md` ledger, and in the per-section self-review verify the section still honors all of them. A silent substitution of something the user dictated is the worst failure this skill can make.

## Core rules (always-on)

Inline these from memory; the full catalog with rationale is in `references/design-rules.md`. These are checks you run continuously, not a final gate.

- **Size families.** Buttons and cards come in a small / medium / large family — pick per context and stay consistent across the whole build; never one-off sizes.
- **Buttons.** Rounded (slightly or fully). Glassy or solid only — no ghost/outline buttons as primary CTAs. Every button has a real hover effect and a smooth transition.
- **Transitions.** Every interactive element has a smooth transition (≈150–300ms, ease-out). Never instant, never bouncy-springy.
- **Headers.** Consistent sizing and padding across sections; don't reinvent header scale per page.
- **Icons.** Always from one icon library (Lucide is the default), one stroke width, on-theme, color used for hierarchy. **Never emoji as icons or bullets. Never a sparkle as an "AI" signifier.**
- **Gradients.** If you use a gradient, add a subtle noise/grain texture over it — flat gradients read as AI. Never gradient-fill body or heading text.
- **No kickers.** No eyebrow labels / kickers / subtitles stacked above a title unless they add real categorization.
- **No cards-in-cards.** Don't nest a card inside another card.
- **No colored left-edge borders** and no side-tab accent borders.
- **No blurred orbs / gradient-mesh blobs** floating in backgrounds.
- **No status dots** (active/inactive colored dots) unless the data genuinely needs them.
- **No floating / bouncing / pulsing** motion unless the user explicitly asks for it.
- **No numbered sections** unless asked.
- **No orphan cards.** Match the grid to the count (3 items → 3-col, not a 2-col with a lonely third).
- **Vary section rhythm.** Adjacent sections must not all be the same card-grid; alternate layout and background so the page has cadence.
- **Dark mode is never pure black** — use `#0a0a0a`–`#1a1a1a`, text `#e0e0e0`–`#f5f5f5`.
- **Copy discipline.** Concrete outcomes over marketing speak ("Send invoices in 30 seconds", not "Streamline your workflow"). Limit redundancy. Go easy on em-dashes.

## Context nuance

Match the ruleset to the context. **Data / dashboard / app UIs favor restraint**: hovers shift border or background, no scale transforms, minimal motion, high information density. **Marketing / kiosk / experience UIs can go bolder**: larger motion, scale, pulse are acceptable when intentional — the cannes F1 kiosk (see `references/presets.md`) deliberately uses pulse and scale that a dashboard never should. Decide which world you're in before applying the motion rules.

## Additional resources

Pull these on demand — read the one that fits the task, not all at once.

- `references/design-rules.md` — the full ~50-rule catalog, grouped, each with its "why", plus the section self-review checklist. Read when applying or explaining a specific rule.
- `references/anti-patterns.md` — the "dead giveaways of vibe-coded" DO-NOT list (pattern → why it reads as AI → fix) and the Three-Question Test. Read during the critique gate and whenever a design feels generic.
- `references/design-fundamentals.md` — craft fundamentals: type scales, spacing, color ramps, hierarchy, depth, motion, accessibility, responsive, polish. Read when setting up a theme or making a quantitative choice.
- `references/component-sources.md` — approved component / icon / 3D libraries and how to use each. Read in Gate 2 before asking the user which sources to use, and again before pulling one in.
- `references/performance-and-layout.md` — hard-won performance and layout-bug learnings (what not to animate, overflow traps, safe rebrands). Read before adding animation or full-viewport effects.
- `references/presets.md` — three copy-paste starting themes (Dark Navy Glass default, F1 high-energy, Warm Organic Light) with palettes, fonts, motion. Read in Gate 1 to pick a theme.
- `assets/design-guidelines.template.md` — the per-project design doc to copy into the repo in Gate 4, including the dictation ledger.
