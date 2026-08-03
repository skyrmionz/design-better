---
name: design-better
description: "Design and build polished, consistent web UI with a disciplined theme-first process and a house ruleset that avoids 'vibe-coded' tells. TRIGGER when: building or restyling a website/web app/landing page/dashboard, setting up a design system or theme, or when the user asks to make a UI look better/more professional/less AI-generated. DO NOT TRIGGER for: backend-only work, pure copywriting with no UI, or non-web UI (native mobile)."
license: Apache-2.0
metadata:
  version: "0.1.0"
  last_updated: "2026-08-03"
  relatedSkills: ["design-system", "frontend-component-build", "art-direction"]
  externalTools: ["impeccable (npx impeccable)"]
---

# design-better

## Purpose

This skill is a **design process + house ruleset**, not a component library. Coding agents left to their own devices produce UIs that all look the same: purple gradients, glassmorphism everywhere, sparkle emoji, Inter, ghost-button CTAs, generic marketing copy. That "vibe-coded" sameness is the enemy. This skill makes you (1) work theme-first and section-by-section instead of improvising, (2) obey a set of hard-won rules that avoid the AI tells, and (3) run a critique gate before you call anything done. Follow the process in order; inline the core rules from memory; pull the reference files on demand.

## The process (do these in order)

**1. Set the theme early — before writing any component.** Pin down: three colors (dominant / accent / neutral), two fonts (title / body), a named style (e.g. "dark navy glass", "warm organic light"), and whether dark or light is primary. **Never default to purple, and never default to Inter.** If the user has no theme, offer a preset from `references/presets.md` or propose one grounded in their brand. A theme decided up front is what keeps the whole build coherent.

**2. Ask before building.** Gather a short design brief: audience, tone, the pages needed, and the actual copy. Get copy from the user — if they have none, write a *high-level placeholder* and label it as such; never invent final marketing copy and present it as real. Confirm the preset or new theme before you build.

**3. Roadmap by page → section.** Name every page, then every section within each page, explicitly (e.g. "Home: hero, logo strip, three-feature row, pricing, FAQ, footer"). Build one section at a time and review it before moving on. Do not generate a whole site in one shot.

**4. Write `design-guidelines.md` into the project.** Copy `assets/design-guidelines.template.md` into the repo, fill it with the theme decisions from step 1, and refer back to it on every section. This is the single source of truth the rest of the build must match.

**5. Build.** Pull components from approved sources (`references/component-sources.md`) and adapt them to the theme — do not paste them in raw. Obey the core rules below and the fundamentals in `references/design-fundamentals.md`. Watch the performance/layout traps in `references/performance-and-layout.md`.

**6. Self-review each section.** Before moving on, check: readable (contrast, line length)? Anything clipped or overflowing? Spacing on-scale and consistent with siblings? Buttons and cards conform to their size family? Full checklist in `references/design-rules.md`.

**7. Critique gate.** Before declaring done, run the `impeccable` critique: `npx impeccable install` then `/impeccable critique` (or `audit`). Fix what it flags. It writes its own `DESIGN.md` — keep that and your `design-guidelines.md` consistent. Then run the anti-pattern pass in `references/anti-patterns.md` and the Three-Question Test on the result.

## Core rules (always-on)

Inline these from memory; the full catalog with rationale is in `references/design-rules.md`.

- **Size families.** Buttons and cards come in a small / medium / large family — pick per context and stay consistent; never one-off sizes.
- **Buttons.** Rounded (slightly or fully). Glassy or solid only — no ghost/outline buttons as primary CTAs. Every button has a real hover effect and a smooth transition.
- **Transitions.** Every interactive element has a smooth transition (≈150–300ms, ease-out). Never instant, never bouncy-springy.
- **Headers.** Consistent sizing and padding across sections; don't reinvent header scale per page.
- **Icons.** Always from one icon library (Lucide is the default), one stroke width, on-theme, color used for hierarchy. **Never emoji as icons or bullets.**
- **Gradients.** If you use a gradient, add a subtle noise/grain texture over it — flat gradients read as AI.
- **No kickers.** No eyebrow labels / kickers / subtitles stacked above a title unless they add real categorization.
- **No cards-in-cards.** Don't nest a card inside another card.
- **No colored left-edge borders** and no side-tab accent borders.
- **No blurred orbs / gradient-mesh blobs** floating in backgrounds.
- **No status dots** (active/inactive colored dots) unless the data genuinely needs them.
- **No floating / bouncing / pulsing** motion unless the user explicitly asks for it.
- **No numbered sections** unless asked.
- **Dark mode is never pure black** — use `#0a0a0a`–`#1a1a1a`, text `#e0e0e0`–`#f5f5f5`.
- **Copy discipline.** Concrete outcomes over marketing speak ("Send invoices in 30 seconds", not "Streamline your workflow"). Limit redundancy. Go easy on em-dashes.

## Context nuance

Match the ruleset to the context. **Data / dashboard / app UIs favor restraint**: hovers shift border or background, no scale transforms, minimal motion, high information density. **Marketing / kiosk / experience UIs can go bolder**: larger motion, scale, pulse are acceptable when intentional — the cannes F1 kiosk (see `references/presets.md`) deliberately uses pulse and scale that a dashboard never should. Decide which world you're in before applying the motion rules.

## Additional resources

Pull these on demand — read the one that fits the task, not all at once.

- `references/design-rules.md` — the full ~50-rule catalog, grouped, each with its "why", plus the section self-review checklist. Read when applying or explaining a specific rule.
- `references/anti-patterns.md` — the "dead giveaways of vibe-coded" DO-NOT list (pattern → why it reads as AI → fix) and the Three-Question Test. Read during the critique gate and whenever a design feels generic.
- `references/design-fundamentals.md` — craft fundamentals: type scales, spacing, color ramps, hierarchy, depth, motion, accessibility, responsive, polish. Read when setting up a theme or making a quantitative choice.
- `references/component-sources.md` — approved component / icon / 3D libraries and how to use each. Read before pulling in a component.
- `references/performance-and-layout.md` — hard-won performance and layout-bug learnings (what not to animate, overflow traps, safe rebrands). Read before adding animation or full-viewport effects.
- `references/presets.md` — three copy-paste starting themes (Dark Navy Glass default, F1 high-energy, Warm Organic Light) with palettes, fonts, motion. Read in step 1 to pick a theme.
- `assets/design-guidelines.template.md` — the per-project design doc to copy into the repo in step 4.
