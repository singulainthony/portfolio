# Anthony Carnevale — Portfolio

Live site: **https://anthonycarnevale.ca**

This repository contains the **built static output** of the portfolio site (Astro 6 + Three.js),
served by GitHub Pages from the `main` branch root on the custom domain `anthonycarnevale.ca`.
The old address, https://singulainthony.github.io/portfolio/, redirects there.

## Source of truth

The editable source lives locally at:

```
/Users/anonymouspro/Dev & Such/Portfolio-Site
```

That directory is an Astro project. It is **not** committed here — this repo holds only the
compiled `dist/` output.

## Redeploying after a content change

The site is served from the domain root, so the plain build works as-is. No path rewriting is needed
(the old `/portfolio/` rewrite script is no longer used).

```bash
cd "/Users/anonymouspro/Dev & Such/Portfolio-Site"
npm run build

# from a clone of this repo:
rsync -a --delete --exclude .git --exclude README.md "/Users/anonymouspro/Dev & Such/Portfolio-Site/dist/" ./
touch .nojekyll
git add -A && git commit -m "Update site" && git push
```

`CNAME` comes from the Astro project's `public/CNAME`, so it is included in every build. Don't delete it,
or GitHub Pages will drop the custom domain.

## Pages configuration

- Source: `main` branch, `/` (root)
- Custom domain: `anthonycarnevale.ca`, HTTPS enforced
- DNS (GoDaddy): four `A` records for `@` → 185.199.108.153 / .109.153 / .110.153 / .111.153,
  and `www` CNAME → `singulainthony.github.io`
- Build type: legacy (no Actions workflow — this is pre-built output)
- `.nojekyll` present so Astro's `_astro/` directory is served
