# elizabethhau.github.io

Personal portfolio site for [Elizabeth Hau](https://elizabethhau.github.io) — software engineer, cloud architect, AI engineer.

Built with [Astro](https://astro.build) and deployed to GitHub Pages via GitHub Actions.

## Stack

- **Framework:** Astro (static output)
- **Styling:** Vanilla CSS with custom properties, `@fontsource/inter`
- **Hosting:** GitHub Pages
- **Analytics:** Cloudflare Web Analytics (cookieless)
- **Deploy:** GitHub Actions on push to `master`

## Development

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # output to dist/
```

## Lighthouse

Performance 99 · Accessibility 100 · Best Practices 96 · SEO 100

## Structure

```
src/
  components/    # Nav, Hero, About, Skills, Experience, Projects, Contact, Footer
  layouts/       # BaseLayout.astro
  pages/         # index.astro, 404.astro
  styles/        # global.css
public/          # favicon, resume PDF
```

## Content

All content decisions are documented in `CONTEXT.md`. Implementation plan lives in `PLAN.md`.
