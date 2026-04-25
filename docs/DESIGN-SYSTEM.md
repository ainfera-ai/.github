# Ainfera · DESIGN-SYSTEM.md

**Version:** v1.1 LOCKED 2026-04-24
**Source:** `ainfera-brand-v1.1.zip` export pack (49 files, 371 KB)
**Pairs with:** `docs/BRAND-WORDS.md` (copy canonical)

This document is the visual spec. Treat each rule as a build
constraint. Every color is a token. Every weight is a number. Every
font has a single canonical source.

---

## §1 · Mark

**File:** `public/brand/mark/ainfera-mark.svg`

Geometry — DO NOT ALTER:

```
viewBox     0 0 100 100
bars        5 horizontal staggered bars
bar size    30 × 5 units each
gap         7 units vertical
stack       53 units total height, centered
offset      +10 units horizontal on odd rows (1, 3, 5)
corner      1.25 units radius (25% of bar height)
footprint   40 × 53 units
```

Reading order — top to bottom maps to architecture:

```
Bar 1 → Trust
Bar 2 → Compute
Bar 3 → Settlement
Bar 4 → Registry
Bar 5 → Orchestration
```

### §1.1 Sizes shipped in export pack

```
favicon-16.png     16×16     browser tab
favicon-32.png     32×32     browser tab retina
favicon-48.png     48×48     desktop shortcut
favicon-180.png    180×180   apple-touch-icon
favicon-512.png    512×512   PWA manifest
favicon-1024.png   1024×1024 high-density / app stores
favicon.ico        multi     legacy fallback
ainfera-mark.svg   vector    canonical source
```

### §1.2 Mark color application

| Background  | Mark color |
|-------------|------------|
| Canvas (dark, default) | Ink `#E8EDF5` |
| Navy (alternate)       | Ink `#E8EDF5` |
| Paper (print only)     | Navy `#0A1F3D` |

### §1.3 Mark misuse — never

- Rotate, skew, distort
- Change bar count (always 5)
- Recolor individual bars
- Apply gradient, shadow, glow
- Place on photography or busy ground

---

## §2 · Color tokens

Monochromatic Deep Blue-Black system. Hierarchy via size, weight,
font family, and opacity — never via hue.

### §2.1 Token table

| Token name      | Hex        | Role                            |
|-----------------|------------|---------------------------------|
| `--canvas`      | `#070B14`  | Page ground, primary canvas     |
| `--midnight`    | `#0A0E1A`  | Elevated surface                |
| `--deep-slate`  | `#0E1322`  | Raised panel                    |
| `--ink`         | `#E8EDF5`  | Primary text                    |
| `--ink-muted`   | `#8A9AB8`  | Secondary text                  |
| `--ink-faint`   | `#5A6B8C`  | Tertiary text, disabled state   |
| `--navy`        | `#0A1F3D`  | Secondary brand accent only     |
| `--paper`       | `#F5F1E8`  | Reversed surface, print only    |

### §2.2 Token files (in export pack)

```
public/brand/tokens/tokens.json     DTCG format
public/brand/tokens/tokens.css      CSS custom properties
public/brand/tokens/tokens.scss     SCSS variables
public/brand/tokens/tailwind.preset.cjs  Tailwind preset
```

Use ONE format for the codebase. For Next.js + Tailwind: extend with
the preset. For plain CSS: import `tokens.css`. Do not maintain hex
values by hand.

### §2.3 Retired colors — NEVER reintroduce

```bash
# Pastel layer accents from Claude Design v1.0 — RETIRED
grep -rEin "#A7B7D4|#C8B890|#8FB39C|#B19CC4|#D18F8F" src/ public/
# Expected: 0 hits

# Status colors — RETIRED (no hue-based status, see §6)
grep -rEin "#6FA37B|#D6B256|#D06A6A|#6A8FD0" src/ public/
# Expected: 0 hits

# Drifted neutrals — RETIRED
grep -rEin "#B6BDC9|#6E7685|#2E3542" src/ public/
# Expected: 0 hits

# Paper drift — RETIRED (canonical is #F5F1E8)
grep -rEin "#F4F3EE" src/ public/
# Expected: 0 hits
```

### §2.4 Hex audit — every hex must be a token

```bash
grep -rEn "#[0-9A-Fa-f]{6}\b" src/ --include="*.tsx" --include="*.ts" --include="*.jsx" --include="*.js" --include="*.css" --include="*.scss"
# Expected: every hit is one of the canonical 8 hex values in §2.1
# OR a hit inside an SVG file in public/brand/ (those are correct)
# Anything else is a violation
```

---

## §3 · Typography

### §3.1 Families

| Role          | Family         | Source                          |
|---------------|----------------|----------------------------------|
| Display, body | Inter Tight    | `@fontsource/inter-tight`       |
| Mono, labels  | JetBrains Mono | `@fontsource/jetbrains-mono`    |

**JetBrains Mono is canonical for mono.** IBM Plex Mono drift in any
v1.0 or v1.1 HTML draft is RETIRED. Verify:

```bash
grep -rEin "IBM Plex|ibm-plex|IBMPlex" src/ public/
# Expected: 0 hits

grep -rEin "JetBrains Mono|@fontsource/jetbrains-mono" src/ public/
# Expected: ≥ 1 hit if mono used anywhere
```

### §3.2 Weights

| Use                              | Weight    |
|----------------------------------|-----------|
| Wordmark, display, headings      | Medium 500 |
| Body, paragraphs, UI             | Regular 400 |
| Emphasis within body             | Medium 500 (NOT bold) |
| Mono labels, numerics, code      | Regular 400 |

**Never use 600 (SemiBold) or 700 (Bold).** Hierarchy is size +
tracking, not weight ramp. Verify:

```bash
grep -rEin "font-weight: ?(600|700|bold|semibold)" src/ --include="*.css" --include="*.scss" --include="*.tsx" --include="*.ts"
# Expected: 0 hits

grep -rEin "font-bold|font-semibold" src/ --include="*.tsx" --include="*.ts" --include="*.jsx" --include="*.js"
# Expected: 0 hits (Tailwind utilities)
```

### §3.3 Font loading — local only

Install:

```bash
npm install @fontsource/inter-tight @fontsource/jetbrains-mono
```

Import only the weights used:

```ts
import '@fontsource/inter-tight/400.css';
import '@fontsource/inter-tight/500.css';
import '@fontsource/jetbrains-mono/400.css';
```

NO Google Fonts CDN. Verify:

```bash
grep -rEin "fonts\.googleapis\.com|fonts\.gstatic\.com" src/ public/
# Expected: 0 hits

grep -rEin "<link[^>]*fonts\.google" public/
# Expected: 0 hits
```

### §3.4 Letter-spacing

| Role               | Tracking      |
|--------------------|---------------|
| Display, H1–H3     | `−0.03em` (Tailwind: `tracking-tight` or tighter) |
| Body               | `0`           |
| Mono eyebrow label | `0.02em` uppercase |

### §3.5 Type scale (web)

| Role         | Family         | Size        | Weight | Tracking  |
|--------------|----------------|-------------|--------|-----------|
| Display      | Inter Tight    | 72 / 80 px  | 500    | −0.03em   |
| H1           | Inter Tight    | 48 / 56 px  | 500    | −0.03em   |
| H2           | Inter Tight    | 32 / 40 px  | 500    | −0.03em   |
| H3           | Inter Tight    | 24 / 32 px  | 500    | −0.02em   |
| Body large   | Inter Tight    | 18 / 28 px  | 400    | 0         |
| Body         | Inter Tight    | 16 / 24 px  | 400    | 0         |
| Body small   | Inter Tight    | 14 / 20 px  | 400    | 0         |
| Eyebrow      | JetBrains Mono | 12 / 16 px  | 400    | 0.02em    |
| Code, data   | JetBrains Mono | 14 / 20 px  | 400    | 0         |

---

## §4 · Spacing

Base unit: 4px. All spacing is a multiple of 4.

| Range       | Use                          |
|-------------|------------------------------|
| 4, 8, 12 px | Within components            |
| 16, 24, 32 px | Between components         |
| 48, 64, 96 px | Section breaks             |

Max widths:

```
Page max:    1280 px
Text column: 720 px
```

---

## §5 · Hero animation (canonical)

Specified explicitly so Claude Code does not improvise.

### §5.1 Composition

```
Layout:        2-column desktop, stacked mobile
Left column:   Animated mark, 480 × 640 px nominal
Right column:  Headline, sub-copy, CTA stack
Background:    var(--canvas)
```

### §5.2 Mark assembly animation

```
Animation:    bars-assemble
Duration:     1.2s total
Stagger:      0.15s between bars
Per-bar:      translateY(-12px) → 0, opacity 0 → 1
Easing:       cubic-bezier(0.16, 1, 0.3, 1)
Order:        Bar 1 (Trust) first, Bar 5 (Orchestration) last
Final state:  Static, visible
```

CSS:

```css
@keyframes bar-arrive {
  from { transform: translateY(-12px); opacity: 0; }
  to   { transform: translateY(0); opacity: 1; }
}

.mark-bar {
  opacity: 0;
  animation: bar-arrive 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}
.mark-bar:nth-child(1) { animation-delay: 0.0s; }
.mark-bar:nth-child(2) { animation-delay: 0.15s; }
.mark-bar:nth-child(3) { animation-delay: 0.30s; }
.mark-bar:nth-child(4) { animation-delay: 0.45s; }
.mark-bar:nth-child(5) { animation-delay: 0.60s; }
```

### §5.3 Ambient breathe (after assembly)

```
Animation:    mark-breathe
Duration:     6s loop
Scale range:  1.0 → 1.015 → 1.0
Easing:       ease-in-out
Origin:       center
Starts:       1.5s after page load
```

```css
@keyframes mark-breathe {
  0%, 100% { transform: scale(1.0); }
  50%      { transform: scale(1.015); }
}

.mark-container {
  animation: mark-breathe 6s ease-in-out 1.5s infinite;
}
```

### §5.4 Reduced motion — required

```css
@media (prefers-reduced-motion: reduce) {
  .mark-bar { opacity: 1; animation: none; }
  .mark-container { animation: none; }
}
```

### §5.5 Layer captions (optional)

JetBrains Mono eyebrow strip on mark's right edge:

```
01 — Trust
02 — Compute
03 — Settlement
04 — Registry
05 — Orchestration
```

Each fades in 0.6s after corresponding bar arrives.

---

## §6 · Status states without hue

The brand has no status colors. State is indicated by typography +
opacity + iconography:

| State        | Treatment                                        |
|--------------|--------------------------------------------------|
| Healthy / OK | Ink at 100% + JetBrains Mono `✓`                |
| Warning      | Ink Muted + JetBrains Mono `!`                  |
| Error        | Ink at 100% weight 500 + JetBrains Mono `×`    |
| Disabled     | Ink Faint                                        |

Verify no hue-based status in code:

```bash
grep -rEin "color: ?(red|green|yellow|orange)|text-(red|green|yellow|orange)" src/
# Expected: 0 hits
```

---

## §7 · Application rules — clean-slate overrides brand v1.1

Three items in the brand v1.1 doc conflict with the clean-slate copy
directive. Clean-slate wins:

| Brand v1.1 says | Clean-slate overrides to |
|-----------------|--------------------------|
| Colophon: `Ainfera Pte Ltd · Singapore` | `© 2026 Ainfera` |
| Cover: `The NYSE of the agentic economy.` | Omit entirely |
| Business card Option C | Template only, never linked from public surface |

---

## §8 · Out of scope (do not generate)

- Conference kit, booth materials
- Podcast branding
- Substack / newsletter templates
- Press release layouts
- `/founder` page, `/team` page
- Headshot placement on any public surface
- Mascot, illustration system

---

## §9 · Asset locations after install

After unzipping `ainfera-brand-v1.1.zip` into `public/brand/`:

```
public/brand/mark/         15 files  master + favicons + variants
public/brand/lockup-h/     17 files  horizontal lockups
public/brand/avatars/       5 files  social avatars
public/brand/social/        5 files  OG images
public/brand/tokens/        4 files  JSON, CSS, SCSS, Tailwind preset
public/brand/README.md      1 file   usage notes
```

Verify after install:

```bash
ls public/brand/mark/ainfera-mark.svg
ls public/brand/tokens/tokens.css
ls public/brand/social/og-1200x630.png
# Expected: all three resolve
```
