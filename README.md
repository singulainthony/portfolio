# Anthony Carnevale — Portfolio

Live site: **https://anthonycarnevale.ca**

This repository contains the **built static output** of the portfolio site (Astro + Three.js),
served by GitHub Pages at the apex domain with a custom `CNAME`.

## Source of truth

The editable source lives locally at:

```
/Users/anonymouspro/Dev & Such/Portfolio-Site
```

That directory is an Astro project and is **not** committed here. This repo holds only the
compiled `dist/` output.

## Deploying: no path rewriting needed

The site is served from the **domain root** (`https://anthonycarnevale.ca/`), so the absolute
URLs Astro emits (`/_astro/...`, `/hire`, `/favicon.svg`) resolve correctly as-is.

```bash
cd "/Users/anonymouspro/Dev & Such/Portfolio-Site"
npm run build
# copy dist/ contents to this repo, commit, push
```

**Do not prefix URLs with a subpath.** An earlier version of this site was served from
`/portfolio/` and needed a rewrite step. That is no longer the case, and applying a prefix
now would 404 every link and image.

## Pages configuration

- Source: `main` branch, `/` (root)
- Custom domain: `anthonycarnevale.ca` (via `CNAME`)
- `.nojekyll` present so Astro's `_astro/` directory is served
- `www.anthonycarnevale.ca` resolves through GitHub Pages

## Contact details used on application materials

- Email: `ac@anthonycarnevale.ca`
- Portfolio: `anthonycarnevale.ca`
