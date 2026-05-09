# myGymPalace

A minimal gym website built with **WordPress** — running entirely in your browser via [WordPress Playground](https://wordpress.org/playground/) (WebAssembly). No PHP, MySQL, or hosting required for the demo.

## What's inside

- **`blueprint.json`** — the Playground recipe. Installs WordPress + the Twenty Twenty‑Four theme, then provisions five pages (Home, Classes, Membership, Trainers, Contact), wires up a primary menu, and sets a static front page.
- **`index.html`** — a tiny launcher that boots the site in an iframe using the Playground JS client.

## Run it locally

You need a static file server (the Playground client is loaded as an ES module, so `file://` won't work — the browser blocks it for security).

Pick any of these:

```bash
cd ~/myGymPalace

python3 -m http.server 8000
npx --yes serve -l 8000
php -S localhost:8000
```

Then open <http://localhost:8000/>. The first load takes ~10 seconds while WordPress + PHP are downloaded as WASM and cached. Subsequent loads are near-instant.

You'll be auto-logged in as `admin` (password `password`) and dropped on the homepage.

## Run it without any local server

You can also paste the blueprint URL directly into the hosted Playground. Either:

1. Host this folder somewhere public (GitHub Pages works), then visit:
   `https://playground.wordpress.net/?blueprint-url=https://YOUR-HOST/blueprint.json`
2. Or copy `blueprint.json`'s contents into the URL fragment of `https://playground.wordpress.net/#{...}`.

## Pages provisioned

| Page         | What it shows                                                     |
|--------------|-------------------------------------------------------------------|
| Home         | Full-width hero, three feature columns, motivational quote band   |
| Classes      | Six classes (HIIT, Yoga, Strength, Spin, Boxing, Functional WOD)  |
| Membership   | Three pricing tiers (Starter / Pro / Elite) with a highlighted plan |
| Trainers     | Three coach profiles with photos and credentials                  |
| Contact      | Address, hours, phone, email, and a CTA                           |

## Customize

- Open the **Open Admin** link in the header → `/wp-admin/` to edit any page in Gutenberg.
- Tweak `blueprint.json` and reload — Playground re-runs the recipe from scratch each time (your edits inside the iframe are ephemeral unless you enable browser storage; see the Playground docs).
- Want to persist edits across reloads? Append `?storage=browser` to the iframe `src`, or pass `storage: 'browser'` when starting the client.

## Why Playground?

It's the fastest way to prototype, demo, or share a WordPress site without provisioning hosting — perfect for a "minimal gym website" you can iterate on, screenshot, or hand off as a single folder.
