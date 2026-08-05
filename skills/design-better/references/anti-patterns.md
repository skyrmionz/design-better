# Anti-Patterns — Dead Giveaways of Vibe-Coded UI

Each entry: **pattern → why it reads as AI → concrete fix.** This is the DO-NOT list. Read it during the critique gate (process step 7) and any time a design feels generic. Framing: *how to make Claude-generated UIs not look Claude-generated.*

Sources: Jim Nielsen "The AI Aesthetic" (2026), Web Designer Depot on vibe coding, Frank Chimero "The Web's Grain", Refactoring UI, NN/g flat-design critique.

---

## Color

- **Purple/violet → coral/pink gradients** (`#1f1235`/`#301e4e`/`#463366` + `#ff6e6c`). *AI: it's the composite of every 2020–2024 startup site.* → Choose colors from the actual brand; avoid purple-to-pink unless genuinely brand-aligned. **Never default to purple.**
- **Industry-stereotype palettes** — reflexive "SaaS blue", "fintech emerald", "brutalist red". *AI: statistical associations, not choices.* → Pick a color for a specific reason; make it *your* blue.
- **The beige/cream + orange + serif "AI aesthetic" trinity.** *AI: current zeitgeist cluster.* → If using warm neutrals, break the trinity with an unexpected accent or non-serif type.
- **Pure-black `#000000` dark mode** with pure-white text. *AI: naive color inversion.* → Base `#121212`–`#1a1a1a`; text `#e0e0e0`–`#f5f5f5`; build elevation with lighter greys, not just shadows.

## Layout

- **The generic hero:** centered headline + subhead + two buttons + background gradient blob. *AI: the average of 10,000 SaaS heroes.* → Break symmetry — offset the headline, use a single CTA, replace the blob with a specific illustration, or lead with a different section type.
- **Cookie-cutter section rhythm:** hero → 3-col features → testimonials → CTA, every time. *AI: the "standard template".* → Vary section types and grid columns; organize by the real user journey.
- **Every section is the same icon-card-grid** on the same background. *AI: found one section pattern and repeated it down the page.* → Alternate layout (grid / split / feature / list) and background (white / tinted) so the page has cadence; adjacent sections must not match.
- **Orphan card** — a 3-item set in a 2-col grid, leaving a lonely third card on its own row (or any grid whose columns don't divide the count). *AI: set the grid once, never checked it against the data.* → Match columns to the item count; N items get an N-col or evenly-dividing grid.
- **Numbered sections** (01 / 02 / 03 eyebrows) when nothing is sequential. *AI: decorative ordinal as a section-template habit.* → Drop the numbers unless the order is genuinely a sequence the reader follows. (Note: "Add a client → start the timer → send the invoice" *is* a real sequence — but show it as prose or connected steps, not as a bare "1 / 2 / 3" numbered list, which is the template tell.)
- **Orphan content on its own line** — a lone item like "Self-host option" or a single trailing bullet sitting on a line by itself, breaking the rhythm of the group it belongs to. *AI: emitted a list without checking whether the item count fills its rows evenly.* → Group it: fold the stray item into the row/grid so the set reads as a unit (an odd count often wants a single row of three, or a deliberate 2+1 with matching weight), never one item marooned below the others.
- **Content that isn't balanced across a set** — cards in a row where one title is one line and the next is two, and every description runs a different number of lines, so the row's baselines and card heights don't align. *AI: writes each cell's copy independently and never compares them side by side.* → Balance the set: equalize title line-counts (tighten or pad copy so they match), keep descriptions within one line of each other, and let the grid equalize card heights. A row of siblings should look like siblings.
- **Mathematically perfect symmetric grids with no hierarchy.** *AI: follows the grid with terrifying precision; perfection now reads as suspicious.* → Introduce intentional asymmetry; make the primary thing dramatically larger (Von Restorff).
- **Identical content density on every page.** *AI: uniform spacing rules ignore content.* → Let dense pages be dense and landing pages breathe.
- **Generic 5-link nav:** Home / Features / Pricing / About / Contact. *AI: the "average" nav.* → Name sections around user goals ("Build", "Deploy", "Monitor").

## Icons & symbols

- **Sparkle ✨ as the AI signifier.** *AI: it's THE universal AI indicator.* → Describe AI features specifically; use custom iconography, never ✨🌈🦄.
- **Emoji as icons or bullets** (✅🚀). *AI: no icon library wired up, so it falls back to Unicode.* → Use one icon set (Lucide/Heroicons/Phosphor); typographic bullets otherwise.
- **Mixed icon sets / inconsistent stroke widths.** *AI: pulls icons without stylistic consistency.* → One library, one stroke width (1.5–2px), one style (all outline or all filled).
- **Too-thin, tiny icons.** *AI: characteristic of AI-tool desktop UIs.* → Match platform icon weight and size on a scale.

## Effects

- **Glassmorphism on everything** — `backdrop-filter: blur()` on every card/nav/modal. *AI: 2021–2023 trend overrepresented as "modern".* → Reserve glass for genuine floating layers (nav, modals); most cards don't need it.
- **Gradient-mesh blobs / blurred orbs** in backgrounds. *AI: a no-decision way to add "visual interest".* → Use brand patterns, illustrations, or subtle texture; geometric/intentional gradients only.
- **Gradient-filled text** (`background-clip: text` on headings). *AI: a decorative-not-meaningful flourish and a top mechanical tell — the impeccable detector flags it.* → Solid color for headings and body; let type carry weight through scale and weight, not a gradient.
- **Glow on everything** (big-blur box-shadow on buttons/cards/text). *AI: "polish" without understanding light.* → Shadows show elevation, not decoration; follow an elevation scale.
- **Long / Flat-2.0 shadows.** *AI: oversampled flat-design era.* → Remove them; use elevation-appropriate shadows.
- **Heavy floating-card drop shadows** (`0 10px 40px`). *AI: "depth = big shadow".* → Subtle borders or light shadows for cards; strong shadows only for modals/dropdowns.
- **Arbitrary / inconsistent border-radius** (some 8px, some 24px, some 32px). *AI: no radius scale.* → One radius ladder, applied consistently; nested radius = outer − gap.
- **Colored left-edge / side-tab borders.** *AI: a generated-component look.* → Use spacing and type for hierarchy instead.

## Typography

- **Inter (or raw system stack) with zero customization.** *AI: the free, statistically-default typeface.* → Customize weights/spacing, or pick a font that reflects the brand.
- **6+ font weights** shipped. *AI: includes every available weight.* → 2–3 weights, each with a purpose.
- **Zero type personality** — Arial/Helvetica untouched. *AI: zero design decisions.* → Add personality via scale, spacing, color; or choose a fitting web font.
- **Widows and orphans** — a heading, CTA, or short paragraph that strands a single word (or a two-word fragment) on its own last line: "…so you can stop wrestling with the **rest**.", "Getting started takes about a **minute.**", a closing line that drops "**you**" alone. *AI: sets a `max-width` once and never looks at where the lines actually break.* → Balance the breaks: `text-wrap: balance` on headings and short blocks, `text-wrap: pretty` on body; tune the measure or insert a `&nbsp;` so the last line never holds one lonely word. Read every heading and CTA as it actually wraps, at every breakpoint.
- **Measure tuned to the container, not the copy** — a paragraph that wraps to four cramped lines because the column is a hair too narrow, when three fuller lines would read better. *AI: picks a round `max-w-*` and ships whatever line count falls out.* → Set the measure to the copy: nudge `max-width` so the line count and the ragged edge look intentional, not accidental.

## Spacing

- **Arbitrary off-scale values** (37px, 43px, 18px) or everything-16px uniformity. *AI: "visually balanced" without a system.* → Snap everything to an 8px scale (4/8/12/16/24/32/48/64/96).
- **Whack-a-mole layout shifts** — a toggle repaints the page and moves the cursor target. *AI: doesn't account for interaction stability.* → Reserve space for state changes; animate transform/opacity, not layout.
- **Sections that grow when something inside expands** — an accordion/FAQ where opening an item pushes everything below it down, so the section visibly jumps taller. *AI: lays out for the collapsed state and lets the DOM reflow do the rest.* → Design for the expanded state: reserve the space the open content will occupy (min-height, or a grid that already accounts for the tallest state), or animate the reveal in place so surrounding content doesn't lurch. The section's footprint should feel stable, not elastic.
- **Abrupt in-page jumps** — clicking an anchor/nav link teleports to the target instead of scrolling to it. *AI: emits a bare `#anchor` href and never sets scroll behavior.* → `scroll-behavior: smooth` on the root (gated behind `prefers-reduced-motion: no-preference`), with `scroll-margin-top` on targets so they don't hide under a sticky header. In-page navigation should read as movement through the page, not a cut.

## Components

- **Ghost buttons as primary CTAs.** *AI: oversampled flat-design pattern; also converts worse.* → Solid, high-contrast primary; ghost only for secondary/tertiary.
- **Label that disappears into its own button** — gray text on a dark-green fill, a low-contrast label that's technically there but unreadable ("Start tracking" invisible on a forest-green button). *AI: styles the button and the label from separate defaults and never checks the pair.* → The label must clear 4.5:1 against the *button's actual fill*, not against the page. Pick the on-color (usually near-white or near-black) from the fill, and verify every button's text against its own background, hover state included.
- **Badge / pill / eyebrow overuse** — a label above every heading. *AI: learned it as a heading pattern.* → Eyebrows only for genuine categorization.
- **Kickers / subtitles stacked above titles.** *AI: section-template habit.* → Drop them unless they carry real information.
- **Cards-in-cards.** *AI: muddy generated nesting.* → Flatten; use spacing/dividers.
- **Modals for everything.** *AI: default "attention hog" for any input.* → Inline forms, slide-outs, dedicated pages.
- **Over-componentizing self-explanatory content.** *AI: wraps a sentence in Card+Icon+Badge.* → Let plain content be plain.

## Content

- **Generic marketing speak** — "Elevate", "Supercharge", "Streamline", "Unlock", "Leverage", "Comprehensive". *AI: statistically overrepresented "safe" words.* → Concrete verbs + outcomes: "Send invoices in 30 seconds".
- **The grammatically-perfect boring "AI voice"** in microcopy ("Submission Successful"). *AI: optimizes correctness over personality.* → Brand voice: "Got it!" / "Oops, we need your email".
- **Over-literal copy that doesn't trust the reader** — spelling out what a design already conveys: "All systems operational" next to a green dot, "Click here to learn more" under a heading, a label that restates the icon beside it. *AI: states everything explicitly, with no subtlety, treating the reader as if they can't infer.* → Trust the reader. Let the green dot mean "healthy" and label it "Operational" or nothing; cut words the layout already says. Subtlety — implying rather than announcing — is a human tell the AI voice lacks.
- **Fake "John D." testimonials** — first name + initial, no photo, no company. *AI: plausible-but-fake filler.* → Real, attributed testimonials with photo + company, or none.
- **Em-dash overuse.** *AI-writing tell.* → Use sparingly.
- **Redundant repeated words/themes** across adjacent sections. *AI-generation artifact.* → Vary and consolidate.

## Motion

- **Over-bouncy / springy easings** (`cubic-bezier(0.68,-0.55,0.265,1.55)`). *AI: "interesting" easing with no reason.* → Ease-out for entrances, ease-in for exits; 200–300ms default; springs only for playful brands.
- **No transitions at all** — instant 0ms state changes. *AI: "keep it simple" omission.* → Add 150–200ms transitions to hover/focus/state changes.
- **Streaming / shimmering text** on non-AI content. *AI: the "AI is thinking" pattern.* → Reserve for actual generated content; else immediate or simple fade-in.
- **Status dots** (active/inactive colored dots) everywhere. *AI: decorative status theater.* → Only when the data genuinely needs a status indicator.
- **Floating / bouncing / pulsing** idle motion. *AI: generated-demo flourish.* → Only when the user asks, or in a kiosk/experience context.

## Process (how the work gets made — the tells that produce all the others)

These aren't visual patterns; they're the *working habits* that generate everything above. They are the most important entries in this file, because a clean process prevents the tells instead of catching them after.

- **One-shotting** — generating a whole page or site in a single pass, then hunting for problems. *AI: optimizes for a fast-looking artifact over a correct one; every rule in this file gets skipped in the rush and "fixed" later, badly.* → Gate the work: theme first, ask before building, roadmap by section, build and self-review one section at a time. A running page that skipped the process is a failure, not a deliverable.
- **Skipping the intake** — starting to build without asking the user the decisions that are theirs: component sources (library vs hand-rolled), 3D/signature visual, exact fonts and sourcing, real copy. *AI: assumes to avoid the friction of asking.* → Hard stop before code; use the AskUserQuestion tool with concrete options. A rejected or redirected question means ask a *better* question, not stop asking.
- **Silent substitution** — the user dictated Avant Garde and you shipped Space Grotesk because it was easier to wire up; they said "bright blue" and you reached for the default. *AI: swaps a dictated constraint for a convenient one and says nothing.* → A stated font/color/library/word-to-avoid is binding. If you can't meet it, stop and say so — never quietly swap. This is the single worst failure the skill can make.
- **Green-scan complacency** — treating a clean detector run or a high heuristic score as permission to stop. *AI: trusts the automated number over the user's eye.* → A clean detector is necessary, not sufficient. It catches mechanical tells and defers taste, copy cadence, and layout rhythm to your judgment. If the user's eyes see "generic," it is generic regardless of the score.
- **Non-collaboration** — treating the skill as a rulebook to satisfy rather than a process to work *through* with the user. *AI: races to "done" instead of pausing to plan and confirm.* → Pause, plan, surface decisions, confirm the roadmap. Collaboration is the deliverable's quality control, not overhead.

---

## The Three-Question Test

Before declaring a design done, ask of each notable choice:

1. **Is this choice specific or statistical?** (Your brand blue vs. "SaaS blue".)
2. **Does it show human judgment?** (Intentional asymmetry vs. a perfect grid.)
3. **Could a bot have made this choice?** If yes — make a different one.

The anti-AI signal is originality itself: intentional imperfection, specific choices, and idiosyncrasy that proves human judgment over statistical optimization.
