# Presets

Three copy-paste starting themes, each drawn from a real shipped project. Pick one in process step 1, or use one as scaffolding for a new theme. Each lists palette (hex + intent), fonts, radius/motion, glass/texture, and when to use it.

> **Assets disclaimer.** These palettes are illustrative presets drawn from the author's own projects — reuse them freely. **Fonts and icons are referenced, not bundled.** *Avant Garde ITC* and *SF Pro* are commercial faces: the `@font-face` below points at an existing CloudFront URL, but you must supply your own licensed copies for production. Salesforce marketing icons are linked via a login-gated portal, not redistributed. When in doubt, swap in a font you're licensed for.

---

## 1. Dark Navy Glass — DEFAULT (from `builders`)

Premium dark marketing / product surface with glassmorphism used *intentionally* (floating layers only) and aurora depth.

**Palette**
| Token | Hex | Intent |
|---|---|---|
| navy (base) | `#001639` | page background |
| navy-mid | `#001e5b` | raised surfaces |
| navy-deep | `#00112e` | deepest wells |
| accent | `#0b9dda` | primary actions, links |
| accent-light | `#90d0fe` | hover, highlights |
| blue-soft | `#b7dffe` | soft text on dark |
| glass | `rgba(0,30,91,0.3)` | glass fill |
| glass-border | `rgba(255,255,255,0.1)` (`0.2` hover) | glass edge |

**Fonts:** `avantgardeitcdemi` (headings) · SF Pro / system sans (body) · Fraunces (serif accent) · Geist Mono (code).
**Radius:** `--radius: 0.625rem` ladder — sm ×.6 / md ×.8 / lg ×1 / xl ×1.4 / 2xl ×1.8.
**Motion:** aurora drift 18–26s (static-at-rest, see `performance-and-layout.md`); `GlowButton` / `SheenGlass` glow spins on hover only. Glass tint rgb `11,157,218`.
**Use when:** marketing sites, product landing pages, premium/enterprise SaaS.

## 2. F1 / High-Energy Experience (from `cannes`)

Angular, high-contrast, motorsport-inspired. A kiosk/experience theme that *deliberately* breaks the "no pulse/scale" rule — bold motion is on-brand here.

**Palette**
| Token | Hex | Intent |
|---|---|---|
| black (base) | `#0a0a0a` | background |
| surface | `#1a1a1a` | cards, panels |
| f1-red | `#E10600` | accent, energy |
| red-glow | `rgba(225,6,0,0.25)` | glow behind red |

**Fonts:** Avant Garde headings, **UPPERCASE**, `tracking-[0.2em]`–`[0.3em]`.
**Radius:** angular — `rounded-sm` (sharp is on-brand here, unlike the other presets).
**Accents:** speed lines ~15° at 3–5% red opacity.
**Motion:** bolder — pulse and scale allowed; step easing `cubic-bezier(0.32,0.72,0,1)`.
**Use when:** events, kiosks, product launches, immersive experiences. **Not** for dashboards or data-dense apps.

## 3. Warm Organic Light (from `af-grove`)

Warm, human, light "daytime grove" — natural tones, soft cards, gentle grain.

**Palette**
| Token | Hex | Intent |
|---|---|---|
| cream (bg) | `#F5EFE1` | page background |
| surface | `#FBF7EE` | cards |
| forest | `#1E4D2B` | primary dark |
| pine | `#2E6B3E` | secondary |
| moss | `#6B8E4E` | tertiary |
| fern | `#A7C489` | soft fills |
| wood | `#8B5E3C` | warm neutral |
| bark (ink) | `#3B2A20` | body text |
| line | `#D8CBB2` | borders |
| ember (accent) | `#D9642C` | primary action |
| flame | `#F0A860` | accent-light |
| sky | `#BBD6E8` | cool contrast |

**Fonts:** Avant Garde headings + system body.
**Radius:** soft — `rounded-2xl` cards.
**Glass/texture:** `.glass` = `bg-white/60 backdrop-blur-xl`; `.card` = `rounded-2xl bg-surface border border-line shadow-card`; subtle multiply-blend grain.
**Use when:** warm/human/light brands, content sites, community/wellness/nature.

---

## Shared Avant Garde `@font-face` snippet

Copy-pasted across all three source projects (font referenced, not bundled — see disclaimer):

```css
@font-face {
  font-family: "avantgardeitcdemi";
  src: url("https://<salesforce-cloudfront-host>/fonts/AvantGardeITC-Demi.woff2") format("woff2");
  font-weight: 600;
  font-display: swap;
}
```

Replace the URL with your own licensed copy for production. If you don't have Avant Garde, substitute a geometric sans with strong caps (e.g. a licensed alternative) rather than defaulting to Inter.

## Defining a new theme instead

If none of these fit, don't force one — define a fresh theme following `design-fundamentals.md` (Color: build 9-shade ramps; Typography: pick a scale + 2 fonts) and record it in the project's `design-guidelines.md`. Just keep the house rules (no purple-default, no ghost CTAs, on-scale spacing/radius, one icon set).
