# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static single-page portfolio for Candela Merás, an Argentine fashion designer (brand: Meiri Doll). The entire site lives in a single `index.html` file — no build system, no package manager, no backend.

## Running Locally

No build step. Open directly or serve statically:

```bash
python -m http.server 8000
# or
npx http-server
```

## Architecture

Everything is in `index.html`:
- **~650 lines of embedded CSS** in a `<style>` block
- **~65 lines of vanilla JS** in a `<script>` block at the bottom
- No external JS dependencies; Google Fonts loaded via CDN

### Sections (top to bottom)
`nav` → `#inicio` (hero) → `#sobre` (about) → `#proyectos` (3 project blocks) → `#contacto` → `footer`

### CSS System
All colors are CSS variables in `:root`: `--rose`, `--burgundy`, `--cream`, `--ink-rose`, `--muted`, etc. Typography mixes Jost (UI/body), Cormorant Garamond (subtitles), and Great Vibes (script titles). Single mobile breakpoint at `@media (max-width: 860px)`.

### JS Behavior
- **Custom cursor**: Two fixed-position elements (`.cursor` dot + `.cursor-ring`) driven by `mousemove`. Body has `cursor: none`.
- **Image uploads**: `.slot` divs wrap hidden `<input type="file">`. `loadSlot()` calls `URL.createObjectURL()` and injects an `<img>`. `removeSlot()` removes it. No persistence — refresh clears all images.
- **Scroll reveal**: `IntersectionObserver` at threshold 0.12 adds `.visible` to `.project-block` elements.
- **Hero upload**: Separate `heroUpload()` function handles the hero photo slot.

### Project Grids
Photo grids use utility classes (`cols-1`, `cols-2`, `cols-3`, `cols-4`, `cols-2-tall`) that map to CSS Grid layouts. Slots have fixed `aspect-ratio` values (3/4, 4/3, 1, 16/7).

## Contact Info in HTML
- Email: `candela@meiridoll.com`
- Instagram: `@meiridoll`
- WhatsApp number is a placeholder — update it in the HTML before deploying
