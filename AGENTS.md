# Repository Guidelines

## Project Structure & Module Organization
- Root static site: `index.html` is the entry point with inline JS and minimal CSS.
- No build step or bundler; files are served as-is.
- External assets are loaded from CDNs. If you add local assets, place them under `assets/` and reference with relative paths.

## Build, Test, and Development Commands
- `pnpm dev` (or `npm run dev`): serves the site via `http-server` at `http://localhost:3000/` and opens the browser.
- Alternative: `npx http-server . -o -p 3000 -a localhost` if you prefer not to use pnpm.
- Production: deploy on any static host (e.g., GitHub Pages, Netlify); no special build required.

## Coding Style & Naming Conventions
- Indentation: 2 spaces for HTML, CSS, and JS.
- JS: prefer `const`/`let`, semicolons required, functions/variables in `camelCase`.
- HTML: element `id`/`class` in `kebab-case` (e.g., `capture-btn`), filenames in `kebab-case`.
- Lint/format: none configured; if adding, use Prettier defaults and ESLint (browser env) to match the current style.

## Testing Guidelines
- No automated tests yet. Perform manual checks:
  - Marker tracking works with the `hiro` preset.
  - GLTF model loads; fallback box appears if it fails.
  - Screenshot button saves an image.
- Cross-check on Chrome and Safari; verify camera permissions and console warnings.
- Optional future tests: Playwright smoke test to load the page and assert AR UI elements.

## Commit & Pull Request Guidelines
- Commits: imperative, present tense, short scope.
  - Example: `feat: add screenshot capture button`, `fix: hide box when model loads`.
- PRs: include a clear description, repro steps, screenshots/video if UI changes, and any related issue links.
- Verify locally (`pnpm dev`) and note tested browsers/devices in the PR.

## Security & Configuration Tips
- Camera access requires a secure origin; `localhost` is fine for dev, use HTTPS in production.
- Use HTTPS for all external assets to avoid mixed content and CORS issues.
- Keep dependencies minimal; the current setup uses CDNs and no build tooling.
