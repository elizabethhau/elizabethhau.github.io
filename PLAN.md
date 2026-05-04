# Portfolio Rebuild Plan — Jekyll → Astro

All content decisions are documented in `CONTEXT.md`. This file tracks implementation progress only.

---

## Phase 1 — Scaffold Astro

Goal: Initialize Astro in the repo root without touching existing files.

- [x] Run `npm create astro@latest . -- --template minimal --no-install --typescript strict`
- [x] Run `npm install`
- [x] Add `.gitignore` entries: `node_modules/`, `dist/`, `.astro/`, `.DS_Store`, `.sass-cache/`, `_site/`
- [x] Verify dev server runs: `npm run dev` → blank page at `localhost:4321`

---

## Phase 2 — Astro Configuration

Goal: Wire up build output and GitHub Pages compatibility before writing any components.

- [x] Edit `astro.config.mjs`: set `site: 'https://elizabethhau.github.io'`, `output: 'static'`
- [x] Create `src/` subdirectories: `components/`, `layouts/`, `pages/`, `styles/`
- [x] Confirm `npm run build` produces a `dist/` directory

---

## Phase 3 — Design System & Global Styles

Goal: Establish all CSS custom properties, typography, and base styles before building any components.

- [x] Install `@fontsource/inter`: `npm install @fontsource/inter`
- [x] Create `src/styles/global.css` with:
  - [x] CSS reset (`* { margin: 0; padding: 0; box-sizing: border-box; }`)
  - [x] `:root` custom properties (colors, fonts) from `wireframes/dark-hybrid.html`
  - [x] Body base styles including dot-grid background texture — always dark, no light mode variant
  - [x] `html { scroll-behavior: smooth; }`
  - [x] `section { scroll-margin-top: 72px; }` — fixes sticky nav covering section headings on anchor link click
  - [x] Reusable utility classes: `.section-label`, `.btn-primary`, `.btn-outline`
  - [x] Inter font import from `@fontsource/inter`

---

## Phase 4 — Layout, Components & Content

Goal: Build every component top to bottom. All content sourced from `CONTEXT.md`.

- [x] **4.1 BaseLayout** — `src/layouts/BaseLayout.astro`
  - Accepts `title` prop, renders `<head>` with charset, viewport, meta description, canonical
  - Open Graph tags: title `Elizabeth Hau — AI Architect & Engineer`, description `Software engineer. Cloud architect. AI engineer. Building data and AI systems end-to-end.` — no OG image for now (add static PNG later when actively sharing)
  - Cloudflare Web Analytics `<script>` tag in `<head>` (token added after manual setup step below)
  - Imports `global.css`
- [x] **Manual step (before first deploy):** Create free Cloudflare account → Web Analytics → Add site → enter `elizabethhau.github.io` → copy the script token → paste into BaseLayout
- [x] **4.2 Static assets** — copy to `public/`:
  - `favicon.png`, `favicon-menlo.png`, `favicon.ico`
  - `assets/pdf/Hau_Elizabeth_Resume.pdf` → `public/Hau_Elizabeth_Resume.pdf`
- [x] **4.3 Nav** — `src/components/Nav.astro`
  - Logo: `elizabeth_hau.sh` (monospace, accent)
  - Links: `#about`, `#skills`, `#experience`, `#projects`, `#contact`
  - Hamburger menu on mobile: links collapse behind a toggle button, JS toggle class, no library needed
- [x] **4.4 Hero** — `src/components/Hero.astro`
  - Label: `// not looking, but listening`
  - H1: `Elizabeth Hau`
  - Tagline: `Software engineer. Cloud architect. AI engineer.`
  - Sub: `The full stack, from infrastructure to intelligence.`
  - CTA: single `#contact` button only — resume download button hidden until updated PDF is ready
- [x] **4.5 About** — `src/components/About.astro`
  - Bio verbatim from `CONTEXT.md`
- [x] **4.6 Skills** — `src/components/Skills.astro`
  - All 5 categories from `CONTEXT.md` (Languages, Cloud & Data, AI/ML, Frameworks, Architecture)
- [x] **4.7 Experience** — `src/components/Experience.astro`
  - J&J Vision (2022–Present)
  - Wayfair (2016–2020)
  - MIT — Leaders for Global Operations (LGO) · M.Eng + MBA, CS & Management (2020–2022)
- [x] **4.8 Projects** — `src/components/Projects.astro`
  - All 5 projects with tags, descriptions, and metric blocks from `CONTEXT.md`
  - Card 5 spans full width
  - Each card has an optional `url` prop — renders an external link icon only when a URL is provided (no current projects have public links)
- [x] **4.9 Contact** — `src/components/Contact.astro`
  - mailto: `elizabeth.h.hau@gmail.com`
- [x] **4.10 Footer** — `src/components/Footer.astro`
  - Copyright + GitHub, LinkedIn, and email icon links (all inline SVG, no icon library)
- [x] **4.11 Index page** — `src/pages/index.astro`
  - Assembles all components in order
- [x] **4.12 404 page** — `src/pages/404.astro`
  - Minimal: centered "page not found" message + "back to home" button, dark hybrid styling

---

## Phase 5 — Responsive CSS

Goal: Ensure layout degrades gracefully on mobile and tablet.

- [x] Mobile (`max-width: 768px`):
  - [x] Nav: reduce padding, wrap links if needed
  - [x] Hero: reduce h1 from 64px → 40px, reduce section padding
  - [x] Skills: switch to single column
  - [x] Experience: stack meta above content
  - [x] Projects: switch to single column, remove card 5 full-width span
- [x] Tablet (`max-width: 1024px`):
  - [x] Skills: switch to 2-column grid

---

## Phase 6 — GitHub Actions Deployment

Goal: Automated deploy to GitHub Pages on push to `master`.

- [x] Create `.github/workflows/deploy.yml` (checkout → setup-node → npm ci → astro build → upload artifact → deploy-pages)
- [x] **Manual step (in browser):** GitHub repo Settings > Pages > Source → set to "GitHub Actions"
- [x] Push and confirm Actions workflow succeeds
- [x] Verify live site at `https://elizabethhau.github.io`

---

## Phase 7 — Jekyll Cleanup

Goal: Remove all Jekyll files after live site is confirmed. Do not start this phase until Phase 6 step 4 is verified.

- [x] Delete Jekyll config files: `Gemfile`, `Gemfile.lock`, `_octopress.yml`, `_config.yml`, `Gruntfile.js`, `feed.xml`, `404.md`
- [x] Delete Jekyll directories: `_layouts/`, `_includes/`, `_sass/`, `_posts/`, `_data/`, `_templates/`
- [x] Delete old page directories: `about/`, `contact/`, `course-work/`, `posts/`, `projects/`, `theme-setup/`
- [x] Delete build artifacts: `_site/`, `.sass-cache/`
- [x] Delete old assets: `images/`, `assets/`
- [x] Delete `index.md` (replaced by `src/pages/index.astro`)
- [x] Commit all deletions, confirm deploy still succeeds

---

## Phase 8 — Verification

Goal: Confirm everything works before declaring done.

- [x] All 6 sections present and in correct order
- [x] Nav anchor links scroll to correct sections
- [x] Resume button hidden (PDF staged at `/Hau_Elizabeth_Resume.pdf` for when ready)
- [x] Contact button opens mailto to `elizabeth.h.hau@gmail.com`
- [x] Dot-grid background visible on live site
- [x] Lighthouse: Performance 99, Accessibility 100, Best Practices 96, SEO 100
- [x] `wireframes/`, `docs/agents/`, `CONTEXT.md`, `CLAUDE.md` all still present

---

## End State — File Tree

```
elizabethhau.github.io/
  .github/workflows/deploy.yml
  .gitignore
  CLAUDE.md
  CONTEXT.md
  PLAN.md
  docs/agents/
  public/
    favicon.png
    favicon.ico
    Hau_Elizabeth_Resume.pdf
  src/
    components/
      Nav.astro
      Hero.astro
      About.astro
      Skills.astro
      Experience.astro
      Projects.astro
      Contact.astro
      Footer.astro
    layouts/
      BaseLayout.astro
    pages/
      index.astro
    styles/
      global.css
  wireframes/
  astro.config.mjs
  package.json
  tsconfig.json
```
