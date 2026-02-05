# Repository Guidelines
Concise guidance for contributing to this static site promoting the 2026 Dana-Farber Marathon Challenge entry. Optimize for clarity, small diffs, and reproducible local previews.

## Project Structure & Module Organization
- `index.html`: Single-page layout, inline script for fade-in effects. Keep new sections semantically grouped with headings and `<section>` tags.
- `styles.css`: Theme variables, layout, and responsive rules. Reuse existing CSS custom properties (`--yellow`, `--blue`, etc.) and prefer extending utility classes like `.fade-in`.
- Assets: Image files live at the repo root; replace in-place to avoid path churn. `CNAME` configures the hosted domain—leave untouched unless changing deployment.

## Build, Test, and Development Commands
- Local preview (no build step): `python -m http.server 8000` then open `http://localhost:8000`.
- Link check (manual): After edits, click `DONATE` and story links in the browser to confirm targets open in new tabs.
- Cache busting: When swapping images, keep filenames or update `<img>` `src` references in `index.html`.

## Coding Style & Naming Conventions
- HTML: Two-space indentation, concise copy, centered text defaults. Use semantic headings (`h2`, `h3`) to match existing hierarchy.
- CSS: Kebab-case class names (`.floating-donate`, `.fade-in`); keep theme colors in `:root` and prefer adjusting variables over hard-coding new values. Preserve responsive adjustments in the media query block.
- JS: Keep inline script minimal; if adding behaviors, stick to vanilla JavaScript and guard against missing elements before manipulating the DOM.

## Testing Guidelines
- Visual QA on desktop and mobile widths; verify outline/box-shadow and floating donate button stay in-bounds.
- Accessibility: Ensure link text stays descriptive, images carry meaningful `alt`, and colors retain contrast against backgrounds.
- Animation sanity: Scroll the page to confirm `.fade-in` elements become visible; avoid adding heavy animations that block interaction.

## Commit & Pull Request Guidelines
- Commits: Follow the existing short, imperative style (`Update styles.css`, `Adjust intro paragraph`). Group related visual and copy changes together.
- PRs: Include a one-line summary, before/after screenshots for layout or color changes, and note any external link updates. Link issues when applicable and describe manual checks performed (desktop/mobile, links clicked).
