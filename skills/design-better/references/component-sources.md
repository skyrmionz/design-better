# Component Sources

Approved places to pull components, icons, and 3D from — and how to use each. **Rule: adapt everything to the project theme (`design-guidelines.md`). Never paste a component in raw with its demo colors and fonts.**

---

## UI components

- **shadcn/ui** — `ui.shadcn.com` — the baseline. Use the neutral base with CSS variables (`base-nova` / neutral / cssVariables style) so the theme's tokens drive everything. This is the default component substrate; most primitives (button, card, dialog, input, tabs) start here.
- **Aceternity UI** — `ui.aceternity.com/components` — for higher-production marketing/hero effects (animated backgrounds, spotlight cards, sheen). Use sparingly and strip the default purple/gradient demo styling; retheme to your palette. Great for the "wow" section, not the whole site.

## Icons

- **Lucide** — `lucide.dev/icons` — **the default icon set.** One library, 1.5–2px stroke, sized on a scale (16/20/24/32/48). Never mix with another set; never fall back to emoji.
- Heroicons / Phosphor are acceptable *alternatives* if a project standardizes on one — but pick exactly one per project.

## 3D / WebGL

- **cloudai-x threejs-skills** — `github.com/cloudai-x/threejs-skills` — for Three.js/R3F scenes and 3D accents. Use for hero centerpieces or interactive experiences; keep it performance-budgeted (lazy-load, pause offscreen — see `performance-and-layout.md`).

## Salesforce-specific assets (SF work only)

*These require Salesforce access and are not redistributed by this skill — see the disclaimer in `presets.md`.*

- **Salesforce marketing icons** — the approved SF icon library via the Widen brand portal (login-gated). Use for on-brand Salesforce collateral; do not substitute random icon packs.
- **3D "Storytelling" icon set** — the approved Salesforce 3D icon collection for richer hero/section art on SF projects.

---

## Fonts

- Default title face: **Avant Garde ITC** (referenced, not bundled — see `presets.md` for the `@font-face` and the licensing note). Default body: **SF Pro / system sans**. A serif (Fraunces) and mono (Geist Mono) are fine as accents.
- Do **not** default to Inter. If you use a system stack, give it personality (scale/spacing/weight).

## Usage checklist when pulling any component

1. Does it match the theme's palette, radius ladder, and fonts? Retheme if not.
2. Does it introduce a banned pattern (ghost CTA, blurred orb, glass-everywhere, emoji)? Strip it.
3. Is its motion on-policy (transform/opacity, ease-out, reduced-motion)? Fix if not.
4. Is it heavier than needed (over-componentized, unused variants)? Trim.
