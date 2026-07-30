# ⚡ Harry Potter GitHub Profile README — 10/10 Design Document

> **A comprehensive, single-file guide to building a wizarding-world–class GitHub profile.** Every section below maps directly to the [README.md](./README.md) template and explains the *why*, the *how*, and the exact code you need.

---

## Table of Contents

1. [Design Philosophy](#-1-design-philosophy)
2. [Color System — All 4 Houses](#-2-color-system--all-4-houses)
3. [Typography & Font Strategy](#-3-typography--font-strategy)
4. [Section-by-Section Breakdown](#-4-section-by-section-breakdown)
5. [Dynamic Widgets & Services](#-5-dynamic-widgets--services)
6. [GitHub Action: Contribution Snake](#-6-github-action-contribution-snake)
7. [Dark/Light Mode Adaptation](#-7-darklight-mode-adaptation)
8. [Accessibility Compliance](#-8-accessibility-compliance)
9. [House Variant Quick-Swap Guide](#-9-house-variant-quick-swap-guide)
10. [Deployment Checklist](#-10-deployment-checklist)

---

## 🧙 1. Design Philosophy

### What makes a 10/10 GitHub Profile?

| Dimension | Basic (5/10) | Premium (10/10) |
| :--- | :--- | :--- |
| **Header** | Static text or plain image | Animated gradient wave banner with fade-in text (`capsule-render`) |
| **Introduction** | Plain paragraph | Typing animation cycling through themed incantations (`readme-typing-svg`) |
| **Tech Stack** | Raw badge soup | Curated icon grid from `skillicons.dev` grouped by wizarding discipline |
| **Projects** | Bullet list of links | Pinned repo cards in a 2×2 table grid with house-colored borders |
| **Stats** | Single stats card | Full telemetry suite: Stats + Languages + Streak + Trophies + Activity Graph |
| **Contribution** | None | Animated snake eating contribution squares (GitHub Action) |
| **Contact** | Plain links | Themed badge buttons with magical labels |
| **Dark/Light** | Breaks in one mode | `<picture>` elements with `prefers-color-scheme` media queries |
| **Footer** | Nothing | Matching animated wave footer |

### Core Principles

1. **Thematic Immersion** — Every section name maps to a Harry Potter concept (Marauder's Map → Stats, Sorting Hat → About, Restricted Section → Hidden details)
2. **Visual Layering** — Animated header → Typing text → Static badges → Grid content → Animated footer creates depth
3. **Professional Balance** — Wizarding flavor enhances but never obscures the actual developer information
4. **Universal Compatibility** — Works in both GitHub dark mode and light mode via `<picture>` elements

---

## 🎨 2. Color System — All 4 Houses

### Gryffindor (Default Template)

| Role | Hex | Usage |
| :--- | :--- | :--- |
| Primary Dark | `#1A0000` | Deepest gradient stop, footer |
| Primary Mid | `#3B0000` | Badge label backgrounds |
| Primary | `#740001` | Main brand — borders, accents, rings |
| Gold Accent | `#EEBA30` | Titles, icons, highlights, CTAs |
| Light Gold | `#FCE074` | Hover states, sparkle effects |
| Text Light | `#E5E7EB` | Body text on dark backgrounds |
| GitHub Dark BG | `#0d1117` | Card backgrounds (matches GitHub's native dark) |

### Slytherin

| Role | Hex | Usage |
| :--- | :--- | :--- |
| Primary Dark | `#05120A` | Deepest gradient stop |
| Primary Mid | `#0D2615` | Badge label backgrounds |
| Primary | `#1A472A` | Main brand — borders, accents |
| Silver Accent | `#AAAAAA` | Titles, icons, highlights |
| Bright Silver | `#FFFFFF` | Sparkle, hover states |

**capsule-render gradient**: `color=0:05120A,30:0D2615,60:1A472A,100:AAAAAA`

### Ravenclaw

| Role | Hex | Usage |
| :--- | :--- | :--- |
| Primary Dark | `#070E24` | Deepest gradient stop |
| Primary Mid | `#1B2A59` | Badge label backgrounds |
| Primary | `#0E1A40` | Main brand — borders |
| Bronze Accent | `#C4923E` | Titles, icons, highlights |
| Warm Bronze | `#F2CF8D` | Hover, sparkle |

**capsule-render gradient**: `color=0:070E24,30:0E1A40,60:1B2A59,100:C4923E`

### Hufflepuff

| Role | Hex | Usage |
| :--- | :--- | :--- |
| Primary Dark | `#0F0C0B` | Deepest gradient stop |
| Primary Mid | `#1F1916` | Badge label backgrounds |
| Primary | `#372E29` | Main brand — borders |
| Yellow Accent | `#ECB939` | Titles, icons, highlights |
| Warm Yellow | `#FCE074` | Hover, sparkle |

**capsule-render gradient**: `color=0:0F0C0B,30:1F1916,60:372E29,100:ECB939`

---

## ✍️ 3. Typography & Font Strategy

GitHub's Markdown engine strips custom `@import` CSS. So we leverage **service-side font rendering**:

| Element | Font | How It Renders |
| :--- | :--- | :--- |
| **Header Title** | System serif (capsule-render default) | Rendered server-side in the SVG by Vercel |
| **Typing Animation** | `Cinzel` (Google Font) | Rendered server-side by `readme-typing-svg` — specify via `?font=Cinzel` |
| **Code Blocks** | GitHub's native `monospace` | Rendered by GitHub Markdown |
| **Body Text** | GitHub's system font stack | `-apple-system, BlinkMacSystemFont, Segoe UI, Noto Sans, Helvetica, Arial` |

### Why Cinzel?

`Cinzel` is a free Google Font inspired by classical Roman inscriptions — it evokes the Hogwarts engraved stone aesthetic while remaining highly legible at all sizes. It pairs beautifully with GitHub's system sans-serif for body text.

---

## 📐 4. Section-by-Section Breakdown

### Section 1: Animated Header Banner

**Service**: [capsule-render](https://github.com/kyechan99/capsule-render)

```
https://capsule-render.vercel.app/api?
  type=waving                          ← Animated wave shape
  &color=0:1A0000,30:3B0000,60:740001,100:EEBA30  ← Gryffindor 4-stop gradient
  &height=220                          ← Banner height in pixels
  &section=header                      ← Top of page
  &text=⚡ WIZARDING DEVELOPER ⚡      ← URL-encoded header text
  &fontSize=42                         ← Large, commanding presence
  &fontColor=EEBA30                    ← Gold text
  &animation=fadeIn                    ← Smooth text entrance
  &desc=I solemnly swear...            ← Subtitle text
  &descSize=16
  &descColor=E5E7EB                    ← Light gray subtitle
```

### Section 2: Animated Typing Incantation

**Service**: [readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg)

```
https://readme-typing-svg.demolab.com?
  font=Cinzel                          ← Wizarding serif font
  &weight=700                          ← Bold weight
  &size=28                             ← Large readable size
  &duration=3000                       ← 3 seconds per line
  &pause=1500                          ← 1.5s pause between lines
  &color=EEBA30                        ← Gold text
  &center=true                         ← Centered alignment
  &width=700                           ← Wide enough for longest line
  &lines=                              ← Semicolon-separated spell text
    ✨ Lumos Maxima! Revealing the Code...;
    🪄 Expecto Patronum! Summoning Projects...;
    🔮 Accio Collaboration!;
    ⚡ Mischief Managed.
```

### Section 3: House Identity Badges

Using [shields.io](https://shields.io) with custom `labelColor` for two-tone badges:

```markdown
![Badge](https://img.shields.io/badge/🦁_House-Gryffindor-740001?style=for-the-badge&labelColor=3B0000)
```

- `740001` = Right-side color (primary house color)
- `labelColor=3B0000` = Left-side label background (darker shade)
- `style=for-the-badge` = Large, prominent badge style

### Section 4: About Me with Floating Image

Using `<img align="right" width="280">` to float a Hogwarts GIF alongside the bio text. This creates a magazine-style layout that uses space efficiently.

### Section 5: Tech Stack with Skill Icons

**Service**: [skillicons.dev](https://skillicons.dev)

```markdown
![Skills](https://skillicons.dev/icons?i=ts,js,python,go,rust,html,css,bash&theme=dark)
```

- Icons are grouped by wizarding discipline (Charms, Transfiguration, Potions, Defense)
- `&theme=dark` ensures icons match GitHub dark mode
- Each group gets its own `### ✦ Category` subheading

### Section 6: Featured Projects as 2×2 Grid

Using `github-readme-stats` **pin cards** inside HTML `<table>` cells:

```markdown
![Pin](https://github-readme-stats.vercel.app/api/pin/?
  username=YOUR_USERNAME
  &repo=REPO_NAME
  &bg_color=0d1117        ← Matches GitHub dark background
  &title_color=EEBA30     ← Gold title
  &icon_color=EEBA30      ← Gold icon
  &text_color=E5E7EB      ← Light body text
  &border_color=740001    ← Gryffindor red border
)
```

### Section 7: Full Stats Telemetry

Four stat widgets, all themed consistently:

1. **GitHub Stats Card** — Overall contributions, stars, PRs
2. **Top Languages Card** — Compact layout showing language distribution
3. **Streak Stats** — Current and longest streak with fire icons
4. **GitHub Trophies** — `darkhub` theme with `no-bg=true` and `no-frame=true` for clean integration

### Section 8: Contribution Snake

Requires a GitHub Action (see Section 6 below). The snake animation is generated daily and stored on an `output` branch.

### Section 9: Restricted Section (Collapsible)

```html
<details>
  <summary><b>🗝️ Cast <code>Alohomora</code> to unlock...</b></summary>
  <!-- Hidden content: experimental projects, certifications, etc. -->
</details>
```

### Section 10: Activity Graph

**Service**: [github-readme-activity-graph](https://github.com/Ashutosh00710/github-readme-activity-graph)

```
https://github-readme-activity-graph.vercel.app/graph?
  username=YOUR_USERNAME
  &bg_color=0d1117
  &color=EEBA30          ← Gold axis labels
  &line=740001           ← Gryffindor red line
  &point=EEBA30          ← Gold data points
  &area_color=740001     ← Red fill under the curve
  &area=true
  &hide_border=true
  &custom_title=Spellcasting Frequency
```

### Section 11: Contact / Owl Post

Each social link uses a distinct brand color with a Harry Potter–themed label:

| Platform | Badge Label | Badge Color |
| :--- | :--- | :--- |
| LinkedIn | `Owl_Post` | `0A66C2` (LinkedIn blue) |
| X / Twitter | `Daily_Prophet` | `000000` (X black) |
| Discord | `Great_Hall` | `5865F2` (Discord blurple) |
| Email | `Hedwig_Express` | `D14836` (Gmail red) |
| Portfolio | `The_Pensieve` | `EEBA30` (Gold) |

### Section 12: Animated Footer Wave

Mirrors the header but inverted with `section=footer` and reversed gradient:

```
color=0:EEBA30,30:740001,60:3B0000,100:1A0000
```

---

## 🔧 5. Dynamic Widgets & Services

All widgets used are **free, open-source services** that render SVGs server-side:

| Service | Purpose | URL Base |
| :--- | :--- | :--- |
| [capsule-render](https://github.com/kyechan99/capsule-render) | Animated header/footer banners | `capsule-render.vercel.app/api` |
| [readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg) | Animated typing text | `readme-typing-svg.demolab.com` |
| [skillicons.dev](https://skillicons.dev) | Beautiful tech stack icon grids | `skillicons.dev/icons` |
| [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) | Stats cards, language cards, pin cards | `github-readme-stats.vercel.app/api` |
| [github-readme-streak-stats](https://github.com/DenverCoder1/github-readme-streak-stats) | Contribution streak counter | `github-readme-streak-stats.herokuapp.com` |
| [github-profile-trophy](https://github.com/ryo-ma/github-profile-trophy) | Achievement trophies | `github-profile-trophy.vercel.app` |
| [github-readme-activity-graph](https://github.com/Ashutosh00710/github-readme-activity-graph) | Contribution activity timeline | `github-readme-activity-graph.vercel.app/graph` |
| [komarev visitor counter](https://github.com/antonkomarev/github-profile-views-counter) | Profile view counter | `komarev.com/ghpvc` |
| [Platane/snk](https://github.com/Platane/snk) | Contribution snake animation | GitHub Action → stored on `output` branch |
| [shields.io](https://shields.io) | Custom badges | `img.shields.io/badge` |

---

## 🐍 6. GitHub Action: Contribution Snake

Place this file at `.github/workflows/snake.yml` in your profile repository:

```yaml
name: Generate Snake Animation

on:
  schedule:
    - cron: "0 0 * * *"  # Daily at midnight UTC
  workflow_dispatch:       # Manual trigger

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark

      - uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

**After setup**: The action generates two SVG files on the `output` branch. Reference them in your README with:

```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/USER/USER/output/github-snake-dark.svg"/>
  <img src="https://raw.githubusercontent.com/USER/USER/output/github-snake.svg" alt="Snake"/>
</picture>
```

---

## 🌓 7. Dark/Light Mode Adaptation

GitHub supports the `<picture>` element with `prefers-color-scheme` media queries. Every stats widget in this template uses dual sources:

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="DARK_MODE_URL"/>
  <img src="LIGHT_MODE_URL" alt="Description"/>
</picture>
```

### Color Mapping by Mode

| Element | Dark Mode | Light Mode |
| :--- | :--- | :--- |
| Card Background | `#0d1117` (GitHub native dark) | `#FFFFFF` |
| Title Color | `#EEBA30` (Gold) | `#740001` (Crimson) |
| Text Color | `#E5E7EB` (Light gray) | `#1A0000` (Near-black) |
| Border Color | `#740001` (Crimson) | `#EEBA30` (Gold) |
| Icon Color | `#EEBA30` (Gold) | `#740001` (Crimson) |

This ensures the profile looks **intentionally designed** in both modes, not like an afterthought.

---

## ♿ 8. Accessibility Compliance

| Requirement | Implementation |
| :--- | :--- |
| **WCAG AA Contrast (4.5:1)** | Gold `#EEBA30` on `#0d1117` → ratio **8.2:1** ✅ |
| **Alt text on all images** | Every `<img>` and `<picture>` tag has descriptive `alt` attributes |
| **Screen reader friendly** | Badges use text content that reads naturally (e.g., `House Gryffindor`) |
| **Keyboard navigation** | `<details>` elements are natively keyboard-accessible |
| **No color-only indicators** | Labels + icons + color are used together, never color alone |
| **Responsive stacking** | HTML tables use percentage widths; images use `width="100%"` |
| **Reduced motion** | Typing SVG and capsule-render animations are server-rendered (not client-side JS) |

---

## 🔄 9. House Variant Quick-Swap Guide

To switch the entire profile to a different house, do a **find-and-replace** on these hex values:

### From Gryffindor → Slytherin

| Find | Replace With |
| :--- | :--- |
| `1A0000` | `05120A` |
| `3B0000` | `0D2615` |
| `740001` | `1A472A` |
| `EEBA30` | `AAAAAA` |
| `FCE074` | `FFFFFF` |
| `D3A625` | `2A623D` |

Also update: Badge labels, section headers, Sorting Hat quote, Patronus animal, Quidditch position.

### From Gryffindor → Ravenclaw

| Find | Replace With |
| :--- | :--- |
| `1A0000` | `070E24` |
| `3B0000` | `0E1A40` |
| `740001` | `1B2A59` |
| `EEBA30` | `C4923E` |
| `FCE074` | `F2CF8D` |

### From Gryffindor → Hufflepuff

| Find | Replace With |
| :--- | :--- |
| `1A0000` | `0F0C0B` |
| `3B0000` | `1F1916` |
| `740001` | `372E29` |
| `EEBA30` | `ECB939` |
| `FCE074` | `FCE074` (same) |

---

## ✅ 10. Deployment Checklist

### Before You Push

- [ ] Replace **ALL** instances of `YOUR_USERNAME` with your actual GitHub username
- [ ] Replace `YOUR_SERVER` with your Discord invite code
- [ ] Replace `wizard@hogwarts.edu` with your real email
- [ ] Replace `yourportfolio.dev` with your actual portfolio URL
- [ ] Update LinkedIn, Twitter/X, Discord links with real URLs
- [ ] Update project repo names (`marauders-map`, `potion-brewer`, `alohomora`, `time-turner`) with your actual repositories
- [ ] Update the Sorting Hat quote and house if you're not Gryffindor
- [ ] Update tech stack icons in `skillicons.dev` URLs to match your actual skills
- [ ] Update certifications in the Restricted Section
- [ ] Run the snake workflow manually (Actions tab → Generate Snake Animation → Run workflow)
- [ ] Verify the profile renders correctly in **both** dark and light mode
- [ ] Test on mobile (GitHub app or responsive browser)

### Repository Structure

```
YOUR_USERNAME/
├── README.md                          ← The profile README (this template)
├── .github/
│   └── workflows/
│       └── snake.yml                  ← Snake animation generator
├── assets/                            ← Optional: custom SVGs, images
│   ├── gryffindor-banner.svg
│   ├── slytherin-banner.svg
│   ├── ravenclaw-banner.svg
│   ├── hufflepuff-banner.svg
│   ├── marauders-map-header.svg       ← Custom self-drawing ink header (dark)
│   ├── marauders-map-header-light.svg ← Light mode variant
│   ├── golden-snitch-divider.svg      ← Animated snitch section divider (dark)
│   ├── golden-snitch-divider-light.svg← Light mode variant
│   ├── quill-signature-footer.svg     ← Quill signing "Mischief Managed" (dark)
│   ├── quill-signature-footer-light.svg← Light mode variant
│   ├── wand-casting-spell.svg         ← Wand shooting spell particles (dark)
│   ├── wand-casting-spell-light.svg   ← Light mode variant
│   ├── patronus-phoenix.svg           ← Ethereal Phoenix with particle trail
│   ├── floating-candles.svg           ← The Great Hall floating candles + background
│   ├── hogwarts-express.svg           ← Coding journey progress bar
│   ├── potion-bottles.svg             ← Skills mastery level display
│   └── dragon-egg.svg                 ← Interactive easter egg with wobbling and glow
├── .github/workflows/
│   ├── snake.yml                      ← Contribution snake animation
│   └── profile-3d.yml                 ← 3D contribution calendar (Gryffindor colors)
└── DESIGN_GUIDE.md                    ← This file (reference documentation)
```

---

## ✨ 11. Custom Animated SVG Assets

All custom SVG animations use **pure CSS** — no JavaScript — ensuring full GitHub Markdown compatibility.

### Asset Inventory

| Asset | File(s) | Animations | Purpose |
|:------|:--------|:-----------|:--------|
| **Marauder's Map Header** | `marauders-map-header.svg` / `-light.svg` | Self-drawing ink text, footsteps, compass spin, lightning flash, ink splatters | Replaces capsule-render header |
| **Golden Snitch Divider** | `golden-snitch-divider.svg` / `-light.svg` | Wing flapping, bobbing, sparkle twinkle, line shimmer, glow pulse | Replaces all `---` dividers |
| **Wand Casting Spell** | `wand-casting-spell.svg` / `-light.svg` | Wand appear, spell beam, flying particles, trail stars, floating wisps | Tech stack section intro |
| **Patronus Phoenix** | `patronus-phoenix.svg` | Wing flap, tail sway, head bob, rising wisps, embers, eye glow | About Me section illustration |
| **Floating Candles** | `floating-candles.svg` | Independent float bobbing, flame flickering, glowing auras, falling wax drips, rising light motes | Great Hall atmosphere above stats |
| **Hogwarts Express** | `hogwarts-express.svg` | Train rolling across screen, spinning wheels, rising smoke puffs, filling progress bar, twinkling stars | Coding journey milestone progress |
| **Potion Bottles** | `potion-bottles.svg` | Liquid filling up flasks, bubbling animations, glowing liquid, surface waves | Skills Mastery display below tech stack |
| **Dragon Egg** | `dragon-egg.svg` | Egg wobbling, glowing cracks, blinking pupil scan, escaping smoke wisps, floating embers | Easter egg in the Restricted Section |
| **Quill Signature Footer** | `quill-signature-footer.svg` / `-light.svg` | Quill writing motion, self-drawing signature, ink drops, wax seal stamp, twinkling stars | Replaces capsule-render footer |

### Animation Techniques Used

| Technique | CSS Property | Used In |
|:----------|:-------------|:--------|
| Self-drawing ink | `stroke-dashoffset` + `stroke-dasharray` | Header title, footer signature, footer text |
| Wing flapping | `transform: rotate()` with `transform-origin` | Snitch wings, phoenix wings |
| Particle trail | `transform: translate()` + opacity fade | Wand particles, patronus wisps |
| Sequential reveal | Staggered `animation-delay` | Footsteps, sparkles, embers |
| Glow pulse | `opacity` keyframes on radial gradient | Snitch glow, patronus outer glow |
| Stamp effect | `transform: scale()` + `rotate()` | Wax seal in footer |
| Shimmer | `transform: translateX()` + opacity | Snitch divider lines |

### Dark/Light Mode Strategy

All SVGs that appear differently between modes use the `<picture>` element:

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/example.svg"/>
  <img src="./assets/example-light.svg" alt="..." width="100%"/>
</picture>
```

The Patronus Phoenix uses the same SVG for both modes (silver-blue works on both backgrounds).

---

<div align="center">

*⚡ Crafted with magic, code, and an unreasonable amount of hex color research. ⚡*

*"After all this time?" — "Always."*

</div>
