# Proposal: Personal Blog (personal-blog)

## What & Why
- **Goal**: Build a personal blog that showcases your planning, projects, and thoughts.
- **Key requirements** (from the conversation):
  1. **Single‑page** architecture with anchor navigation (lightweight, no routing).
  2. **Content source**: a local `data/blog.json` file that can be edited directly – changes are reflected on the site after deployment.
  3. **Deploy** on Vercel under the custom domain `xiaoliang.tech`.
  4. **Dynamic visual flair**: card‑flip on hover, scroll‑parallax background, micro‑animations for buttons (already present).
  5. **Future‑proof**: keep the implementation simple now, but allow later enhancements (search, comments, multi‑page).

## Success Criteria
- The site loads fast (static HTML + Tailwind CDN).
- Updating `blog.json` and redeploying shows new content without code changes.
- Animations work across modern browsers.
- The domain resolves to the Vercel deployment.

## Non‑Goals (out of scope for now)
- Server‑side search, comment system, authentication, or RSS feed.
- Multi‑page routing or complex build pipelines.

---
*Prepared for the `personal-blog` change.*
