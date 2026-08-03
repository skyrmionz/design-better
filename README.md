# design-better

A Claude Code **skill** that helps any coding agent produce better, more consistent web UI — and stop shipping designs that look "vibe-coded" (purple gradients, glassmorphism everywhere, sparkle emoji, Inter, ghost-button CTAs, generic marketing copy).

It's a **design process + house ruleset**, not a component library. It makes the agent:

1. Work **theme-first** — lock colors, fonts, and a named style before building.
2. Roadmap by **page → section** and build one section at a time.
3. Obey a catalog of hard-won **rules** and avoid a catalog of **anti-patterns**.
4. Run a **critique gate** ([`impeccable`](https://www.npmjs.com/package/impeccable)) before calling anything done.

## What's inside

```
skills/design-better/
├── SKILL.md                         # the lean core: 7-step process + always-on core rules
├── references/
│   ├── design-rules.md              # full ~50-rule catalog, each with its "why" + self-review checklist
│   ├── anti-patterns.md             # dead giveaways of vibe-coded UI → fixes + the Three-Question Test
│   ├── design-fundamentals.md       # type, spacing, color ramps, hierarchy, depth, motion, a11y, responsive
│   ├── component-sources.md         # approved component / icon / 3D libraries + how to use each
│   ├── performance-and-layout.md    # what not to animate, overflow traps, safe rebrands
│   └── presets.md                   # 3 ready themes: Dark Navy Glass, F1, Warm Organic Light
└── assets/
    └── design-guidelines.template.md # per-project design doc the agent copies into your repo
```

## Install

### As a plugin (recommended)

```
/plugin marketplace add skyrmionz/design-better
/plugin install design-better
```

Then reload Claude Code. The skill auto-triggers when you ask to build or restyle a website, landing page, dashboard, or design system — or just run `/design-better` to invoke it manually.

### Manually

Copy the skill into your Claude Code skills directory:

```bash
git clone https://github.com/skyrmionz/design-better.git
cp -r design-better/skills/design-better ~/.claude/skills/
```

### Make the agent reach for it every time (optional)

Add a line to your global `~/.claude/CLAUDE.md`:

```
For any web UI / website / landing-page / design work, invoke the `design-better` skill before starting.
```

## Usage

Once installed, just describe the UI work:

> "Build me a landing page for my analytics tool — make it look professional, not AI-generated."

The skill will pin down a theme, ask for copy, write a `design-guidelines.md` into your project, build section-by-section against the rules, and run the critique gate before finishing.

## Assets disclaimer

The three presets are drawn from the author's own shipped projects and are free to reuse. **Fonts and icons are referenced, not bundled:**

- **Avant Garde ITC** and **SF Pro** are commercial typefaces. The `@font-face` snippet points at an existing CloudFront URL, but **you must supply your own licensed copies** for production. If you don't have them, substitute a font you're licensed for — don't default to Inter.
- **Salesforce marketing icons** are linked via a login-gated brand portal, not redistributed here. Lucide is the default open icon set.
- The mined color palettes are illustrative presets; adapt them to your own brand.

## License

[Apache-2.0](./LICENSE).
