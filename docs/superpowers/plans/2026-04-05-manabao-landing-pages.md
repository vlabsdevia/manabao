# Manabao Landing Pages Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build two static landing page variants (minimal and standard) for Manabao coffee brand using a shared design system stylesheet.

**Architecture:** Plain HTML + CSS, no build tools. One shared `styles.css` implements the full design system (colors, typography, components, texture). Two HTML files (`minimal.html`, `standard.html`) each compose sections from the shared styles. Google Fonts loaded via `<link>`.

**Tech Stack:** HTML5, CSS3, Google Fonts (Noto Serif, Space Grotesk)

---

## File Structure

| File | Responsibility |
|------|---------------|
| `styles.css` | Design system: CSS custom properties, typography, noise texture, button variants, nav, Origin Stamp chip, section layouts, responsive breakpoints |
| `minimal.html` | Variant A: nav, hero, origin blurb, CTA, minimal footer |
| `standard.html` | Variant B: nav, hero, origin story, product highlight, testimonials, full footer |

---

### Task 1: Design System Foundation (`styles.css` — Reset, Custom Properties, Typography)

**Files:**
- Create: `styles.css`

- [ ] **Step 1: Create `styles.css` with reset and custom properties**

```css
@import url('https://fonts.googleapis.com/css2?family=Noto+Serif:ital,wght@0,400;0,700;1,400&family=Space+Grotesk:wght@400;500;700&display=swap');

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  /* Colors */
  --primary: #8D6E63;
  --primary-light: #e4beb2;
  --primary-dim: #d4a596;
  --primary-container: #4d352b;
  --secondary: #3E2723;
  --tertiary: #BF360C;
  --tertiary-container: #721900;
  --background: #121212;
  --surface: #131313;
  --surface-container-low: #1a1614;
  --surface-container: #211c19;
  --on-surface: #e5e2e1;
  --on-primary: #121212;
  --outline-variant: rgba(229, 226, 225, 0.15);

  /* Typography */
  --font-headline: 'Noto Serif', serif;
  --font-body: 'Space Grotesk', sans-serif;

  /* Spacing */
  --section-padding: 120px 24px;
  --section-padding-mobile: 80px 16px;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: var(--font-body);
  background-color: var(--background);
  color: var(--on-surface);
  line-height: 1.6;
  -webkit-font-smoothing: antialiased;
}

a {
  color: var(--primary-light);
  text-decoration: none;
}

a:hover {
  color: var(--primary-dim);
}

img {
  max-width: 100%;
  display: block;
}
```

- [ ] **Step 2: Add typography classes**

Append to `styles.css`:

```css
/* Typography Scale */
.display-lg {
  font-family: var(--font-headline);
  font-size: 3.5rem;
  font-weight: 700;
  letter-spacing: -0.02em;
  line-height: 1.1;
  color: var(--primary-light);
}

.headline-sm {
  font-family: var(--font-headline);
  font-size: 1.75rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  line-height: 1.2;
  color: var(--primary-light);
}

.body-text {
  font-family: var(--font-body);
  font-size: 1rem;
  line-height: 1.7;
  color: var(--on-surface);
}

.label-sm {
  font-family: var(--font-body);
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--on-surface);
}

@media (max-width: 768px) {
  .display-lg {
    font-size: 2.5rem;
  }

  .headline-sm {
    font-size: 1.35rem;
  }
}
```

- [ ] **Step 3: Verify file exists**

Run: `ls -la styles.css`
Expected: file exists with non-zero size

- [ ] **Step 4: Commit**

```bash
git add styles.css
git commit -m "feat: add design system foundation — reset, colors, typography"
```

---

### Task 2: Noise Texture, Buttons, and Components (`styles.css`)

**Files:**
- Modify: `styles.css`

- [ ] **Step 1: Add noise texture overlay**

Append to `styles.css`:

```css
/* Noise Texture Overlay */
body::after {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 9999;
  opacity: 0.03;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
  background-repeat: repeat;
  background-size: 256px 256px;
}
```

- [ ] **Step 2: Add button variants**

Append to `styles.css`:

```css
/* Buttons — all 0px border-radius */
.btn {
  display: inline-block;
  padding: 14px 32px;
  font-family: var(--font-body);
  font-size: 0.875rem;
  font-weight: 500;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  border: none;
  border-radius: 0;
  cursor: pointer;
  text-decoration: none;
  transition: background-color 0.3s ease;
}

.btn-primary {
  background-color: var(--primary);
  color: var(--on-primary);
}

.btn-primary:hover {
  background-color: var(--primary-dim);
  color: var(--on-primary);
}

.btn-secondary {
  background-color: var(--secondary);
  color: var(--primary-light);
}

.btn-secondary:hover {
  background-color: var(--primary-container);
  color: var(--primary-light);
}

.btn-inverted {
  background-color: var(--primary-light);
  color: var(--secondary);
}

.btn-inverted:hover {
  background-color: var(--primary-dim);
  color: var(--secondary);
}

.btn-outlined {
  background-color: transparent;
  color: var(--primary-light);
  border: 1px solid var(--outline-variant);
}

.btn-outlined:hover {
  background-color: var(--surface-container-low);
  color: var(--primary-light);
}
```

- [ ] **Step 3: Add Origin Stamp chip and nav styles**

Append to `styles.css`:

```css
/* Origin Stamp Chip */
.origin-stamp {
  display: inline-block;
  padding: 6px 16px;
  background-color: var(--tertiary-container);
  color: #ffb5a1;
  font-family: var(--font-body);
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  border-radius: 0;
}

/* Glassmorphic Nav */
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 40px;
  background-color: rgba(19, 19, 19, 0.7);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
}

.nav-logo {
  font-family: var(--font-headline);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--primary-light);
  letter-spacing: -0.01em;
}

.nav-links {
  display: flex;
  gap: 24px;
  list-style: none;
}

.nav-links a {
  color: var(--primary-dim);
  font-family: var(--font-body);
  font-size: 0.85rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  transition: color 0.3s ease;
}

.nav-links a:hover {
  color: var(--primary-light);
}

@media (max-width: 768px) {
  .nav {
    padding: 14px 20px;
  }

  .nav-links {
    gap: 16px;
  }

  .nav-links a {
    font-size: 0.75rem;
  }
}
```

- [ ] **Step 4: Commit**

```bash
git add styles.css
git commit -m "feat: add noise texture, button variants, origin stamp, nav"
```

---

### Task 3: Section Layout Utilities (`styles.css`)

**Files:**
- Modify: `styles.css`

- [ ] **Step 1: Add hero, section, and layout utilities**

Append to `styles.css`:

```css
/* Hero Section */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding: 80px 24px;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    rgba(18, 18, 18, 0.4) 0%,
    rgba(18, 18, 18, 0.6) 50%,
    rgba(18, 18, 18, 0.9) 100%
  );
}

.hero-content {
  position: relative;
  z-index: 1;
  max-width: 700px;
}

.hero-content .display-lg {
  margin-bottom: 16px;
}

.hero-subtitle {
  font-family: var(--font-body);
  font-size: 1rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--primary-dim);
  margin-bottom: 24px;
}

.hero-content .origin-stamp {
  margin-bottom: 32px;
}

/* Sections */
.section {
  padding: var(--section-padding);
}

.section--surface {
  background-color: var(--surface);
}

.section--low {
  background-color: var(--surface-container-low);
}

.section--container {
  background-color: var(--surface-container);
}

.section-inner {
  max-width: 1100px;
  margin: 0 auto;
}

/* Two-Column Editorial Layout */
.editorial-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0;
  align-items: center;
}

.editorial-grid__image {
  position: relative;
  overflow: hidden;
}

.editorial-grid__image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  min-height: 400px;
}

.editorial-grid__text {
  padding: 60px;
  position: relative;
}

.editorial-grid__text .headline-sm {
  position: relative;
  left: -40px;
  margin-bottom: 24px;
}

.editorial-grid__text .body-text {
  margin-bottom: 32px;
}

/* Product Highlight — Asymmetric */
.product-card {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 60px;
  align-items: center;
}

.product-image-placeholder {
  width: 100%;
  aspect-ratio: 3 / 4;
  background: linear-gradient(135deg, var(--primary-container), var(--secondary));
}

.product-info .headline-sm {
  margin-bottom: 12px;
}

.product-info .body-text {
  margin-bottom: 8px;
}

.product-price {
  font-family: var(--font-headline);
  font-size: 1.5rem;
  color: var(--primary-light);
  margin: 20px 0 28px;
}

/* Testimonials */
.testimonial {
  max-width: 700px;
  margin: 0 auto;
  padding: 60px 0;
  text-align: center;
}

.testimonial-quote {
  font-family: var(--font-headline);
  font-size: 1.5rem;
  font-style: italic;
  color: var(--primary-light);
  line-height: 1.6;
  margin-bottom: 20px;
}

.testimonial-attribution {
  font-family: var(--font-body);
  font-size: 0.75rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--primary-dim);
}

/* Footer */
.footer {
  background-color: var(--surface-container-low);
  padding: 60px 24px;
  text-align: center;
}

.footer-logo {
  font-family: var(--font-headline);
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary-light);
  margin-bottom: 8px;
}

.footer-tagline {
  font-family: var(--font-body);
  font-size: 0.8rem;
  color: var(--primary-dim);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-bottom: 32px;
}

.footer-nav {
  display: flex;
  justify-content: center;
  gap: 32px;
  list-style: none;
  margin-bottom: 40px;
}

.footer-nav a {
  font-family: var(--font-body);
  font-size: 0.8rem;
  color: var(--on-surface);
  letter-spacing: 0.05em;
  text-transform: uppercase;
  transition: color 0.3s ease;
}

.footer-nav a:hover {
  color: var(--primary-light);
}

.footer-bottom {
  font-size: 0.7rem;
  color: rgba(229, 226, 225, 0.4);
  letter-spacing: 0.05em;
}

/* Responsive */
@media (max-width: 768px) {
  .section {
    padding: var(--section-padding-mobile);
  }

  .editorial-grid {
    grid-template-columns: 1fr;
  }

  .editorial-grid__text {
    padding: 40px 20px;
  }

  .editorial-grid__text .headline-sm {
    left: 0;
  }

  .product-card {
    grid-template-columns: 1fr;
    gap: 32px;
  }

  .footer-nav {
    flex-direction: column;
    gap: 16px;
  }
}
```

- [ ] **Step 2: Commit**

```bash
git add styles.css
git commit -m "feat: add hero, section, editorial grid, product, testimonial, and footer layouts"
```

---

### Task 4: Minimal Landing Page (`minimal.html`)

**Files:**
- Create: `minimal.html`

- [ ] **Step 1: Create `minimal.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Manabao — Coffee from the Dominican Mountains</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <!-- Nav -->
  <nav class="nav">
    <a href="#" class="nav-logo">Manabao</a>
    <ul class="nav-links">
      <li><a href="#">Origin</a></li>
      <li><a href="#">Shop</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>

  <!-- Hero -->
  <section class="hero" style="background-image: url('image.png');">
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <span class="origin-stamp">Dominican Origin</span>
      <h1 class="display-lg">Manabao</h1>
      <p class="hero-subtitle">Coffee from the Dominican Mountains</p>
    </div>
  </section>

  <!-- Origin Blurb -->
  <section class="section section--low">
    <div class="section-inner" style="max-width: 650px; text-align: center;">
      <h2 class="headline-sm" style="margin-bottom: 24px;">Rooted in the Earth</h2>
      <p class="body-text">
        Born in the misty peaks of the Cordillera Central, Manabao coffee is cultivated by 
        hand at elevations above 1,200 meters. Each bean carries the volcanic soil, the 
        mountain rain, and the patience of generations of Dominican farmers.
      </p>
      <div style="margin-top: 48px;">
        <a href="#" class="btn btn-primary">Discover Our Coffee</a>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="footer">
    <div class="footer-logo">Manabao</div>
    <p class="footer-bottom">&copy; 2026 Manabao. All rights reserved.</p>
  </footer>

</body>
</html>
```

- [ ] **Step 2: Open in browser to verify**

Run: `open minimal.html`
Expected: Dark page with hero image, Manabao logo, origin blurb, and CTA button. No rounded corners. Warm tones. Noise texture visible on close inspection.

- [ ] **Step 3: Commit**

```bash
git add minimal.html
git commit -m "feat: add minimal landing page variant"
```

---

### Task 5: Standard Landing Page (`standard.html`)

**Files:**
- Create: `standard.html`

- [ ] **Step 1: Create `standard.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Manabao — Coffee from the Dominican Mountains</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <!-- Nav -->
  <nav class="nav">
    <a href="#" class="nav-logo">Manabao</a>
    <ul class="nav-links">
      <li><a href="#">Origin</a></li>
      <li><a href="#">Shop</a></li>
      <li><a href="#">Press</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>

  <!-- Hero -->
  <section class="hero" style="background-image: url('image.png');">
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <span class="origin-stamp">Dominican Origin</span>
      <h1 class="display-lg">Manabao</h1>
      <p class="hero-subtitle">Coffee from the Dominican Mountains</p>
      <a href="#origin" class="btn btn-outlined" style="margin-top: 16px;">Our Story</a>
    </div>
  </section>

  <!-- Origin Story -->
  <section id="origin" class="section section--low">
    <div class="section-inner">
      <div class="editorial-grid">
        <div class="editorial-grid__image">
          <img src="image copy.png" alt="Freshly roasted coffee beans with rising steam">
        </div>
        <div class="editorial-grid__text">
          <span class="label-sm" style="display: block; margin-bottom: 16px;">The Origin</span>
          <h2 class="headline-sm">From the Peaks of Cordillera Central</h2>
          <p class="body-text">
            In the Dominican Republic's highest mountain range, where the clouds settle 
            between the peaks, Manabao coffee has been cultivated for generations. Our farmers 
            work at elevations above 1,200 meters, hand-picking only the ripest cherries 
            from volcanic soil that gives each cup its distinctive depth and character.
          </p>
          <p class="body-text">
            Every batch is micro-lot processed, sun-dried on raised beds, and roasted in 
            small quantities to preserve the terroir of the Dominican highlands.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- Product Highlight -->
  <section class="section section--container">
    <div class="section-inner">
      <span class="label-sm" style="display: block; text-align: center; margin-bottom: 48px;">Featured</span>
      <div class="product-card">
        <div class="product-image-placeholder"></div>
        <div class="product-info">
          <span class="origin-stamp" style="margin-bottom: 16px;">Single Origin</span>
          <h3 class="headline-sm" style="margin-top: 16px;">Manabao Reserve</h3>
          <p class="body-text">
            Tasting Notes: Dark chocolate, toasted walnut, brown sugar with a 
            smooth, full-bodied finish.
          </p>
          <p class="body-text label-sm" style="margin-top: 8px;">
            Process: Washed &bull; Altitude: 1,400m &bull; Varietal: Typica
          </p>
          <div class="product-price">$24.00</div>
          <a href="#" class="btn btn-primary">Add to Cart</a>
        </div>
      </div>
    </div>
  </section>

  <!-- Testimonials -->
  <section class="section section--surface">
    <div class="section-inner">
      <span class="label-sm" style="display: block; text-align: center; margin-bottom: 40px;">What They Say</span>

      <div class="testimonial">
        <p class="testimonial-quote">
          "Manabao is what coffee should taste like — honest, complex, and deeply rooted 
          in its origin. A revelation in every cup."
        </p>
        <p class="testimonial-attribution">Coffee Review Magazine</p>
      </div>

      <div class="testimonial">
        <p class="testimonial-quote">
          "The kind of coffee you slow down for. Rich volcanic character with an 
          elegance that lingers."
        </p>
        <p class="testimonial-attribution">James Alderton, Specialty Roaster</p>
      </div>

      <div class="testimonial">
        <p class="testimonial-quote">
          "From the mountains to the cup, you can taste the care in every step 
          of the process."
        </p>
        <p class="testimonial-attribution">Dominican Coffee Collective</p>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="footer">
    <div class="footer-logo">Manabao</div>
    <p class="footer-tagline">Coffee from the Dominican Mountains</p>
    <ul class="footer-nav">
      <li><a href="#">Our Story</a></li>
      <li><a href="#">Products</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    <p class="footer-bottom">&copy; 2026 Manabao. All rights reserved.</p>
  </footer>

</body>
</html>
```

- [ ] **Step 2: Open in browser to verify**

Run: `open standard.html`
Expected: Dark editorial page with hero, two-column origin story with overlapping headline, product highlight with asymmetric layout, three testimonial quotes, and full footer. All warm tones, zero-radius, no borders.

- [ ] **Step 3: Commit**

```bash
git add standard.html
git commit -m "feat: add standard landing page variant"
```

---

### Task 6: Final Visual QA and Polish

**Files:**
- Possibly modify: `styles.css`, `minimal.html`, `standard.html`

- [ ] **Step 1: Check both pages at desktop width (1200px+)**

Run: `open minimal.html && open standard.html`
Verify:
- Noise texture is visible but subtle
- Nav is glassmorphic with blur effect
- Hero image fills viewport
- All text is `#e5e2e1` (not pure white)
- Buttons are sharp 0px radius
- No rounded corners anywhere
- Origin Stamp looks like a branded crate mark
- Generous whitespace between sections

- [ ] **Step 2: Check responsive at mobile width (375px)**

Resize browser or use DevTools responsive mode.
Verify:
- Editorial grid stacks to single column
- Product card stacks to single column
- Typography scales down (display-lg to 2.5rem)
- Nav remains usable
- Footer nav stacks vertically

- [ ] **Step 3: Fix any visual issues found**

Address any inconsistencies with the design spec.

- [ ] **Step 4: Final commit**

```bash
git add -A
git commit -m "polish: visual QA fixes for both landing page variants"
```
