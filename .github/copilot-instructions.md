Project snapshot
----------------
- Static portfolio website (single-page). Entry: `index.html`.
- Styling: prebuilt `css/style.css` is present; source SCSS in `scss/style.scss` and `scss/bootstrap/*` (Prepros config included).
- JS: jQuery + plugins; custom initialization lives in `js/main.js`.
- Assets: images in `images/`, fonts in `fonts/`, third-party libs in `lib/` and top-level `js/` and `css/`.

What an AI coding agent should know
----------------------------------
- This is not a Node project — there is no `package.json`. It's a client-side static template derived from Colorlib.
- SCSS is the source of truth for styles. The repository includes a `prepros-6.config` which indicates the project was compiled with Prepros to produce `css/style.css`.
- JavaScript relies on jQuery (v3.x), Owl Carousel, Magnific Popup, AOS, and other plugins. `js/main.js` contains the glue/initialization (carousel, scroll effects, counters, popups).
- Content is inline in `index.html`. Sections are anchor-linked (#home-section, #about-section, #project-section, #contact-section).

Common edit/preview workflows (discoverable)
-------------------------------------------
- Quick preview: open `index.html` in a browser (double-click or use an HTTP server). For live reload use a VS Code Live Server extension or `python -m http.server` from the repo root.
- Rebuild CSS from SCSS: the repo expects a SASS/Prepros workflow. Two options:
  - Use Prepros: open `prepros-6.config` in Prepros to reproduce the original compile setup.
  - Use the Dart Sass CLI: from project root run `sass scss/style.scss:css/style.css --no-source-map --style=expanded` (install `sass` first). On Windows PowerShell join commands with `;` if needed.
- No JS build steps required; edit `js/main.js` directly. Changes take effect on page reload.

Project-specific conventions and patterns
----------------------------------------
- Single-page layout: index sections are marked with IDs used by the nav and `js/main.js` for smooth scrolling. Example: the nav links target `#about-section` and `onePageClick()` in `js/main.js` animates scrollTop with a -70 offset.
- CSS source: `scss/style.scss` imports Bootstrap pieces under `scss/bootstrap/`. If you change variables, recompile `scss/style.scss` to update `css/style.css`.
- Animation & counters: counters use `data-number` attributes (see `.number` in `index.html`) and are animated via `jquery.animateNumber` and Waypoints in `js/main.js`.
- Carousel: `.home-slider` is initialized with Owl Carousel in `js/main.js` — change behavior there (autoplay, transition) rather than editing plugin files.
- Image popups: links with `.image-popup` are wired to Magnific Popup; YouTube/Vimeo iframes use `.popup-youtube` classes.

Integration and external dependencies
-------------------------------------
- External fonts loaded from Google Fonts in `index.html` (Poppins).
- No CI, hosting, or backend in repo. Typical deploy is static hosting (GitHub Pages, Netlify, Vercel, S3).
- If adding package-managed tooling (npm, node-sass, gulp), add `package.json` and document the new workflow. Currently none exists.

Examples the agent can act on
-----------------------------
- Update hero text: edit `<h1>` and the `#typing-animation` array in `index.html` (script near the top). For typing changes, prefer small edits to the array `typingTexts`.
- Add a project card: copy one `.blog-entry` block under `#project-section` in `index.html`, update `background-image` URL and text.
- Change primary color: edit `$primary` in `scss/style.scss` and recompile to `css/style.css`.
- Tweak navbar scroll behavior: modify thresholds (150, 350) in `js/main.js` -> `scrollWindow()`.

When to ask for human help
--------------------------
- Any change requiring a build pipeline (add npm/gulp, CI) or credentials for external services.
- If you can't reproduce SCSS output differences locally (install `sass` or use Prepros).
- When major layout or accessibility changes are proposed — ask for design intent.

Files to inspect first
----------------------
- `index.html` — content, sections, inline scripts
- `js/main.js` — event wiring, plugin initialization, scroll/counter logic
- `scss/style.scss` and `prepros-6.config` — source styles and compile mapping
- `css/style.css` — compiled output used in production

If anything in this file is unclear, tell me what you plan to edit and I will update these instructions with concrete examples.
