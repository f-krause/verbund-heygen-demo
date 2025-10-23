# Repository Guidelines

## Project Structure & Module Organization
- Root contains a static single‑page demo:
  - `index.html` — UI, styles, and HeyGen embed logic.
  - `logo.webp` — brand asset.
  - `robots.txt`, `README.md` — metadata and notes.
- No build system or frameworks. All code is vanilla HTML/CSS/JS. Keep changes minimal and self‑contained.

## Build, Test, and Development Commands
- Local server (Python): `python3 -m http.server 8080` then open `http://localhost:8080`.
- Local server (Node): `npx serve -l 8080 .` or use an editor “Live Server” extension.
- There is no build step. Deploy by serving these static files from any host.

## Coding Style & Naming Conventions
- Indentation: 2 spaces; line length: keep readable (<120 chars when possible).
- CSS classes: kebab-case (e.g., `avatar-overlay`, `avatar-fab`).
- JS variables/functions: camelCase; avoid global leaks; prefer small helpers.
- Scope styles to the widget (prefix `avatar-`) and prefer responsive units (`dvh`, `env(safe-area-inset-*)`).
- Avoid introducing tooling or dependencies unless discussed (no bundlers, no frameworks).

## Testing Guidelines
- Manual testing across: Desktop Chrome/Edge, iOS Safari, Android Chrome.
- Verify:
  - FAB opens overlay; Minimize docks; Esc and backdrop click close.
  - Microphone permission prompts appear only after user gesture.
  - Loader hides after HeyGen `init` postMessage.
  - Safe-area padding on notched devices; landscape handling; 320px width.
- Use DevTools Console for errors; fix regressions before submitting.

## Commit & Pull Request Guidelines
- Commits: short, imperative, and scoped (e.g., "improve mobile safe-area handling").
- PRs should include:
  - Summary of changes and rationale.
  - Before/after screenshots or a short clip (desktop + mobile).
  - Any known tradeoffs and manual test results.

## Security & Configuration Tips
- Do not commit secrets or API keys. The HeyGen share link in `index.html` is public; rotate if needed.
- If you add CSP headers on hosting, allow `https://labs.heygen.com` for `frame-src` and mic permissions.

## Agent-Specific Instructions
- Keep patches focused; don’t reformat unrelated sections.
- Mirror existing patterns; prefer small utilities over new libraries.
- Update `README.md` when user-facing behavior changes.
- Keep the page static, it should be able to be hosted on GitHub Pages
