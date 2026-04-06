# Design System: High-End Editorial & Artisanal Gritty

## 1. Overview & Creative North Star
The Creative North Star for this design system is **"The Earthbound Archive."** 

This system rejects the sterile, bright-white "tech" aesthetic in favor of a moody, tactile, and highly editorial experience. It is designed to feel like a premium printed monograph or a curator’s private journal. We achieve this by leaning into **Organic Brutalism**: a combination of razor-sharp, zero-radius edges and gritty, atmospheric textures. 

To break the "template" look, layouts must embrace intentional asymmetry—overlapping text over images, dramatic vertical white space, and a typography scale that values massive headline-to-body contrast. The design should feel "found" and "handcrafted," mirroring the artisanal nature of Dominican mountain coffee.

---

## 2. Colors: Tonal Depth & Soul
Our palette is rooted in the earth. It moves from deep volcanic blacks to sun-baked umber.

### Core Tokens
*   **Background (`#131313`):** The primary canvas. Never pure black, but a deep charcoal that allows for "lower" depth tiers.
*   **Primary (`#e4beb2` / `primary_container: #4d352b`):** Use these warm, sepia tones for moments of high emphasis.
*   **Tertiary (`#ffb5a1` / `tertiary_container: #721900`):** These burnt orange/umber tones evoke rusted metal and coffee cherries. Use sparingly for critical calls to action.

### The "No-Line" Rule
**Explicit Instruction:** Do not use 1px solid borders for sectioning. Structural boundaries must be created through background shifts.
*   Place a `surface_container_low` section directly against a `surface` background to define a change in content.
*   Avoid the "boxed" look. If a container is needed, let the tonal shift do the work.

### Signature Textures & Soul
To move beyond flat hex codes, apply a subtle noise overlay (2-3% opacity) across the entire UI to mimic parchment or grit. Use gradients transitioning from `primary` to `primary_container` on interactive elements to provide a "metallic" or "liquid" depth that feels premium.

---

## 3. Typography: The Editorial Voice
The typography is a dialogue between the poetic and the technical.

*   **Display & Headlines (Noto Serif):** Bold, high-contrast, and unapologetic. Large headlines (`display-lg`: 3.5rem) should feel like titles on a book cover. Use tight letter-spacing for a sophisticated, "pressed" look.
*   **Body & Functional Text (Space Grotesk):** A clean, technical Sans-Serif. Its geometric nature provides a "modern blueprint" contrast to the organic Serif. Use it for descriptions, data, and navigation.
*   **Labels:** Small-caps or wide letter-spacing on `label-sm` should be used for metadata, mimicking the serial numbers on industrial coffee sacks.

---

## 4. Elevation & Depth: Tonal Layering
We move away from traditional drop shadows in favor of physical stacking.

*   **The Layering Principle:** Depth is achieved by "stacking" surface-container tiers. 
    *   *Example:* Place a `surface_container_lowest` card on a `surface_container_low` section. This creates a "recessed" or "carved" effect.
*   **Ambient Shadows:** If an element must "float" (e.g., a modal), use an extra-diffused shadow (Blur: 40px+) at 5% opacity. The shadow color should be a tinted version of `on_surface` (warm grey) rather than pure black.
*   **Glassmorphism:** For top navigation or floating action bars, use `surface` colors at 70% opacity with a `20px` backdrop blur. This allows the "gritty" textures of the background to bleed through, integrating the UI.
*   **The "Ghost Border":** If accessibility requires a border, use `outline_variant` at 15% opacity. High-contrast borders are strictly prohibited.

---

## 5. Components: Rugged Precision

### Buttons
*   **Primary:** Zero border radius (`0px`). Background: `primary`. Text: `on_primary`. 
*   **Secondary/Outlined:** No solid border. Use a "Ghost Border" or a subtle `surface_variant` background.
*   **States:** On hover, shift the background color by one tonal tier (e.g., `primary` to `primary_fixed_dim`) rather than using a glow.

### Cards & Lists
*   **Rule:** No divider lines. Separate list items using `16px` or `24px` of vertical white space or alternating `surface_container` subtle shifts.
*   **Editorial Cards:** Images should be the hero. Overlap the `headline-sm` text onto the corner of the image to break the grid.

### Input Fields
*   **Style:** Minimalist under-lines only using `outline_variant`. 
*   **Focus:** Transition the underline to `primary`. No "glow" effects. Text should be `spaceGrotesk` to maintain a technical feel.

### Signature Component: The "Origin Stamp"
*   A specialized `Chip` variant using `tertiary_container`. Use it for "Dominican Origin" or "Artisanal" tags. It should look like a branded mark on a wooden crate.

---

## 6. Do's and Don'ts

### Do
*   **DO** use large, atmospheric imagery of coffee beans, smoke, and mountain landscapes.
*   **DO** leave "uncomfortable" amounts of white space (negative space) to emphasize the editorial feel.
*   **DO** align the 'Manabao' logo with the 'Coffee from the Dominican Mountains' subtitle in a way that feels like a seal of quality, often centered or tucked into a corner as a "stamp."
*   **DO** use 0px border radius for everything. Sharpness equals premium.

### Don't
*   **DON'T** use rounded corners. It breaks the "Artisanal Brutalist" aesthetic.
*   **DON'T** use standard blue for links. Use `primary` or `tertiary`.
*   **DON'T** use pure white (`#FFFFFF`) for text. Use `on_surface` (`#e5e2e1`) to keep the atmosphere moody and easy on the eyes in low light.
*   **DON'T** use generic icons. Use thin-stroke, technical icons that match the `spaceGrotesk` aesthetic.