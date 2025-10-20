# Aniket_Portfolio

Static single-page portfolio built from a Colorlib template.

## Project structure (important files)

- `index.html` — single-page site markup and inline scripts (hero typing, section anchors).
- `scss/style.scss` — primary SCSS source (imports Bootstrap partials in `scss/bootstrap/`).
- `css/style.css` — compiled CSS used in the site (do not edit directly unless intentional).
- `js/main.js` — site-specific JavaScript (carousel, scroll behaviour, counters, popups).
- `lib/`, `js/`, `css/` — third-party plugins and vendor assets.
- `images/`, `fonts/` — static assets.
- `.github/copilot-instructions.md` — guidance for AI contributors.

## Quick preview

Open `index.html` in a browser (double-click) or run a local HTTP server from the repo root:

```powershell
python -m http.server 8000
# then open http://localhost:8000 in your browser
```

## Rebuild CSS (SCSS → CSS)

This project expects SCSS as the source of truth. Two recommended ways to build the CSS:

- Prepros: open `prepros-6.config` in Prepros (GUI) to reproduce the original compile mapping.
- Dart Sass CLI (PowerShell):

```powershell
sass scss/style.scss:css/style.css --no-source-map --style=expanded
```

Install Dart Sass from https://sass-lang.com/install if not available.

## Common edits (where to change things)

- Hero/typing text: edit the hero `<h1>` and the `typingTexts`/typed-array in `index.html`.
- Add a project: copy a `.blog-entry` block inside the `#project-section` in `index.html` and update the `background-image` and links.
- Change colours: update variables in `scss/style.scss` (e.g. `$primary`) and recompile.
- JS tweaks: edit `js/main.js` (carousel options, scroll thresholds like `150`, `350`, offset `-70`).

## Contact / Ask a question

The projects section includes an "Ask a question" CTA that links to the contact section. Edit `index.html` if you want per-project email links or different contact behavior.

## Notes & gotchas

- There are multiple copies of jQuery/plugins in the repo (top-level `js/` and `lib/`). Prefer the top-level `js/` files to avoid duplicates.
- `css/style.css` is generated; prefer editing `scss/style.scss` so changes are maintainable.
- No build system (npm/webpack) is configured. If you add one, add a `package.json` and document the workflow.

## License

This repository is a personal portfolio. Replace this section with your chosen license if you make this public.
