# DimensionCalc

A modern, offline-capable calculator with unit conversion and an interactive
3D formula grapher — built with plain HTML, CSS, and JavaScript (no build
step, no external dependencies).

## Features
- **Standard calculator** — free forever: +, −, ×, ÷, %, backspace, clear.
- **Scientific mode** — premium: sin/cos/tan, √, x², log, ln, π, n!, 1/x.
- **Unit converter** — free: length, weight, temperature, area, speed, data.
- **3D Graph** — plot any `z = f(x, y)` formula, drag to rotate, scroll to
  zoom. Ships with a free Cyan theme; Magma / Aurora / Gold are premium.
- **Premium modal** — UI-only demo unlock (no payment processing) that
  toggles the locked features via `localStorage`.
- **Fully offline** — a service worker (`sw.js`) caches every asset on
  first load, so DimensionCalc keeps working with no network connection,
  just like installed software.
- **Realistic 3D button feel** — layered box-shadows + a translateY
  "depress" animation on every key press.

## Run locally
Any static file server works, e.g.:

```bash
npx serve .
# or
python3 -m http.server 8080
```

Then open the printed local URL. The first load registers the service
worker and caches the app; after that, you can go offline and it still
works.

## Deploy to Vercel
```bash
npm i -g vercel
vercel
```

No build step is required — this is a static site. `vercel.json` is
already included with sensible cache headers for the service worker.

## Install as an app
Because of `manifest.json` + `sw.js`, most browsers let you "Install" or
"Add to Home Screen" for DimensionCalc, so it opens like a standalone
offline app rather than a browser tab.

## File overview
- `index.html` — structure & panels (Standard, Scientific, Convert, 3D Graph)
- `style.css` — design system (crystal/geometric theme), 3D key styling
- `app.js` — calculator engine, converter, formula parser, custom 3D
  canvas renderer (no Three.js — fully self-contained for offline use),
  premium modal logic, service worker registration
- `manifest.json` / `sw.js` — offline/installable PWA support
- `icon.svg` — the Geometric-style faceted "D" logo
