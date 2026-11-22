# Shadcn/Svelte Landing Page Template

A responsive landing page template built with [SvelteKit](https://svelte.dev/docs/kit), [shadcn-svelte](https://www.shadcn-svelte.com/), TypeScript and [Tailwind CSS v4](https://tailwindcss.com/). It is a port of [shadcn-vue-landing-page](https://github.com/leoMirandaa/shadcn-vue-landing-page) to SvelteKit.

Live demo: <https://shadcn-sveltekit-landing-page.zxce3.net>

<!-- TODO: replace with an up-to-date screenshot -->
![Screenshot of the landing page](./static/demo-image.png)

## Features

- Fully responsive layout with a mobile sidebar
- Dark mode (via `mode-watcher`)
- SEO basics: title, description, Open Graph and Twitter meta tags, canonical link (configured in `src/lib/config/meta.ts`)
- Svelte 5 (runes), Tailwind CSS v4, Vite 8, SvelteKit 3
- Static output through `@sveltejs/adapter-static`

### Sections

Navbar, Hero, Sponsors, Benefits, Features, Services, How It Works, Testimonials, Team, Community, Pricing, Contact, FAQ, Footer.

## Quick start

Requirements: a current Node.js LTS (or Bun).

```bash
git clone https://github.com/zxce3/shadcn-sveltekit-landing-page.git
cd shadcn-sveltekit-landing-page
bun install        # or: npm install
bun run dev        # or: npm run dev
```

Open <http://localhost:5173>.

### Scripts

| Script | Description |
| --- | --- |
| `dev` | Start the dev server |
| `build` | Production build (static site in `build/`) |
| `preview` | Preview the production build |
| `check` | Type-check with `svelte-check` |

## Customizing

- Site name, description, URL and OG image: `src/lib/config/meta.ts`
- Sections: `src/lib/components/`
- Theme colors (CSS variables) and Tailwind theme: `src/app.css`
- UI primitives: `src/lib/components/ui/` (shadcn-svelte)

## Deployment

The project uses `adapter-static`, so `bun run build` produces a static site in `build/` that can be hosted anywhere.

- GitHub Pages: `.github/workflows/deploy.yml` builds and deploys on every push to `main`. If the site is served from a sub-path, set `paths.base` in the `sveltekit(...)` options in `vite.config.ts`.
- Other static hosts (Netlify, Cloudflare Pages, Vercel, etc.): build command `bun run build` (or `npm run build`), output directory `build`.
- For SSR, swap in another [adapter](https://svelte.dev/docs/kit/adapters).

## License

[MIT](./LICENSE)
