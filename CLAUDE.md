# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static single-page portfolio for Candela Merás, an Argentine fashion designer (brand: Meiri Doll). No build system, no package manager, no backend. Hosted on Vercel (`https://candelameras.vercel.app/`, static, no build; `vercel.json` redirects `/admin` → `/admin/` so Sveltia finds `config.yml`). Keep asset URLs relative. The owner edits content from her phone via Sveltia CMS at `/admin/`.

## Running Locally

Must be served over HTTP (content is loaded with `fetch`; `file://` won't work):

```bash
python -m http.server 8000
# or
npx http-server
```

## Architecture

- `index.html` — all CSS (in `<style>`) and JS (in `<script>`). The `<body>` is a shell; JS fetches the JSON content and renders it.
- `content/general.json` — hero (`portada`, incl. carousel `fotos`), `sobre_mi`, `proyectos_intro`, `contacto`. Elements with `data-bind="a.b"` get `textContent` from that path.
- `content/proyectos.json` — `{ proyectos: [{ titulo, etiqueta, descripcion, visible, destacado, secciones: [{ titulo, columnas: "1".."4", formato: vertical|horizontal|cuadrado|panoramico, fotos: [path] }] }] }`. Projects with `visible: false` and sections with no photos are not rendered.
- `admin/index.html` + `admin/config.yml` — Sveltia CMS. **Any change to the JSON shape must be mirrored in `config.yml`** (and vice versa). Auth goes through a sveltia-cms-auth Cloudflare Worker (`backend.base_url`).
- `images/` — WebP only (CMS converts uploads to WebP ≤2048px). CMS uploads land in `images/subidas/`. Paths in JSON start with `/images/...`; the renderer strips the leading slash so they resolve relative to the page.
- SEO/Open Graph tags are static in `<head>` (crawlers don't run JS); `images/og-image.jpg` is the 1200×630 share image.

### Sections
`nav` → `#hero` (carousel) → `#sobre-mi` → `#proyectos` (`#projectList`, rendered) → `#contacto` → `footer` → lightbox.

### CSS System
Colors are CSS variables in `:root` (`--rose`, `--burgundy`, `--cream`, `--ink-rose`, `--muted`, …). Fonts: Jost (UI/body), Cormorant Garamond (subtitles), Pinyon Script (script titles). Breakpoints: 860px and 480px; `prefers-reduced-motion` disables animations. Grid classes `cols-1..4`; photo shape classes on `.photo`: `vertical` (3/4, default), `horizontal`, `cuadrado`, `panoramico`.

### JS Behavior
- Always escape CMS content with `esc()` before inserting HTML. `sobre_mi.texto` supports blank-line paragraphs and `*text*` → script-font emphasis.
- Custom cursor only on `(hover: hover) and (pointer: fine)` without reduced motion (adds `body.custom-cursor`).
- Scroll reveal: `IntersectionObserver` (threshold 0) adds `.visible` to `.project-block`.
- Lightbox: click a `.photo` → navigates within that grid (arrows, keyboard ←/→/Esc, swipe).

## Contact Info
Lives in `content/general.json` (`contacto`): email `candela@meiridoll.com`, Instagram `meiridoll`, WhatsApp `5493415706842`.
