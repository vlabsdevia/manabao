# Manabao Landing Pages — Design Spec

## Overview

Two static landing page variants for Manabao, a Dominican mountain coffee brand. Both share a single design system stylesheet and follow the "Earthbound Archive" editorial aesthetic — moody, tactile, zero-radius, with organic brutalist principles.

- **Minimal** (`minimal.html`): Hero, origin blurb, CTA
- **Standard** (`standard.html`): Hero, origin story, product highlight, testimonials, footer

## File Structure

```
cafe/
├── minimal.html          # Variant A
├── standard.html         # Variant B
├── styles.css            # Shared design system
├── image.png             # Brand/logo hero image (beans + scoops)
├── image copy.png        # Atmospheric steaming beans image
└── image copy 2.png      # UI reference (not used in site)
```

No build tools, no JS frameworks. Plain HTML + CSS + Google Fonts.

## Design System (`styles.css`)

### Colors

| Token | Hex | Usage |
|-------|-----|-------|
| Primary | `#8D6E63` | Button fills, key brand color |
| Primary light | `#e4beb2` | Headlines on dark, text accents |
| Primary dim | `#d4a596` | Hover states, secondary accents |
| Primary container | `#4d352b` | Deep tonal containers |
| Secondary | `#3E2723` | Dark brown depth layers |
| Tertiary | `#BF360C` | Burnt orange — CTAs, Origin Stamp |
| Tertiary container | `#721900` | Origin Stamp chip background |
| Background | `#121212` | Page canvas |
| Surface | `#131313` | Primary surface |
| Surface container low | `#1a1614` | First depth tier |
| Surface container | `#211c19` | Second depth tier |
| On-surface | `#e5e2e1` | Body text (never pure white) |
| Outline variant | `rgba(229,226,225,0.15)` | Ghost borders when needed |

### Typography

- **Headlines:** Noto Serif, bold. `display-lg` at 3.5rem with tight letter-spacing (-0.02em). Used for hero title, section headings.
- **Body:** Space Grotesk, regular. 1rem/1.1rem. Navigation, descriptions, data.
- **Labels:** Space Grotesk, small-caps or wide letter-spacing (0.1em). Metadata, tags, serial-number style.

### Texture & Atmosphere

- CSS pseudo-element noise overlay on `body::after` at 2-3% opacity — a repeating noise SVG or data-URI to simulate parchment grit.
- Covers the entire viewport, `pointer-events: none`, `position: fixed`.

### Elevation

- No box-shadow for cards. Depth via tonal background shifts (surface → surface-container-low → surface-container).
- Glassmorphic nav: surface color at 70% opacity + `backdrop-filter: blur(20px)`.
- If a border is required for accessibility: `outline-variant` at 15% opacity only.

### Components

**Buttons (all 0px border-radius):**
- Primary: bg `#8D6E63`, text `#121212`
- Secondary: bg `#3E2723`, text `#e4beb2`
- Inverted: bg `#e4beb2`, text `#3E2723`
- Outlined: transparent bg, ghost border `rgba(229,226,225,0.15)`, text `#e4beb2`
- Hover: shift bg one tonal tier (no glow, no scale)

**Origin Stamp Chip:**
- bg `#721900`, text `#ffb5a1`, small-caps Space Grotesk
- Looks like a branded mark on a wooden crate

**Nav Bar:**
- Glassmorphic (70% opacity, 20px blur), fixed/sticky top
- Logo left, icon links right (home, search, profile — thin-stroke style)
- Icons in warm salmon tones on dark background

**Search Bar:**
- Dark bg (`#1a1614`), no border, warm placeholder text
- Underline on focus using `#8D6E63`

## Page Designs

### Minimal (`minimal.html`)

Sections top to bottom:

1. **Nav** — Glassmorphic sticky bar. Manabao text-logo left. Nav icons right.
2. **Hero** — Full-viewport-height section. `image.png` as background (cover, centered). Text-based Manabao logo (Noto Serif, display-lg) centered with "Coffee from the Dominican Mountains" subtitle below in Space Grotesk. Origin Stamp chip: "Dominican Origin". Large display-lg headline overlapping the image per editorial card rules.
3. **Origin Blurb** — Background shifts to `surface-container-low`. 2-3 sentences in Space Grotesk about Manabao's roots. Generous vertical padding (120px+).
4. **CTA** — Primary button "Discover Our Coffee" centered. Links to `#`.
5. **Footer** — Minimal. Brand mark centered, muted on-surface text. "Manabao" in Noto Serif.

### Standard (`standard.html`)

Sections top to bottom:

1. **Nav** — Same as Minimal.
2. **Hero** — Same as Minimal.
3. **Origin Story** — Two-column layout. Left: `image copy.png` (steaming beans). Right: Noto Serif headline overlapping the image corner (editorial card style). Body text in Space Grotesk describing the Dominican mountain origin. Background: `surface-container-low`.
4. **Product Highlight** — Background shifts to `surface-container`. Placeholder product card: coffee bag image area (placeholder div), product name in headline-sm, tasting notes in body text, price, Primary CTA button. Asymmetric layout — product offset from center.
5. **Testimonials** — Background shifts back to `surface`. 2-3 pull quotes in large Noto Serif italic. Attribution in Space Grotesk label style. Generous whitespace between quotes.
6. **Footer** — Full footer. Logo, tagline, placeholder nav links (Our Story, Products, Contact), social media placeholder icons. All in muted on-surface colors.

## Constraints

- All CTA/links are `#` placeholder anchors.
- No JavaScript required (CSS-only interactions for hover states).
- No rounded corners anywhere — 0px border-radius on everything.
- No 1px solid borders — structure via tonal shifts only.
- No pure white (`#FFFFFF`) — always `#e5e2e1` or warmer.
- No standard blue links — use primary or tertiary colors.
- Images referenced as relative paths (`image.png`, `image copy.png`).

## Responsiveness

- Mobile-first with breakpoints at 768px (tablet) and 1200px (desktop).
- Hero image stays full-bleed at all sizes.
- Two-column layouts stack to single column on mobile.
- Nav icons collapse; logo stays visible.
- Typography scales down: display-lg from 3.5rem (desktop) to 2.5rem (mobile).
