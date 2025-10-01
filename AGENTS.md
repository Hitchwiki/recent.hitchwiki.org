# Repository Guidelines

## Project Structure & Module Organization
- `htdocs/index.html` – single-page app with layout, map logic, and relay handlers; respect existing comment blocks when editing.
- `htdocs/favicon.ico` – browser icon; keep size below 32×32 for consistency.
- `settings.json` – stores the public npub used across views; avoid adding secrets.
- `deploy.sh` – rsyncs `htdocs/index.html` to the production host; update paths if the remote changes.
- `TODO.md` – working backlog; adjust status whenever features ship.

## Build, Test, and Development Commands
- `open htdocs/index.html` – fastest local load in your default browser.
- `python3 -m http.server 8080 --directory htdocs` – static server that satisfies CSP and lets you test WebSocket upgrades.
- `bash deploy.sh` – pushes latest HTML to the live server; dry-run via `rsync -n` if you tweak the script.

## Coding Style & Naming Conventions
- Use four-space indentation in HTML, CSS, and embedded scripts; keep each major section separated by descriptive HTML comments.
- Prefer ES6 syntax: `const`/`let`, arrow callbacks, camelCase helpers, and uppercase constants for relay URLs.
- Keep UI color variables and map configuration near the top so gradient themes and Leaflet options stay easy to discover.
- Run Prettier (HTML mode) before committing when large blocks are reformatted.

## Testing Guidelines
- After changes, serve locally, reload the page, and confirm the map initializes, markers cluster, and the live feed increments.
- Watch browser devtools for console warnings, verify both relay WebSockets connect, and inspect note detail drawers for regressions.
- When editing geo parsing, replay cached events from `localStorage.recentEvents` to avoid hammering live relays.

## Commit & Pull Request Guidelines
- Follow the existing short imperative commit voice (`Add favicon and cluster map markers`).
- Reference related TODO items or GitHub issues in commit bodies for traceability.
- PRs should describe impact, list manual verification steps, and attach screenshots or a brief capture for UI updates.
- Request review from relay maintainers whenever endpoints, authentication, or deployment scripts are touched.

## Deployment & Configuration Tips
- Keep `settings.json` limited to public-facing identifiers and document any relay changes in the PR.
- After running `deploy.sh`, smoke-test https://recent.hitchwiki.org and confirm sister domains resolve the same build before closing work.
