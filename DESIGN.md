# Design System Document: The Editorial Artifact

## 1. Overview & Creative North Star
**Creative North Star: "The Analog Precisionist"**

This design system rejects the ephemeral, "soft" nature of modern web interfaces in favor of something that feels permanent, physical, and uncompromising. By blending the raw, architectural honesty of Neo-Brutalism with high-end editorial layouts, we create a "Digital Artifact." 

The system moves beyond a standard blog template by embracing **intentional asymmetry** and **physicality**. We treat the screen not as a window, but as a printed canvas where elements are "bolted" onto a persistent dot-grid texture. The aesthetic is loud but disciplined, utilizing heavy weights and hard edges to command authority while using a sophisticated cream base to maintain a premium, archival feel.

---

## 2. Colors & Texture
The palette is built on high-contrast foundations punctuated by "Electric Monochromatics."

### The Palette
- **Base Surface:** `background` (#f7f7f3) — A warm, archival cream that reduces eye strain and provides a premium feel compared to pure white.
- **The Ink:** `on_surface` (#2d2f2d) — Used for body copy.
- **The Frame:** `inverse_surface` (#0d0f0d) — Pure black, used for all structural borders and hard shadows.
- **Vibrant Accents:** 
    - `tertiary_fixed`: Bright Yellow (#ffff00)
    - `secondary`: Vibrant Pink (#a80096)
    - *Additional Accents:* Electric Green and Cyan should be pulled from the extended brand palette to highlight categories or specific interactive states.

### Texture & The Grid
- **The Global Texture:** The entire viewport must sit on a `surface` background with a light gray dot grid overlay. 
- **The "Hard-Line" Rule:** Contrary to standard soft UI, sectioning is defined by **thick, 100% opaque black borders** (`border-4`). 
- **Surface Nesting:** Depth is not achieved through light; it is achieved through layering. A `surface_container` element is "stacked" on the `background` using a hard offset shadow, never a blur.

---

## 3. Typography
Our typography is a dialogue between the "Loud Headline" and the "Technical Annotation."

- **Display & Headlines:** *Epilogue*. A heavy sans-serif. Use `display-lg` (3.5rem) for hero titles. Tighten letter spacing (-0.02em) to create a "blocky" visual weight that mirrors the UI components.
- **Body:** *Work Sans*. Optimized for readability. Use `body-lg` (1rem) for long-form content. 
- **The Technical Layer:** *Space Grotesk* (Monospace feel). Used for `label-md` and `label-sm`. This font acts as the "metadata" of the system—use it for dates, tags, and captions to provide a technical, curated contrast to the heavy headings.

---

## 4. Elevation & Depth: The Physical Offset
In this system, elevation is a physical measurement, not a lighting effect.

- **The Layering Principle:** Every "raised" element (Cards, Buttons, Inputs) must be contained within a `border-4` of `inverse_surface`.
- **Hard Offset Shadows:** Shadows must have **zero blur**. 
    - **Default State:** `4px 4px 0px 0px #0d0f0d`.
    - **High Importance:** `8px 8px 0px 0px #0d0f0d`.
- **The "Physical Press" Interaction:** To simulate a tactile button click, components must use a `translate-x-[4px] translate-y-[4px]` transform while simultaneously setting the `shadow` to `none`. This creates the illusion of the element being physically pushed into the page.

---

## 5. Components

### Buttons
- **Primary:** Background of `tertiary_fixed` (Yellow), `border-4`, black text. On hover, background shifts to `secondary` (Pink).
- **Secondary:** Background of `surface_lowest` (White), `border-2`.
- **Interaction:** Must implement the "Physical Press" (translate + shadow-none).

### Cards & Lists
- **Editorial Cards:** No dividers. Use `border-4` frames. Backgrounds should alternate between `surface_container` and `surface_bright` to define hierarchy.
- **Asymmetric Layouts:** Shift cards 15-30px off the standard grid alignment to create a custom, zine-like feel.

### Input Fields
- **States:** 
    - **Default:** `border-2`, `background: #ffffff`. 
    - **Focus:** `border-4`, background shifts to `surface_container_low`. 
    - **Error:** `border-4` with `on_error_container` (Deep Red) text accents.

### Tooltips & Badges
- **Badges (Chips):** High-contrast blocks using `spaceGrotesk`. `border-2`, no rounded corners. 
- **Tooltips:** Background of `inverse_surface` with `inverse_on_surface` text. No transparency.

---

## 6. Do's and Don'ts

### Do:
- **Do** use `0px` border-radius for everything. Sharp corners are non-negotiable.
- **Do** allow elements to overlap. A card’s hard shadow can bleed over the section below it.
- **Do** use "vibrant" accents sparingly—one primary accent color per section to maintain editorial focus.
- **Do** utilize the `Space Grotesk` labels for "utility" text (e.g., "READ TIME: 5 MIN").

### Don't:
- **Don't** use gradients or blurs. Every color transition must be hard-edged.
- **Don't** use 1px borders. If a line is worth drawing, it must have weight (`border-2` minimum).
- **Don't** use standard "drop shadows." If it isn't a hard-offset "block shadow," it doesn't belong in this system.
- **Don't** use centered layouts for everything. Lean into left-heavy editorial alignments with wide right-hand margins for annotations.