# Zordere — Astro Rebuild

## Brand palette — LOCKED
As of this decision, Zordere's palette is **Charcoal-Teal / Aged Bronze / Bone** — not navy/gold/ivory. That combination reads too close to Waysoroh's ceremonial register (a separate venture); Zordere's identity is deliberately closer to a calibrated instrument — patina, precision, structure — than to gold-leaf ceremony. Reasoning and comparison mockup preserved in chat history; the short version: teal carries a genuine ancient-*and*-modern duality (oxidized bronze/malachite *and* scientific-instrument/terminal-display) that gold-on-navy doesn't.

All tokens live under their original variable names in `src/styles/global.css` (`--navy`, `--gold`, `--ivory`, etc.) — only the hex values changed, so nothing elsewhere in the codebase needed touching. `HeroSky.astro`'s right-side aurora ribbon and horizon band were also rebalanced from yellow-green/gold toward bronze/teal to match. Any new page or component should pull from these variables rather than hardcoding hex values, or this decision silently erodes page by page.

## What's here right now
- `astro.config.mjs`, `package.json`, `tsconfig.json` — standard Astro project setup.
- `src/styles/global.css` — every design token (colors, fonts, spacing) extracted from the current live site, plus shared button/utility classes.
- `src/components/Header.astro`, `Footer.astro` — the nav and footer, written once. Every page pulls from these instead of duplicating markup.
- `src/components/HeroSky.astro` — the layered nebula/aurora hero background, ported from the original SPA and rebalanced to the locked palette.
- `src/layouts/BaseLayout.astro` — shared `<head>`, meta tags, canonical URL, font loading, and the Header/Footer wrapper.
- `src/pages/index.astro` — the new Home page: thesis + three entry points, not the full site crammed into one scroll.

## What's NOT here yet
`/approach/`, `/frameworks/`, `/manifesto/`, `/services/`, `/legibility-score/` don't exist as pages yet — Home currently links to URLs that will 404 until each is built. This was the first slice: prove the foundation works before migrating 7,000 lines of content into it.

## Running it
This sandbox has no network access, so I couldn't run `npm install` or boot the dev server to visually confirm it — the files are standard, valid Astro syntax, but you should verify locally before trusting it blindly:

```
npm install
npm run dev
```

Then open `http://localhost:4321`.

## Deploying
Push this to the GitHub repo (replacing the current static files), connect it in Vercel, framework preset: **Astro**. Vercel runs the build (`npm install && npm run build`) on its own servers — no local install required for deployment, only for previewing.

## Next slices (in order)
1. `/approach/` and `/manifesto/` — content already exists in the old `index.html`, needs porting into `.astro` pages using this layout.
2. `/frameworks/` — new: one page per concept (RAFU, Perception Engine, Complexity Tax, Interpretation Window, Three Laws). RAFU's page needs its own communication-diagnosis-specific definition — not imported wholesale from Waysoroh's cultural-memory framing.
3. `/services/` — the four tiers, ported from old site.
4. `/legibility-score/` — port the existing working diagnostic tool in as its own Astro page (it's currently static HTML and functionally complete — this is a wrapper job, not a rebuild).
