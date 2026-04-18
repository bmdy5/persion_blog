# Design: Personal Blog Enhancement

## Visual Language
- **Base Theme**: Dark background `#0d0f0d` with light accent `#f7f7f3` (existing). 
- **Accent Colors**: `#ffff00` (yellow) and `#a80096` (magenta) for hover/interactive states.
- **Typography**: Use existing Tailwind fonts – `Epilogue` for headings, `Work Sans` for body, `Space Grotesk` for labels.
- **Rounded Elements**: Only avatar container and tool‑card backgrounds use `rounded-lg` (8 px). All other containers keep `border-radius: 0` to preserve Neo‑Brutalism.
- **Glass‑morphism**: Avatar outer frame and tool‑card background apply `backdrop-filter: blur(8px)` with semi‑transparent background (`bg-white/10`).

## Layout
1. **Hero Section** (top)
   - Avatar (circular, drop‑shadow, optional glass frame) on the left.
   - Short intro text on the right.
2. **Timeline Section**
   - Vertical line (`border-l-4 border-dashed border-inverse-surface`).
   - Each stage is a card (`bg-[#fffdec] border-4 border-inverse-surface`).
   - Card front shows period & brief description; back (on hover) shows “遗憾” notes with hand‑written style.
3. **Projects Grid**
   - `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`.
   - Card uses existing flip animation (`.card`, `.card-inner`).
   - Front: title, short description, tech tags.
   - Back: detailed link/buttons.
4. **Tools Carousel** (footer)
   - Horizontal scroll container `flex overflow-x-auto gap-4`.
   - Each tool card: icon (SVG), name, link button.
   - Hover: background `bg-[#a80096]` with white text, slight scale.

## Interaction Details
- **Avatar**: `hover:scale-105` + subtle hue shift.
- **Timeline Cards**: `hover:translate-x-[2px] hover:translate-y-[2px]` and remove shadow.
- **Project Cards**: full 3D flip on hover (`rotateY(180deg)`).
- **Tool Cards**: `hover:bg-[#a80096] hover:text-[#f7f7f3] scale-95`.
- All transitions `duration-200` for smooth feel.

## Implementation Steps (high‑level)
- Add avatar container with `rounded-full` and optional glass wrapper.
- Build timeline markup and CSS.
- Create project grid component, reuse existing flip CSS.
- Add tool‑card component, fetch icons into `img/tools/`.
- Update Tailwind config if new colors needed.
- Ensure SEO meta tags (title, description, headings) are present.

## Dependencies
- Avatar image placed in `img/` (filename to be provided).
- Tool icons saved as SVGs in `img/tools/`.
- Existing Tailwind setup already provides required utilities.
