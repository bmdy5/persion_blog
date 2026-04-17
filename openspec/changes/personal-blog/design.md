# Design: Personal Blog (personal-blog)

## Architecture Overview
- **Single‑page application** built with pure HTML, Tailwind CSS (via CDN) and vanilla JavaScript.
- **Data source**: `data/blog.json` – a static JSON file that lives in the repository. The page fetches it at runtime and renders the content dynamically.
- **Routing**: Anchor‑based navigation (`#plan`, `#projects`, etc.) – no client‑side router required.
- **Animations**:
  1. **Card flip** – CSS 3D transform on `.card:hover .card-inner`.
  2. **Scroll parallax** – background‑attachment: fixed on the hero section and a tiny `translateY` on the title tied to `scrollY`.
  3. **Micro‑animations** – already present on buttons (translate + shadow removal) and will be reused for other interactive elements.
- **Deployment**: Static site hosted on Vercel, bound to the custom domain `xiaoliang.tech`. Vercel serves the `public` folder (our `index.html`/`code.html`) and any static assets (`data/blog.json`).

## Technical Stack
| Layer | Technology |
|-------|------------|
| Markup | HTML5 |
| Styling | Tailwind CSS (CDN) – custom config for Neo‑Brutalism colors, fonts, hard borders, zero radius |
| Logic | Vanilla JavaScript (ES6) – `fetch` for JSON, DOM manipulation, scroll listener for parallax |
| Build | None – pure static files. Optional `npm run dev` with Vite can be added later for local hot‑reload.
| Hosting | Vercel (static) |

## Key Implementation Details
1. **Create `data/blog.json`** – an array of objects with fields `title`, `slug`, `tags`, `content` (HTML string) and optional `cover`.
2. **HTML skeleton** – keep the existing `code.html` structure, but add two main sections:
   ```html
   <section id="plan" class="...">…</section>
   <section id="projects" class="...">…</section>
   ```
   The navigation links in the header will point to `#plan` and `#projects`.
3. **Render function** – after `DOMContentLoaded`, fetch the JSON, iterate over items, and inject a card into the appropriate container based on `tags`.
4. **Card component** – markup:
   ```html
   <div class="card border-4 border-inverse-surface shadow-[4px_4px_0px_0px_#0d0f0d] overflow-hidden">
     <div class="card-inner relative transition-transform duration-300">
       <div class="card-front p-4">
         <h3 class="font-headline font-black text-xl mb-2">${title}</h3>
         <div class="content">${content}</div>
       </div>
       <div class="card-back p-4 bg-[#fffdec] hidden">
         <!-- optional back side, e.g., tech stack -->
       </div>
     </div>
   </div>
   ```
   CSS for flip (add to `<style>`):
   ```css
   .card { perspective: 1000px; }
   .card-inner { transform-style: preserve-3d; transition: transform .3s; }
   .card:hover .card-inner { transform: rotateY(180deg); }
   .card-front, .card-back { backface-visibility: hidden; position: absolute; inset:0; }
   .card-back { transform: rotateY(180deg); }
   ```
5. **Parallax** – on the hero section:
   ```css
   .hero-bg { background-attachment: fixed; background-size: cover; }
   ```
   JS snippet:
   ```js
   window.addEventListener('scroll', () => {
     const title = document.querySelector('.hero-title');
     title.style.transform = `translateY(${window.scrollY * 0.2}px)`;
   });
   ```
6. **Micro‑animations** – already present for language toggle and dev‑mode; reuse the same Tailwind utility classes for new buttons.
7. **SEO basics** – add a `<title>` that reflects the site name, a `<meta name="description" content="Personal blog of Liang Ge – planning, projects, thoughts.">`, and use semantic tags (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`).
8. **Vercel configuration** – no special config needed; ensure the `data` folder is inside the repository so Vercel serves it as a static asset.

## Future Extensibility
- **Search** – integrate `lunr.js` and index the JSON content.
- **Comments** – embed Giscus or Utterances later.
- **Multi‑page** – migrate to Astro/Next.js; the JSON can become a data source for generated static pages.
- **CMS** – replace the static JSON with a Notion or headless‑CMS sync when the content volume grows.

---
*Design document for the `personal-blog` change.*
