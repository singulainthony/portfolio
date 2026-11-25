# Anthony Carnevale — Portfolio

Live site: **https://singulainthony.github.io/portfolio/**

This repository contains the **built static output** of the portfolio site (Astro 6 + Three.js),
served by GitHub Pages from the `main` branch root.

## Source of truth

The editable source lives locally at:

```
/Users/anonymouspro/Dev & Such/Portfolio-Site
```

That directory is an Astro project. It is **not** committed here — this repo holds only the
compiled `dist/` output.

## Why paths are rewritten

GitHub Pages serves this repo from a subpath (`/portfolio/`), but the Astro build emits
root-absolute URLs (`/hi`, `/_astro/...`). Those would 404 at the subpath. So the build is
post-processed to prefix every root-absolute `href`, `src`, `srcset`, `poster`, `content`
and CSS `url(/...)` reference with `/portfolio`.

The rewrite script lives at:

```
~/.hermes/profiles/apple-job/scripts/deploy-portfolio.py
```

## Redeploying after a content change

```bash
cd "/Users/anonymouspro/Dev & Such/Portfolio-Site"
npm run build

python3 ~/.hermes/profiles/apple-job/scripts/deploy-portfolio.py \
  "/Users/anonymouspro/Dev & Such/Portfolio-Site/dist" \
  ~/.hermes/profiles/apple-job/cache/scratch/pf-out2 \
  /portfolio/ \
  https://singulainthony.github.io/portfolio

cd ~/.hermes/profiles/apple-job/cache/scratch/pf-out2
touch .nojekyll
git add -A && git commit -m "Update site" && git push
```

**Do not skip the rewrite step.** A plain `npm run build` + push will break every link and
image on the live site, because the emitted URLs assume the domain root.

## Pages configuration

- Source: `main` branch, `/` (root)
- Build type: legacy (no Actions workflow — this is pre-built output)
- `.nojekyll` present so Astro's `_astro/` directory is served
