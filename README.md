# OldPlay — Classic Games Website

Play legendary classic games in the browser. Dark neon-arcade design,
14 games, global search + genre filters (All / Zombies / Adventure /
Shooter / Sports / Mobile), featured GTA V card, gameplay video.

## Files

- `index.html` — the whole site (self-contained: HTML + CSS + JS in one file)
- `assets/` — 16 game covers/icons + `gta-v-browser-demo.mp4`
  (the gameplay clip: compressed, loads only when the visitor presses play)

## How to host (GitHub Pages)

1. Create a repo named e.g. `oldplay`, upload ALL files keeping the
   folder structure (`assets/...` next to `index.html`).
2. Settings → Pages → Deploy from branch → `main` → `/ (root)`.
3. Open `https://YOUR-USERNAME.github.io/oldplay/`
4. Later: point your `oldplay.space` domain to it (Settings → Pages →
   Custom domain) — same as you did before.

## How to add / edit a game

Open `index.html`, find the `games=[...]` list near the top of the
`<script>` section. Copy a game block and change:

- `title`, `genre`, `categories` (which filter tabs show it)
- `site` (short line under the title), `url` (where PLAY sends the visitor)
- `image` (put the file in `assets/` and reference `assets/your-file.jpg`)

Search finds every game automatically — no extra step needed.

## The GTA V "Verifying..." flow

Clicking the featured GTA V card shows an animated "Verifying..."
(typing dots), then a "Bot verification" screen. The three
content-locker scripts are wired through one function, `loadLocker(src)`:

- GTA V bot verification → `https://apptrck.net/cl/js/7jwoqk`
- Mobile GTA V button → `https://trckapp.org/cl/js/34j1lm`
- Choo Choo Charles button → `https://apptrck.net/cl/js/82v6qj`

Each game entry carries its script in the `locker:` field — change the
URL there to swap scripts, or remove the field to link straight through.

## Where to paste Adsterra ads

Search `index.html` for `adbox` — there are 3 placeholder slots:

1. `Advertisement · leaderboard slot` — below the header
2. `Advertisement · in-feed slot` — between the game grid and the how-to section
3. `Advertisement · footer banner slot` — above the footer

Paste your Adsterra code inside the `<div class="adbox">…</div>`.
(Adsterra → your site → get code → paste. Slots stay invisible until
you add code, so the design stays clean.)

## The gameplay video

`assets/gta-v-browser-demo.mp4` (~0.45MB, with sound) is embedded with
`preload="none"` — it costs zero bandwidth until a visitor presses play.
To swap it, replace the file and keep the same name, or edit the
`<video>` tag's `src`.
