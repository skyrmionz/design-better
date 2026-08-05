# Design Rules — Full Catalog

The complete house ruleset. Each rule has a one-line **why** so you apply judgment instead of cargo-culting. Grouped by area. The highest-signal subset is inlined in `SKILL.md`; this is the full reference.

---

## Themes & color

- **Decide the theme before building.** Three colors (dominant / accent / neutral), two fonts (title / body), a named style, and dark-or-light-primary. *Why: a theme fixed up front is what makes an entire multi-page build feel like one product instead of a pile of components.*
- **Never default to purple.** Purple→pink/coral gradients are the single strongest "AI made this" signal. *Why: it's the statistical mean of 2020–2024 startup landing pages in the training data.*
- **Pick colors from the brand, not the industry stereotype.** Don't reach for reflexive "SaaS blue" / "fintech emerald" / "brutalist red". *Why: stereotype palettes read as statistical, not chosen.*
- **Build ramps, not single hexes.** Each color needs ~9 shades (100–900); base at 500. *Why: real UIs need many tints for text, borders, fills, hovers — five hexes force you to fake the rest.* (See `design-fundamentals.md`.)
- **60-30-10 distribution.** ~60% dominant/neutral, 30% secondary, 10% accent. *Why: keeps accent meaningful and the page calm.*
- **Dark mode is never pure black.** Base `#0a0a0a`–`#1a1a1a`; body text `#e0e0e0`–`#f5f5f5`, not pure white. *Why: pure black + pure white smears on OLED and strains eyes; it also reads as a lazy inversion.*
- **Gradients get grain.** Overlay subtle noise/texture on any gradient. *Why: perfectly smooth gradients are a flat-AI tell; grain reads as crafted.*
- **Never gradient-fill text.** Headings and body stay a solid color. *Why: `bg-clip-text` gradient headings are decorative-not-meaningful and a top mechanical AI tell (the impeccable detector flags them).*

## Typography

- **Two fonts max**, one for titles, one for body (a mono for code is a fine third). *Why: more than that fragments the identity.*
- **Don't default to Inter or a raw system stack with zero customization.** If you use them, give them personality via scale, spacing, and weight. *Why: undifferentiated Inter is an AI default.*
- **Limit to 2–3 weights**, each with a clear job. *Why: shipping all 9 weights signals no decision was made.*
- **Consistent header scale across the site.** Same H1/H2/H3 sizes and padding everywhere. *Why: per-page reinvented headers destroy coherence.*
- **Line length 45–75ch; body line-height ~1.5, headings 1.1–1.2.** *Why: readability fundamentals; agents routinely ship full-width text lines.*
- **No widows or orphans.** No heading, CTA, or short paragraph may strand a single word (or two-word fragment) on its own last line. Use `text-wrap: balance` on headings/short blocks, `text-wrap: pretty` on body; tune the measure or add `&nbsp;` where needed. *Why: a lonely trailing word ("…the rest.", "…a minute.", "…with you.") is a constant AI tell — it means the line breaks were never actually looked at.*
- **Tune the measure to the copy, not to a round number.** Set `max-width` so the resulting line count and ragged edge look intentional; don't let a paragraph cramp to four lines when three read better. *Why: an arbitrary `max-w-*` ships whatever break falls out; deliberate measure reads as crafted.*
- **Balance copy across a set of siblings.** Cards/tiles in a row should have title line-counts that match and descriptions within one line of each other. *Why: one 1-line title beside a 2-line title, with descriptions of every length, makes a row of "siblings" look assembled by different hands.*
- **Ease off em-dashes.** *Why: em-dash overuse is a recognizable AI-writing tell.*

## Buttons & interaction

- **Size families.** Buttons come in small / medium / large — pick per context, stay consistent. *Why: one-off sizes look accidental.*
- **Rounded** (slightly or fully), never sharp-cornered by default. *Why: matches the house style; sharp corners are reserved for the F1/angular preset.*
- **Glassy or solid only.** No ghost/outline buttons as primary CTAs. *Why: ghost CTAs are a flat-era AI pattern and convert worse.*
- **Every button has a hover effect** and a smooth transition. *Why: static buttons feel dead; instant changes feel broken.*
- **One primary action per view.** Secondary actions are visually quieter. *Why: two equal CTAs = no CTA.*
- **Button label clears 4.5:1 against the button's own fill.** Pick the on-color from the fill, not the page; verify each button (and its hover state) as a pair. *Why: gray text on a dark fill is technically present but invisible — a label you can't read is a broken button.*
- **Every interactive element has a transition** (~150–300ms, ease-out). *Why: motion communicates state change and feels alive without being distracting.*

## Layout & spacing

- **Spacing on an 8px scale** (4px half-step allowed). No arbitrary 37px/43px values. *Why: off-scale spacing is the clearest "no system" tell.*
- **Section-by-section, not all-at-once.** Build and review one section before the next. *Why: catches drift early.*
- **Vary content density by page type.** Dense legal pages, airy landing pages. *Why: identical density everywhere is an AI uniformity tell.*
- **No cards-within-cards.** *Why: nested containers muddy hierarchy and look generated.*
- **No orphan cards.** Match the grid columns to the item count; N items get an N-column (or evenly-dividing) grid, never a 2-col grid with a lonely third card wrapping to its own row. *Why: a stranded last card is the clearest sign the grid was set once and never checked against the data.*
- **No orphan content on its own line.** A lone list item or trailing element ("Self-host option" sitting alone below a row) must fold back into its group. *Why: a marooned item breaks the group's rhythm and signals the item count was never checked against the layout.*
- **Reserve space for expandable content; sections don't grow on interaction.** An accordion/FAQ must design for its open state — the section's footprint stays stable when items expand, either by reserving the space or animating the reveal in place. *Why: a section that visibly jumps taller when something opens is an interaction-stability failure and reads as unconsidered.*
- **Vary section rhythm.** Adjacent sections must not repeat the same icon-card-grid back to back; alternate the layout (grid / split / feature / list) and the background (white / tinted) so the page has cadence. *Why: identical section after identical section is the strongest "template, not designed" tell after the middle of the fold.*
- **No colored left-edge borders / side-tab accent stripes.** *Why: a recognizable generated-component look.*
- **Nested radius = outer radius − gap.** *Why: concentric corners look right; equal radii look wrong.* (See `design-fundamentals.md`.)
- **Max content widths:** reading 640–768px, marketing 1200–1440px, forms 480–600px. *Why: full-bleed text and forms read as unconsidered.*

## Components

- **No kickers / eyebrows / subtitles above titles** unless they add real categorization. *Why: reflexive eyebrow labels are an AI section-template habit.*
- **No badge/pill overuse** ("NEW", "FEATURED" on everything). *Why: dilutes meaning; template smell.*
- **No modals for everything** — prefer inline forms, slide-outs, dedicated pages. *Why: modal-by-default is an AI reflex.*
- **Don't over-componentize** self-explanatory content. *Why: wrapping a sentence in a Card+Icon+Badge is generated bloat.*
- **Real depth, not decoration.** Shadows show elevation/hierarchy, not sprinkled glow. *Why: glow-on-everything is a polish shortcut that reads as AI.*

## Motion

- **No floating / bouncing / pulsing** unless asked. *Why: idle motion is distracting and a generated-demo tell — except in kiosk/experience contexts.*
- **Ease-out for entrances**, 150–300ms UI / ≤500ms large moves. *Why: natural deceleration; snappy without being abrupt.*
- **No over-bouncy springs** (`cubic-bezier(0.68,-0.55,0.265,1.55)`). *Why: "interesting" easings applied without reason read as AI.*
- **Animate transform/opacity only** (see `performance-and-layout.md`). *Why: animating layout/box-shadow/background thrashes the compositor.*
- **No streaming/shimmering text** on non-AI content. *Why: it's now the "AI is thinking" signifier.*
- **Smooth-scroll in-page navigation.** Anchor/nav links scroll to their target (`scroll-behavior: smooth`, gated behind `prefers-reduced-motion: no-preference`), with `scroll-margin-top` so targets clear a sticky header. *Why: a bare `#anchor` teleports; the abrupt cut reads as broken, not instant.*
- **Respect `prefers-reduced-motion`.** *Why: accessibility and polish.*

## Copy

- **Concrete outcomes over marketing speak.** "Send invoices in 30 seconds", not "Elevate/Supercharge/Streamline/Unlock/Leverage". *Why: buzzword copy is statistically AI.*
- **Brand-voice microcopy**, not grammatically perfect boredom. *Why: "Submission Successful" reads as a machine; give it a voice.*
- **No fake testimonials.** Real, attributed (name + company + photo), or none. *Why: "John D." placeholders are an obvious tell.*
- **Get real copy from the user**; placeholder only when labeled. *Why: inventing final copy misrepresents the product.*
- **Limit redundancy** — don't repeat the same word/theme across adjacent sections. *Why: repetition is an AI-generation artifact.*
- **Trust the reader; don't state what the design already says.** Cut over-literal labels ("All systems operational" beside a green dot, "Click here to learn more"). *Why: announcing what the layout already conveys is the subtlety-free AI voice; implying rather than spelling out is a human tell.*

## Icons & imagery

- **All icons from one library** (Lucide default), one stroke width (1.5–2px), sized on a scale (16/20/24/32/48). *Why: mixed sets/weights are a glaring inconsistency tell.*
- **Never emoji as icons or bullets.** *Why: emoji-as-icon means no icon library was wired up — pure AI default.*
- **Color icons for hierarchy**, on-theme. *Why: rainbow icons or all-grey icons both signal no system.*
- **No sparkle ✨** as an "AI feature" signifier. *Why: it's THE cliché.*
- **Real photography over sterile stock.** Natural light, candid, imperfect. *Why: flawless-office stock reads as AI-selected.*

## Process

- **Never one-shot.** Do not generate a whole page/site in one pass and look for problems after. *Why: post-hoc cleanup of a one-shot is how every rule below gets skipped; the process exists to prevent exactly this.*
- **Ask before building (hard stop).** Run an intake before writing code: audience, tone, pages, copy, and the user's decisions — component sources (libraries vs hand-rolled), 3D/signature visual, exact fonts and how they're sourced. Use the AskUserQuestion tool with concrete options. *Why: these are the user's calls; assuming them silently is the collaboration failure the skill is built to stop. A redirected question means ask better, not stop asking.*
- **Honor dictated constraints; never silently substitute.** A stated font/color/library/word-to-avoid is binding. If you can't meet it, stop and say so — don't quietly swap in an easier choice. *Why: a silent substitution of something the user dictated is the single worst failure this skill can make.*
- **Write `design-guidelines.md` and refer back to it.** Include a "Dictated by the user" ledger. *Why: the doc is what keeps section 12 consistent with section 1, and the ledger is what you check each section against.*
- **Self-review every section** (checklist below), including the dictation check. *Why: drift compounds; catch it per section.*
- **Run the impeccable critique gate** before "done", but treat a clean detector as necessary, not sufficient. *Why: the detector catches mechanical tells and defers taste/copy/rhythm to your eye; a green scan or high heuristic score is not permission to skip judgment.*
- **Run the Three-Question Test** (see `anti-patterns.md`). *Why: final gut-check against statistical choices.*

---

## Section self-review checklist

Run on every section before moving to the next:

1. **Readable?** Text contrast ≥ 4.5:1 (3:1 for large); line length 45–75ch; nothing too small.
2. **Clipping / overflow?** No cut-off text, no horizontal scroll, no elements escaping their container at any breakpoint.
3. **Spacing consistent?** All values on the 8px scale; matches sibling sections' rhythm.
4. **Size families conform?** Buttons and cards use the chosen family sizes, not one-offs.
5. **States present?** Hover, focus-visible, active, disabled, loading/empty where relevant.
6. **On-theme?** Colors, fonts, radius, icon set all match `design-guidelines.md`.
7. **Dictation honored?** Every constraint in the "Dictated by the user" ledger is met in this section — the actual fonts, colors, libraries the user named, with no silent substitution.
8. **Grid fits the count?** No orphan card stranded on its own row; columns match the item count.
9. **Rhythm varies?** This section doesn't repeat the previous one's layout+background; the page has cadence.
10. **Motion sane?** Transitions present, ease-out, transform/opacity only, respects reduced-motion.
11. **Responsive?** Works mobile-first; reflows cleanly at 640/768/1024/1280.
12. **Line breaks clean?** No widow/orphan (no lone last word) in any heading, CTA, or short paragraph, at every breakpoint; the measure suits the copy, not a round number.
13. **Set balanced?** Sibling cards/tiles have matching title line-counts and descriptions within a line of each other; no item stranded alone on its own line.
14. **Labels readable on their fill?** Every button/badge label clears 4.5:1 against its *own* background (default and hover).
15. **Interaction stable?** Expanding content (accordions, toggles) doesn't grow the section or shift surrounding layout; in-page links smooth-scroll, not jump.
16. **Copy trusts the reader?** No over-literal label restating what the design already conveys.
17. **No anti-patterns?** Quick scan against `anti-patterns.md` (no purple-default, ghost CTA, emoji icon, sparkle, gradient text, kicker, card-in-card, blurred orb, status dot, numbered section).

> **Read the rendered page, not the source.** Notes 12–15 only surface when you look at the actual output — where lines truly break, whether a label is legible on its fill, whether a section jumps on expand. A source read will pass all of them and still ship every tell. View the built section (screenshot desktop + mobile) before checking these off. Most of the tells in this build's field notes were invisible in code and obvious on screen.
