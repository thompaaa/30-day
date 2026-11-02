# CLAUDE.md

## Project Overview

**Fotbollsträning – planerare** is a Swedish-language, single-file web app for planning football practice sessions for a youth team (7–8 years). Everything lives in `index.html`: no build system, no dependencies, no server. Served via GitHub Pages.

## Architecture

- `categories{}` — category key → name + color.
- `exercises[]` — static exercise bank edited by hand (id, category, name, minutes, desc, tip, gear). `id` must stay stable; saved sessions reference it. Unknown ids are skipped when rendering.
- `plans` — object keyed by weekday (`mon`…`sun`): `{ items: [{id, min}], done, note }`, persisted to `localStorage` under `fotboll_veckopass`.
- `render()` rebuilds `#main` on every state change. Two tabs: "Veckans pass" (weekday grid + session panel) and "Övningar" (bank with category filter, search, and add buttons). `pickerDay` marks which day the bank adds to.

## Conventions

- Swedish UI text, metric units.
- Inline CSS and JS only, no CDN dependencies.
- `localStorage` is the only persistence (per device).
- Bump `CACHE` in `sw.js` when cached assets change significantly.
