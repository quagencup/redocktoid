# 808Way — self-hosted biolink page

A standalone clone of the guns.lol-style profile page layout: full-bleed
grayscale background photo with a slow ambient zoom, glitching username,
glass profile card with avatar + online status + "last seen" text, a
diamond badge with a hover tooltip, and a row of social icons.

Single `index.html`, no build step, no required external dependencies
(Google Fonts are loaded from a CDN link — remove that `<link>` tag and
set `--font-display`/`--font-body` to a system font if you want fully
offline fonts too).

## Folder layout

```
index.html
assets/
  bg/
    background.jpg      <- your background image (or video)
  audio/
    Ok Teaze.mp3         <- your background track
  icons/                 <- put your own icon images here (optional)
```

## Customize it

Open `index.html` and edit the `CONFIG` object near the top of the
`<script>` section:

- `username`, `handle`, `avatarLetter` / `avatarImage`
- `online` (true/false) and `lastSeenAt` — the "last seen" text updates
  itself live based on this timestamp
- `badge.tooltip` — the text shown when you hover the purple diamond
  (defaults to "Premium Member"); `badge.image` lets you swap the
  diamond for your own icon image
- `background` — already points at `assets/bg/background.jpg`. Add more
  entries (images or videos) to cross-fade between several:

  ```js
  background: [
    { type: "image", src: "assets/bg/background.jpg" },
    { type: "video", src: "assets/bg/clip.mp4" },
  ],
  ```

- `audio.src` — already points at `assets/audio/Ok Teaze.mp3`. Browsers
  block autoplaying audio with sound, which is why there's a
  "click to enter" gate and a mute/unmute button in the corner.
- `links` — each entry has a built-in `icon` (svg fallback: `discord`,
  `kick`, `twitch`, `steam`, `tiktok`, `x`, `instagram`) **and** an
  optional `image` field. Set `image` to a file path, e.g.
  `"assets/icons/discord.png"`, to use your own icon image instead of
  the built-in SVG — when `image` is set it always wins.

## Deploy

Any static host works. Two of the simplest:

**GitHub Pages**
1. Create a new repo, upload `index.html` and the `assets/` folder.
2. Repo Settings → Pages → set source to the `main` branch.
3. Your page is live at `https://yourusername.github.io/reponame/`.

**Netlify / Vercel**
Drag the folder into their web dashboard's deploy area — no config needed.

If you own a domain, point its DNS at whichever host you pick and you're done.
