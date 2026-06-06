# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Styrka på mattan – 30 dagar** is a Swedish-language, single-file web app for a 30-day bodyweight strength training program. It lives entirely in `index.html` with no build system, no dependencies, and no server — open the file in a browser or serve via GitHub Pages.

## Architecture

Everything is in one file: `index.html` contains inline CSS, inline JavaScript, and the full 30-day workout program as a JS data array. There is no bundler, no npm, no framework.

**Data flow:**
- `program[]` — static array of 30 day objects (focus, exercises, sets, tips)
- `completed` — plain object persisted to `localStorage` under the key `traning30_completed`
- `openDay` — in-memory state for the currently expanded day panel
- `render()` + `updateProgress()` — full re-render on every state change (no virtual DOM)

**Layout structure:**
- Dark header with name, subtitle, and progress bar
- `#main` div rebuilt on every `render()` call — 4 week sections, each with a 7-column day grid
- Clicking a day button toggles `openDay` and re-renders a `detail-panel` below the grid
- Completion banner shown when all 30 days are marked done

**Color system:** `weekAccents[]` — one hex color per week, applied to labels, borders, backgrounds, and the progress bar gradient.

## Development

No build step. Edit `index.html` and open it in a browser. GitHub Pages serves from the `main` branch root.

To preview locally:
```
python3 -m http.server 8000
# then open http://localhost:8000
```

## Conventions

- Language: Swedish throughout (UI text, exercise names, tips)
- Units: metric (kg, cm) if added in the future
- All styling is embedded in `<style>` — no external CSS
- All logic is embedded in `<script>` — no external JS
- `localStorage` is the only persistence layer
- Keep the app installable as a standalone HTML file (no CDN dependencies)
