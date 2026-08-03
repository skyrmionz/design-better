# Performance & Layout

Hard-won engineering learnings mined from real shipped project code (primarily **builders**). These prevent invisible performance drains and layout bugs that make an otherwise-good design feel janky. Read before adding animation or any full-viewport effect.

---

## Animation performance

- **Animate `transform` and `opacity` only.** Never animate `width`/`height`/`top`/`left`/`margin`/`padding`/`box-shadow`/`background` in a loop. *Why: layout properties trigger reflow every frame; transform/opacity are GPU-composited at 60fps.*
- **Never animate full-viewport backgrounds or blurred/screen-blended layers.** A drifting full-page gradient mesh or an animated `mix-blend-mode` layer forces a full recomposite every frame. *(builders' `.gradient-mesh` and aurora carry exactly this warning.)* → Keep the big background static; animate a small element on top instead.
- **Keep expensive effects static at rest; animate only on hover/focus.** Conic-gradient glow rings, auroras, sheen — render them still by default, spin/drift them only on interaction, and ease them back on leave. *(builders' `GlowButton`.)* *Why: idle GPU-heavy animation drains battery and framerate for zero benefit.*
- **Cut blur radius on large blended layers.** builders cut an aurora's blur from 72px → 40px and it stopped stuttering. *Why: `filter: blur()` cost scales with radius × area; large blurred surfaces are the most expensive thing on the page.*
- **Pause offscreen animation** with an `IntersectionObserver`; **respect `prefers-reduced-motion`.** *Why: animating things nobody can see is pure waste; reduced-motion is an a11y requirement.*

## Layout gotchas

- **`overflow-x: clip`, not `overflow-x: hidden`.** `hidden` establishes a scroll container that silently breaks `position: sticky` descendants. `clip` clips without that side effect. *Why: the classic "my sticky header stopped sticking" bug.*
- **`overflow-anchor: none`** on containers with lazy-hydrating canvases/embeds. *Why: scroll anchoring fights late-loading content and makes the page jump.*
- **`history.scrollRestoration = 'manual'`** for app-like routing. *Why: the browser's automatic scroll restoration fights client-side navigation.*
- **Reserve space for state changes** — don't let a toggle or async load reflow the page under the cursor. *Why: "whack-a-mole" layout shift is both an AI tell and a real UX failure.*

## Safe rebrands

- **Alias legacy token keys to new values** instead of mass-renaming classNames. When af-grove rebranded, the old `ink`/`brand`/`cyan.glow` token keys were repointed to the new palette so existing `className`s kept compiling; new code uses the new semantic keys. *Why: a palette swap shouldn't require touching every component; alias first, migrate gradually.*

## Accessibility baseline (ship every time)

- Skip-link to main content.
- `:focus-visible` rings on all interactive elements (never removed).
- `aria-hidden` on purely decorative marks (glow layers, speed lines, background art).
