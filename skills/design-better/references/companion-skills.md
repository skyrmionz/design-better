# Companion skills — frameworks to borrow, skills to route to

`design-better` owns the opinionated **process + house rules** for building web UI that doesn't look AI-generated. It is deliberately self-contained: it does not depend on any other skill being installed. But five sibling design skills (from the Salesforce `design-intelligence` system) cover adjacent ground well, and their best ideas are folded into this skill's gates. This file does two things:

1. **Frameworks to borrow** — portable ideas from those skills, restated here so you can apply them without needing the other skill installed.
2. **Skills to route to** — when to hand off to the real thing, and what it needs to run.

Nothing Salesforce-internal is copied into this public skill. Where a companion is SF-internal or asset-dependent, this file *points* to it; it does not reproduce it.

---

## Part 1 — Frameworks to borrow (apply these directly)

### A. The Design Intent brief (deepens GATE 2)

Before building, don't just collect a color and some copy — frame the *problem*. A one-paragraph brief that survives the whole build. Borrowed from the Double Diamond (Discover → Define → Develop → Deliver): slow down upstream so a weak assumption costs a sentence now instead of a rebuild later. Capture:

- **Problem statement** — one sentence, framed as a user + job-to-be-done, not a feature list. ("An AP clerk needs to see which invoices are overdue at a glance," not "build an invoices table.")
- **Users** — named with enough specificity to disqualify "everyone" (role + context).
- **Requirements** — split into must-have / should-have / won't-have. Forcing the split forces the tradeoff.
- **Success criteria** — a future state someone can actually check.
- **Constraints** — platform, brand, accessibility target, timeline, existing design system.
- **Open questions** — what's still unknown. Capture these instead of guessing; they go in the `design-guidelines.md` ledger.

**Stance while you gather it — positive friction, not transcription.** Lead with what's promising before what's broken. Name weak assumptions out loud *as assumptions* ("is that tested, or is it just how it's usually done?"). When two requirements pull against each other (density vs. scannability, power vs. simplicity), name the tension rather than papering over it. But you surface considerations; the user decides. After ~3 pushbacks on the same point with no progress, force a resolution — commit, defer it to Open questions, or move on. Don't grind, and don't rubber-stamp ("looks great" with no engagement is a failure).

### B. The five-dimension Craft Report (deepens GATE 7, alongside impeccable)

`impeccable` catches mechanical tells. This is the felt-level pass — the way an interior decorator evaluates a room: two builds can satisfy every rule and one still feels more considered. **Run it on the rendered output (screenshots / live URL), never on the code** — a craft audit from source reads as an engineering audit, which is the wrong job.

Score five dimensions **1–10** (pass threshold **7**):

| Dimension | The felt question |
|---|---|
| **Useful** | "Does this earn the screen real estate it occupies?" |
| **Usable** | "Does this feel effortless, or am I working against it?" |
| **Reliable** | "Do I know what's happening, what just happened, and what will?" |
| **Coherent** | "Does every screen feel like the same hand made it?" |
| **Well-Crafted** | "Was this made with care, or just shipped?" |

**Verdict:** PASS (all ≥ 7) · WARN (some < 7, none < 5) · FAIL (any < 5).

Method: (1) look at it for 30s and record **three first impressions in plain language** *before* any rule-based analysis — honest first impressions anchor everything. (2) Score each dimension on what the user *experiences*, not what you intended. (3) Cap findings at 5 per dimension; if a problem repeats 3+ times, log it once with a count.

**Findings and fixes speak at the felt level, not the implementation level:**
- ✅ "The toolbar feels overworked — too many controls compete for attention; the eye doesn't know what's primary."
- ❌ "Two button base classes: `button toolbar-btn` vs `toolbar-icon-button`."

End with a **Fix Prompt** — a copy-paste directive that opens with a one-sentence felt goal, lists the moves in priority order in *design language* (not "change this CSS var"), names the felt outcome of each, anchors them to regions/screens by name (not file:line), and ends with "re-audit on fresh screenshots; dimensions X and Y should reach N." Also name **what NOT to change** so the next pass doesn't regress what already works.

### C. Accessibility gate (both SF validators defer full WCAG to "a dedicated accessibility skill" — so own it here)

`impeccable`'s audit and the craft report both stop short of real WCAG conformance. Before declaring done, run an explicit accessibility pass targeting **WCAG 2.1 AA**:

- **Contrast** — body text ≥ 4.5:1, large text (≥18px, or ≥14px bold) and UI components/graphics ≥ 3:1, focus indicators ≥ 3:1 against adjacent color. (This is stricter than the house rule's "label clears its own fill" — verify with a contrast checker, don't eyeball.)
- **Never color alone** — every status/meaning pairs color with text, icon, or shape.
- **Keyboard** — every interactive element reachable and operable by keyboard; visible `:focus-visible` ring, never `outline: none` without a replacement; logical tab order (no positive `tabindex`); a skip-link past the nav.
- **Semantics** — semantic HTML (`<button>`, `<nav>`, `<main>`, headings in order, no skipped levels); ARIA only where semantics can't carry it; `alt`/`aria-label` on every meaningful image and icon, `aria-hidden` on decorative marks.
- **Motion** — honor `prefers-reduced-motion`; nothing critical conveyed by motion alone.
- **Zoom** — layout survives 200% zoom; never disable pinch-zoom in the viewport meta.

If you want a deeper, scored a11y audit than this checklist, route to a dedicated accessibility skill (Part 2).

### D. Brand-token extraction (an on-ramp to GATE 1)

When the user has an existing brand (a live site, a Figma file, a PDF brand book, a screenshot, or a CSS file), don't hand-pick three hex codes — extract the real system. Pull a full token set: colors (brand / surface / text / feedback / border), typography (families, a size scale, weights, line-heights), spacing scale, radius scale, shadows, and optionally logo, gradients, and motion. Build **9-shade color ramps** (per `design-fundamentals.md`), not five loose hexes. If a source is inaccessible, say what failed and offer the fallback (screenshot → manual) — never silently default the whole palette. Feed the result into `design-guidelines.md` as GATE 1's theme. For a full extraction pipeline with output formats (tokens.json, CSS vars, brand sheet), route to `extracting-brand` (Part 2).

---

## Part 2 — Skills to route to (hand off when deeper work is warranted)

These are separate skills. Route to one when the task genuinely needs it; otherwise the frameworks folded above are enough. Availability varies — some are Salesforce-internal and won't be installed outside SF.

| Skill | Track | Use it when | Availability |
|---|---|---|---|
| **designing-experiences** | design | The problem is fuzzy and needs real upstream framing — research synthesis, problem definition, structured ideation, design critique. Produces a "Design Intent" artifact. This is the full version of Framework A. | Universal (platform-agnostic) |
| **validating-designs** | design | You want the full scored craft evaluation with conditional reference loading per topic (components, interaction, navigation, state, data, AI, trust…). Full version of Framework B. | Universal |
| **extracting-brand** | design | You need the real extraction pipeline and output formats (tokens.json, tokens.css, brand-sheet.html, Tokens Studio/DTCG, Salesforce CMS brand JSON). Full version of Framework D. | Universal |
| **applying-slds** | engineering | The UI must be **true Salesforce** — Lightning Base Components, SLDS Blueprints, `--slds-g-*` styling hooks, utility classes, SLDS icons. Enforces LBC > Blueprint > Hooks > custom CSS, verify-before-use, and slds-linter validation. | **SF-internal**; depends on bundled SLDS metadata + search scripts |
| **validating-slds** | engineering | You need to score an LWC/SLDS component for compliance — runs the SLDS linter + supplementary analyzer, scores across Linter/Theming/Accessibility/Code-Quality/Component-Usage, and gates on a manual review. | **SF-internal**; depends on `analyze-quality.cjs` + hooks index |

**When building for Salesforce:** the order is `designing-experiences` (frame) → `design-better` (this skill: house rules + theme) → `applying-slds` (build with real SLDS artifacts) → `validating-slds` (score compliance) → dedicated a11y skill (WCAG). `design-better`'s house rules and SLDS's artifact rules are complementary: SLDS tells you *which* button component and hook exists; this skill tells you the button shouldn't be a ghost CTA, needs a real hover, and its label must clear 4.5:1.

### Dedicated accessibility skills (both validators explicitly punt full WCAG to one of these)

Framework C above is the fast gate. For a deep, scored accessibility audit, route to whichever is available in your environment:

- **Accessibility Evaluator** — WCAG 2.1 AA evaluation; lives in the same `design-intelligence` catalog as the skills above.
- **experience-quality** — broader experience-quality checks including accessibility (`git.soma.salesforce.com/jonmoore/experience-quality`).
- **mulesoft-accessibility** — MuleSoft's a11y skill (`git.soma.salesforce.com/mulesoft/mule-omni` → `.claude/skills/mulesoft-accessibility`).
- **a11y-audit** — Data360's accessibility audit (`github.com/salesforce-ux-emu/data360-ux-skills` → `a11y-audit`).

None of these are bundled with `design-better`. Route to them by name/path; if none is installed, Framework C is the floor you still hold.
