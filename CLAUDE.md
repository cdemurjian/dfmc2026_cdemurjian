# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static website for a Dana-Farber Marathon Challenge (DFMC) 2026 Boston Marathon fundraising campaign. Hosted via GitHub Pages at www.charlie-dfmc2026.com (configured via CNAME).

## Architecture

- **No build system** — plain HTML/CSS served directly by GitHub Pages
- `index.html` — Main fundraising page with personal story and donate links
- `drawing.html` — Opportunity drawing page (self-contained styles, not linked to styles.css)
- `styles.css` — Shared stylesheet (currently only used by index.html)
- Images are stored at repo root (PNG, JPG, JFIF)

## Design System

Both pages share the same visual language: **Bebas Neue** (display/headings, via Google Fonts) + **DM Sans** (body), warm cream background (`#f5f4ee`) with a subtle diagonal stripe texture, and a blue/yellow Boston Marathon palette.

CSS custom properties (defined in `:root` of both `styles.css` and `drawing.html`'s inline `<style>`):
- `--yellow: #ffde00` / `--yellow-hi: #ffe94d`
- `--blue: #162f77`
- `--cream: #f5f4ee`
- `--border: #e2e1d8`

`drawing.html` is fully self-contained (inline styles). `index.html` links to `styles.css`.

## Key Patterns

- **Header**: Full-bleed blue with diagonal bottom edge via `clip-path: polygon(0 0, 100% 0, 100% calc(100% - 2.5rem), 0 100%)`. Bebas Neue title with staggered CSS `riseUp` animations (`.h-1` / `.h-2` / `.h-3`).
- **Footer**: Full-bleed blue with mirrored diagonal top edge via `clip-path: polygon(0 2.25rem, 100% 0, 100% 100%, 0 100%)`. Yellow Bebas Neue headline.
- **Buttons** (Donate, Venmo): Yellow with blue border + retro offset `box-shadow: 4px 4px 0 var(--blue)`. Hover lifts (`translate(-2px,-2px)` + larger shadow), active presses.
- **Section labels**: Bebas Neue small-caps with a yellow extending line via `::after` flex trick.
- Scroll-triggered fade-in via IntersectionObserver (`.fade-in` / `.visible`)
- Floating fixed-position donate button (bottom-right, same press-effect style)
- Responsive breakpoint at `min-width: 768px`
- External links open in new tabs (`target="_blank"`)
- Donate links point to Dana-Farber's JimmyFund platform

## Development

Open HTML files directly in a browser — no server or build step required.
