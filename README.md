# Iyengar Course Companion — deployable site

Static site. No build step, no server code. Drop these files at any web root.

| File | What it is |
|---|---|
| `index.html` | Page shell, storage shim, service-worker registration |
| `app.bundle.js` | The whole app plus React, ~2.0 MB (about 700 KB over the wire, gzipped) |
| `manifest.webmanifest` | Makes it installable as a home-screen app |
| `sw.js` | Caches everything on first visit so it runs without a signal |
| `icon-*.png`, `favicon-32.png` | App icons |

## Deploying to GitHub Pages

1. Create a repository, e.g. `iyengar-companion`.
2. Upload the contents of this folder to the repository root.
3. Settings → Pages → Source: **Deploy from a branch**, Branch: **main**, Folder: **/ (root)**. Save.
4. Wait 1–2 minutes. The URL appears at the top of the Pages settings screen:
   `https://<your-username>.github.io/iyengar-companion/`

## Adding it to your home screen

**iPhone / iPad** — open the URL in **Safari** (not Chrome; only Safari can install web apps).
Tap Share → Add to Home Screen → Add.

**Android** — open in Chrome, tap the ⋮ menu → Install app / Add to Home screen.

It then opens full-screen with no browser chrome, and works offline after the first load.

## Updating

Replace `app.bundle.js` and bump `CACHE` in `sw.js` (e.g. `iyengar-v2`), otherwise devices
keep serving the cached old version. Then push.

## Data

Sessions, quiz history, corrections and voice preferences are stored in `localStorage` on the
device. They are not synced and are lost if you clear site data.
