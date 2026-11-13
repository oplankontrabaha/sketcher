# OKB Dredge Area Sketcher

Page where regional offices submit the cubic meters dredged and draw the cleaned stretches of each waterway on the map, for **Oplan Kontra Baha (OKB)**.

**Live page:** https://oplankontrabaha.github.io/sketcher/

## How it works

| Part | Where it lives | What it does |
|---|---|---|
| `index.html` | this repository (GitHub Pages) | the whole page: sign-in, map, sketching, volume entry, photos |
| `Code.gs` | the Apps Script project (not in this repo) | the server: reads the OKB SSOT, checks region passwords, writes cleaned points, volumes and the change log, sends confirmation emails |

The page talks to the server through the Apps Script `/exec` link, saved as `API_URL` in `index.html`.
Every request is one `POST` with `{ "fn": "...", "args": [...] }`, and Code.gs only answers the ten functions listed in its `API_FUNCTION_NAMES`.

## Updating

- **Page changes:** edit `index.html` here and commit. GitHub Pages updates within a minute or two.
- **Server changes:** paste the new `Code.gs` into Apps Script, then
  **Deploy → Manage deployments → ✏️ Edit → Version: New version → Deploy**.
  Always edit the existing deployment: a new deployment gets a new `/exec` link, and `API_URL` would have to change too.
- **Access:** the deployment must be *Execute as: Me* and *Who has access: Anyone*.
- **Check the server:** open the `/exec` link with `?ping=1` at the end. It should answer with `"ok": true`.
- **Sample data:** add `?preview=1` to the page address to try it without touching the sheets.
