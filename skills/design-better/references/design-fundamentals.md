# Design Fundamentals

The craft fundamentals that separate professional from amateur work — concrete and quantitative, each with a "why". Synthesized from Refactoring UI, WCAG 2.1, Material Design, Apple HIG, Nielsen Norman Group, and modern CSS guidance. Read when setting up a theme or making a quantitative choice.

---

## Typography

- **Modular type scale.** Pick a ratio and multiply from a 16px/1rem base: 1.125 (dense/app UIs) → 1.25 (balanced) → 1.333 (marketing) → 1.5+ (expressive). *Why: harmonious, predictable size relationships instead of arbitrary heading sizes.*
- **Line-height:** body ~1.5 (1.4–1.6), headings 1.1–1.2, UI labels 1.0–1.3. *Why: screen reading needs more vertical space than the browser default 1.2; large text needs less.*
- **Line length 45–75ch** (optimal 60–70). `max-width: 60ch`. *Why: longer lines lose the reader's place; shorter breaks rhythm.*
- **Letter-spacing:** all-caps +0.05–0.1em; large headings −0.02–0.05em; tiny text +0.02em; body 0. *Why: caps need air, large type looks loose without optical tightening.*
- **2–3 weights max**, each with a job (e.g. 400 body / 500 UI / 700 heading). Avoid 100–300 for body. *Why: more weights dilute hierarchy and slow load.*
- **`font-variant-numeric: tabular-nums`** for tables, counters, financial data, animated numbers. *Why: proportional numerals misalign in columns and jump when animating.*

## Spacing & layout

- **8px base with a 4px half-step.** Scale: 4/8/16/24/32/48/64/96. Every value comes from it. *Why: enough visual distinction, renders crisply at all densities, avoids 35 near-identical values.*
- **Use more whitespace than feels necessary**; increase spacing up the hierarchy (tight within components, loose between sections); group related, separate unrelated. *Why: whitespace creates hierarchy and a premium feel.*
- **12-column grid**, gutters 16–24px, outer margins 16px (mobile) → 24px+ (desktop). *Why: divides into halves/thirds/fourths/sixths cleanly.*
- **Max content widths:** reading 640–768px, marketing 1200–1440px container, forms 480–600px. *Why: ultra-wide text is unreadable; constraint focuses attention.*
- **Optical alignment over mathematical.** Align icons to cap/x-height not baseline; let circles/triangles overshoot the grid; center visual weight (play triangles). *Why: bounding-box centering often looks wrong.*

## Color

- **Build 9-shade ramps (100–900), not 5 hexes.** Base at 500 (works as a button bg); set 900 (text) and 100 (tint) edges; fill 300/700 then the rest. Define shades as fixed values, not on-the-fly lighten/darken. *Why: real UIs need tints for hover/disabled/border/bg — five hexes force fakery.*
- **Adjust saturation at extremes:** bump saturation on very light shades (avoid muddy grey), drop it on very dark (avoid neon). Greys carry a slight hue (2–10% sat). *Why: linear lightness changes look washed-out or garish.*
- **60-30-10** dominant/secondary/accent. *Why: keeps the accent effective.*
- **Never pure black.** `#0a0a0a`–`#1a1a1a` base; body text `#e0e0e0`–`#f5f5f5`. *Why: pure black vibrates against white and reads as a lazy inversion.*
- **WCAG contrast:** 4.5:1 normal text, 3:1 large text (24px, or 18.5px bold) and UI components/graphics. Don't round (4.499 fails). *Why: legibility for low-vision, older, and bright-environment users — and everyone's comprehension speed.*
- **Semantic colors** red=error, amber=warning, green=success, blue=info — but never color alone (see accessibility).

## Visual hierarchy

- **The squint test:** blur the design; the important things should still dominate. *Why: reveals actual emphasis vs. intended.*
- **Size → weight → color, in that order**, and don't use all three on everything. *Why: too many competing signals flatten hierarchy.*
- **De-emphasize secondary content** to ~70–80% size/contrast (metadata, timestamps, helper text). *Why: making everything bold makes nothing stand out.*
- **One primary action per view**; secondary quieter; tertiary as text links. *Why: competing CTAs kill conversion.*

## Depth & elevation

- **Layered shadows**, not one harsh drop shadow: stack 2–3 (low) to 6–8 (high) layers, each low-alpha (~0.3–0.4), progressive offset/blur, negative spread on larger layers. *Why: single shadows look artificial; stacked ones read as real depth.*
- **Tint shadows** toward the ambient light color (slight blue/warm), not pure grey. *Why: grey shadows feel flat.*
- **Borders vs shadows:** borders for crisp minimal boundaries, shadows for premium depth; combining a subtle border + shadow is often best.
- **Named elevation tokens** (`--elevation-01…05`) not arbitrary shadows/z-index. *Why: predictable depth, no z-index chaos.*

## Components & states

- **Define every state:** default, hover, focus, active, disabled, loading, plus error/success on forms. *Why: missing states cause double-clicks, confusion, a11y failures.*
- **Focus rings** 2–4px, offset ~2px, high contrast, `:focus-visible`; never `outline: none` without a replacement. *Why: keyboard users lose orientation otherwise (WCAG 2.4.7).*
- **Touch targets ≥ 44×44px** (48 more comfortable); expand hit area with transparent padding if the visual must stay small. *Why: mis-taps for motor impairments, mobile, older users (WCAG 2.5.5).*
- **Forms:** labels above inputs, single column, correct input types, inline validation after blur (not while typing), primary button left-aligned with fields. *Why: form UX is the #1 conversion killer.*
- **Empty states:** explain what's empty + why, a visual, and a primary action. **Loading states** per Nielsen's thresholds — 0.1s none, 1s subtle indicator, 10s+ progress bar with cancel; show feedback immediately on click (waiting feels 3× longer). Prefer skeletons matching content shape.

## Motion

- **Ease-out for entrances** `cubic-bezier(0,0,0.2,1)`, ease-in for exits, ease-in-out within viewport; linear only for color/opacity. *Why: linear position/scale feels robotic.*
- **Durations:** 150–200ms simple UI, 200–300ms dropdowns/tooltips, 300–500ms large; rarely >500ms; smaller/shorter = faster. *Why: too fast jars, too slow drags.*
- **Animate transform/opacity only** (color/bg with care); never width/height/top/left/margin/padding. *Why: layout properties trigger reflow; transform/opacity are GPU-composited at 60fps.*
- **Purposeful, not decorative** — feedback, guiding attention, showing relationship, maintaining context. *Why: gratuitous motion distracts and can cause motion sickness.*
- **`prefers-reduced-motion`:** cut autoplay/parallax/animated gradients/decorative motion; keep essential feedback. *Why: vestibular disorders — a medical necessity.*

## Icons & imagery

- **One icon set, one stroke width** (1.5–2px), one fill style; never mix. **Size scale** 16/20/24/32/48. *Why: mixed sets/weights look unprofessional.*
- **Optically align** icons to cap/x-height with small negative margins as needed. *Why: bounding-box centering looks off.*
- **Consistent image treatment:** uniform corner radius and aspect ratios (16:9 hero, 4:3 content, 1:1 avatar). Always `alt` (empty for decorative). *Why: mixed ratios/treatments read as chaos.*

## Accessibility as quality

- **Never color alone** — add icon/text/underline/shape (error = red border + icon + text; link = color + underline). *Why: ~8% of men have color-vision deficiency (WCAG 1.4.1).*
- **Semantic HTML** — landmarks (`header/nav/main/article/section/footer`), correct heading order (no skips), `<button>` vs `<a>`. *Why: screen readers navigate by landmarks/headings; free a11y + SEO.*
- **Keyboard nav** — everything focusable, logical tab order, no traps, skip links, Esc-to-close. *Why: motor-disability and power users rely on it.*
- **ARIA sparingly** — first rule of ARIA is don't; use semantic HTML, reach for ARIA only for custom widgets/dynamic content. *Why: misused ARIA is worse than none.*

## Responsive

- **Mobile-first** — base styles for small screens, enhance up with `min-width`. *Why: forces prioritization; easier to enhance than strip.*
- **Content-driven breakpoints** (defaults 640/768/1024/1280/1536). *Why: devices change; content doesn't.*
- **Fluid type via `clamp()`** e.g. `clamp(1rem, 0.875rem + 0.74vw, 1.5rem)` — but must still allow 200% zoom (WCAG 1.4.4). *Why: smooth scaling without breakpoint jumps.*
- **`hover`/`pointer` media queries** — don't assume hover on touch. **Viewport meta** `width=device-width, initial-scale=1`; never `user-scalable=no`/`maximum-scale`. *Why: blocking zoom is an a11y fail.*

## Polish

- **Corner-radius scale** — pick 2–3 values, apply consistently. **Nested radius = outer − gap** (`calc(var(--radius-lg) - var(--spacing-2))`). *Why: equal radii on nested elements look broken.*
- **Browser reset:** `box-sizing: border-box`, zero default margins, `button/input/textarea/select { font: inherit }`, `img { display:block; max-width:100% }`. *Why: browser defaults conflict with designs.*
- **Favicon + meta + `<title>` + description + apple-touch-icon.** *Why: absence signals neglect; needed for bookmarks/share previews.*
- **A state for everything** (see Components). *Why: undefined states break consistency and a11y.*
