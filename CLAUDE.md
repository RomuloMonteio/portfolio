# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static personal portfolio site for Romulo Monteiro (Frontend Developer, based in Portugal). Written in Portuguese (pt-PT). No build tools, bundlers, or package managers — open `index.html` directly in a browser or serve it with any static server.

## Development

To preview locally:
```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

No build, lint, or test commands — this is a plain HTML/CSS project with no toolchain.

## Architecture

Single-page layout with three sections, all in `index.html`:

- **Navbar** — glassmorphism pill-style nav (`.glass-nav`) using Bootstrap 5.3 collapse for mobile. The "Vamos conversar →" CTA button uses `.btn-glass`.
- **Home** — two-column flex layout (`.home`): text content left, profile photo right. Collapses to single column on mobile.
- **Services** — Bootstrap grid of three cards with `.liquid-card` glass effect (blur + translucent background + inset border highlight).
- **Portfolio** — dark gradient section with pseudo-element blobs (`::before`/`::after`) as decorative background. Cards use the same liquid-glass pattern as Services but are scoped under `.portfolio .card`.

## Styling Conventions

All styles live in `css/style.css`. Key design tokens used throughout:

| Token | Value | Use |
|-------|-------|-----|
| Accent blue | `#38bdf8` / `#0ea5e9` | Headings, buttons, underlines |
| Gradient purple→blue | `#8b5cf6` → `#3b82f6` | CTA buttons (`.btn-glass`, `.liquid-btn`, `.portfolio .btn-primary`) |
| Glass base | `rgba(255,255,255,0.08)` + `backdrop-filter:blur(18px)` | All card and navbar backgrounds |
| Body gradient | `#0f172a → #1e293b → #0f172a` | Dark navy page background |

The mobile breakpoint is `max-width: 768px`. Bootstrap handles the navbar collapse; custom media queries handle the home section stacking.

## External Dependencies (CDN only)

- Bootstrap 5.3 CSS + JS bundle
- Font Awesome 6.5 (icons — currently loaded but not visibly used on page)
