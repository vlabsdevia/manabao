# Manabao Cultural Bridge Variants — Design Spec

## Overview

Three new landing page variants exploring the cultural bridge between the Dominican Republic and the Dominican diaspora in Jacksonville, Florida. Each variant tells the same core story — Manabao coffee traveling from DR mountains to a Hispanic tienda in Jacksonville — but through a different language and layout.

All variants share the existing design system (`styles.css`) and follow the "Earthbound Archive" editorial aesthetic.

**Core Theme:** Cultural bridge. A taste of home found 3,000 miles away.

## Variants

### Variant E — "The Bridge" (`bridge.html`) — English

**Language:** English only
**Layout:** Split-screen storytelling — "There" (DR) vs "Here" (Jacksonville) mirrored sections connected by a transitional middle.

**Sections:**

1. **Nav** — Glassmorphic sticky bar. "Manabao" text-logo left. Links: There, Here, Find Us.
2. **Hero — Split** — Two-column full-viewport hero. Left half: Dominican mountain/farm image with dark overlay. Right half: Jacksonville bodega storefront image with dark overlay. Centered headline spanning both: *"From Our Mountains to Your Neighborhood"*. Origin Stamp: "Dominican Origin". Subtitle: *"Manabao — Jacksonville, FL"*.
3. **There (DR)** — Full-bleed farm image section (journey-image style, 70vh). Editorial grid below: image of coffee harvest on one side, text on the other. Headline: *"Where It Begins"*. Body text about the farmers, the Cordillera Central, generations of cultivation. Background: `surface-container-low`.
4. **Transition Band** — Full-width quote band. Dark `secondary` background. Large Noto Serif text: *"3,000 miles. One family."* Centered, generous padding (100px vertical).
5. **Here (Jacksonville)** — Editorial grid (reversed). Image: bodega interior/shelves. Headline: *"Where It Arrives"*. Body text about the tienda, the owner, why they carry Manabao. Background: `surface-container`.
6. **The Moment** — Full-bleed image section (journey-image style). Image: customer picking up the bag or pouring coffee at home. Caption overlay: *"The Moment It Becomes Home Again"*.
7. **CTA Section** — Centered text block. Headline: *"Find Manabao Near You"*. Body: short paragraph about availability. Primary button: *"Locate a Store"*. Background: `surface-container-low`.
8. **Footer** — Standard footer with links to other variants.

**Unique CSS:** `.hero-split` — two-column hero with each half holding a background image. Uses `grid-template-columns: 1fr 1fr` at desktop, stacks on mobile. Headline absolutely positioned to span center.

---

### Variant F — "El Puente" (`puente.html`) — Spanish

**Language:** Spanish only
**Layout:** Vertical scroll narrative — single centered column, intimate and text-forward, like a letter being read. Inspired by long-form editorial/magazine storytelling.

**Sections:**

1. **Nav** — Glassmorphic sticky bar. "Manabao" text-logo left. Links: La Tierra, El Viaje, La Tienda, El Sabor.
2. **Hero** — Full-bleed bodega interior image, warm lighting. Dark overlay. Headline: *"De Nuestras Montañas a Tu Mesa"*. Subtitle: *"Café dominicano en Jacksonville"*. Origin Stamp: *"Origen Dominicano"*.
3. **La Tierra** — Centered narrow column (max-width 700px). Label: *"01 — La Tierra"*. Headline: *"Donde Todo Comienza"*. Body text about the Dominican soil, the farmers, the tradition of growing coffee in the Cordillera Central. Pull quote in large Noto Serif italic: *"Cada grano lleva la historia de nuestras montañas."* Background: `surface-container-low`.
4. **El Viaje** — Dark atmospheric section. Background: `secondary`. Full-width. Centered text. Label: *"02 — El Viaje"*. Headline: *"Cruzando el Mar"*. Shorter body text about the journey — from mountain to port to Florida. Moody, minimal. This section breathes with large vertical padding.
5. **La Tienda** — Editorial grid layout. Image: bodega exterior or shelves with Manabao bags. Label: *"03 — La Tienda"*. Headline: *"Un Pedazo de Casa en Jacksonville"*. Body text about the store owner, the community, what it means to stock Dominican coffee. Background: `surface-container`.
6. **El Sabor de Casa** — Full-bleed image (journey-image style, 70vh). Image: someone drinking coffee, eyes closed, a moment of peace. Caption overlay with label: *"04 — El Sabor"*. Below: centered text section. Headline: *"El Primer Sorbo Sabe a Casa"*. Emotional body text about the taste of home. Background: `surface-container-low`.
7. **CTA** — Centered. Headline: *"Encuentra Manabao Cerca de Ti"*. Primary button: *"Buscar Tienda"*.
8. **Footer** — Standard footer, link text in Spanish.

**Unique CSS:** `.narrative-section` — centered narrow column (max-width 700px) with generous vertical padding (140px). `.narrative-step` — numbered step label styled like the journey variant's step numbers but smaller and inline.

---

### Variant G — "De Allá Pa'cá" (`dealla.html`) — Spanglish

**Language:** Natural code-switching between Spanish and English. Headlines may be Spanish, body English, or mixed within the same sentence. Reflects how Dominican-Americans actually speak.
**Layout:** Mosaic/collage energy — asymmetric grids, overlapping elements, more dynamic and youthful than the other variants.

**Sections:**

1. **Nav** — Glassmorphic sticky bar. "Manabao" text-logo left. Links: La Historia, The Store, Búscalo.
2. **Hero** — Collage-style hero. Multiple images layered/tiled (mosaic grid from craft variant, adapted). Images: farm, bodega, coffee cup, neighborhood. Headline: *"De Allá Pa'cá"*. Subtitle: *"Same coffee. Same roots. New neighborhood."* Origin Stamp: *"Dominican · Jacksonville"*.
3. **Community Mosaic** — Grid of 4-6 image tiles with short captions mixing Spanish and English. Examples: *"La cosecha — the harvest"*, *"El anaquel — on the shelf"*, *"Mi cocina — my kitchen"*. Each tile has an overlay caption. Uses the mosaic component from craft variant with modifications.
4. **Quote Band** — Full-width. *"Esto no es solo café — this is where we come from."* Large Noto Serif, centered.
5. **The Story Block** — Asymmetric two-column. Left: large image of the bodega. Right: text mixing languages naturally. Headline: *"Not Just a Store"*. Body: *"Es el lugar donde encuentras lo tuyo. The coffee your abuela made, the brand from back home, sitting right there on the shelf between the Bustelo and the Pilón."* Background: `surface-container-low`.
6. **Flip Section** — Reversed asymmetric two-column. Left: text. Right: image of DR farm. Headline: *"Directo de la Loma"*. Body: *"Straight from the mountain. No middlemen, no corporate roasters — just Dominican farmers and the families who know what good coffee tastes like."* Background: `surface-container`.
7. **CTA** — Centered. Headline: *"Get Yours / Búscalo Aquí"*. Two buttons side by side: Primary *"Find a Store"* and Secondary *"Nuestra Historia"*.
8. **Footer** — Standard footer, mixed language links.

**Unique CSS:** `.collage-hero` — mosaic grid adapted for hero use (3 columns, varied row heights). `.caption-overlay` — small text overlay on mosaic tiles with label styling.

---

## Shared Elements

All three variants use:
- Same color tokens, typography, and texture overlay from `styles.css`
- Glassmorphic nav
- Standard footer component
- Origin Stamp chip
- 0px border-radius everywhere
- No pure white, no 1px borders
- Placeholder images (gradient fills matching existing `product-image-placeholder` pattern or existing `img/` assets reused)
- All links are `#` placeholders
- No JavaScript

## New CSS Components Needed

| Component | Used By | Description |
|-----------|---------|-------------|
| `.hero-split` | Variant E | Two-column hero, each half with background image |
| `.transition-band` | Variant E | Reuses `.quote-band` from craft — no new CSS needed |
| `.narrative-section` | Variant F | Centered narrow column with generous padding |
| `.narrative-step` | Variant F | Numbered step label (inline, smaller than journey steps) |
| `.collage-hero` | Variant G | Mosaic grid adapted for hero with 3+ images |
| `.caption-overlay` | Variant G | Small label overlay on mosaic tiles |

Existing components reused: `.quote-band`, `.editorial-grid`, `.editorial-grid--reverse`, `.journey-image`, `.journey-image__caption`, `.mosaic`, `.mosaic__item`, `.mosaic__overlay`.

## Placeholder Images

Where real photos aren't available yet, use gradient placeholder divs:
- Farm/mountain scenes: `linear-gradient(135deg, var(--primary-container), var(--secondary))`
- Bodega/store scenes: `linear-gradient(135deg, var(--surface-container), var(--primary-container))`
- People/moments: `linear-gradient(135deg, var(--secondary), var(--tertiary-container))`

Reuse existing images from `img/` where thematically appropriate (e.g., `cherries-branch.png` for harvest, `roasted-steam.png` for roasting, `hero-brand.png` for hero backgrounds).

## Responsiveness

Same breakpoint strategy as existing variants:
- Desktop: multi-column layouts as designed
- 768px and below: all grids collapse to single column, typography scales down, hero-split stacks vertically
- Collage hero (Variant G): simplifies to 2-column or single-column grid on mobile

## File Structure (New)

```
cafe/
├── bridge.html     # Variant E — English
├── puente.html     # Variant F — Spanish
├── dealla.html     # Variant G — Spanglish
├── styles.css      # Updated with new components
└── index.html      # Updated hub with 3 new cards
```
