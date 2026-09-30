# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static GitHub Pages project page for the paper **SteadyTray: Learning Object Balancing Tasks in Humanoid Tray Transport via Residual Reinforcement Learning** (UCSD ARClab; arXiv 2603.10306; IROS 2026, finalist for the IROS Best Application (ICROS) and Mobile Manipulation (OMRON Sinic X) Paper Awards). The method is called **ReST-RL**; **SteadyTray** is the task/benchmark name. Both are styled as `<strong style="color: #1a1a1a;">` in body text.

The site is adapted from the Nerfies / UMI-On-Legs template. There is no build step, package manager, linter, or tests. Everything under `main` is served as-is by GitHub Pages.

## Previewing

Open `index.html` directly, or serve the repo root so relative paths and videos behave like production:

```sh
python3 -m http.server 8000   # then visit http://localhost:8000
```

Headless Chrome screenshots need a time budget or they hang on the YouTube iframe and autoplaying videos:

```sh
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars \
  --virtual-time-budget=5000 --window-size=1280,900 --screenshot=out.png "file://$PWD/index.html"
```

## Structure

- `index.html` holds the whole page. Sections in order: hero (title with logo, authors, affiliation/venue logo row, award badge, link buttons), YouTube teaser, abstract and method figures, real-world video grids, simulation videos, BibTeX, footer.
- `static/css/index.css` holds the site styles on top of `bulma.min.css`. Much of the page still uses inline `style=""` attributes; the award badge (`.award-badge*`) and the logo row (`.affiliation-logos`) are the only class-based components added beyond the template.
- `static/js/index.js` is template leftover. It initializes bulma-carousel/slider and preloads interpolation frames from `./static/interpolation/stacked`, which does not exist in this repo. The page doesn't use a carousel or interpolation slider, so 404s for those frames are expected and harmless.
- Assets: `static/images/` (logos and method figures), `static/videos/*.mp4` (large and committed directly), `static/docs/SteadyTray.pdf` (the Paper button links to it).

## Conventions

- Icons come from the Font Awesome 6.4 **CDN** stylesheet and Academicons (for `ai-arxiv`) loaded in `<head>`. The local `static/js/fontawesome.all.min.js` is not loaded.
- Brand colors: `#1E72B8` (SteadyTray blue in the title). The award badge uses a gold palette that matches IROS 2026 and UCSD gold.
- New videos follow the existing pattern `<video autoplay muted loop playsinline controls style="width: 100%;">` inside Bulma `columns`/`column`.
- Keep the BibTeX block in sync with the paper metadata when venue or citation details change.
