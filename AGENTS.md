# Base44 Dev Environment

## Project Overview

Static HTML personal portfolio site for Rayyan Dawood. No build step, no backend, no database.

## Structure

- `index.html` — main entry point (served at `/`)
- `index_Version5.html` — alternate version (accessible at `/index_Version5.html`)
- `logo-rayyan.png` — logo image

## Running

```bash
docker compose -f docker-compose.base44.yml up -d
```

Serves via nginx:alpine on host port 3000. The repo root is bind-mounted read-only into nginx's html directory, so edits to HTML files appear immediately on browser refresh (no reload needed — nginx serves files directly).

## Verification

- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` should return `200`
- The page at `/` renders the portfolio card with red-on-black styling

## Notes

- No secrets required — the app is fully static with no external service dependencies.
- No live-reload dev server; nginx serves files directly. Call `reload_preview` after edits if the browser doesn't refresh on its own.
