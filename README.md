<h1 align="center">Terminal Decryption: A Birthday Wish, Disguised as a Breach</h1>

<p align="center">
  <i>"No server, no signup, no tracking. Just a payload that only one person can open."</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/HTML5-Structure-E34F26?logo=html5&logoColor=white" alt="HTML5 Badge">
  <img src="https://img.shields.io/badge/CSS3-Styling-1572B6?logo=css3&logoColor=white" alt="CSS3 Badge">
  <img src="https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?logo=javascript&logoColor=black" alt="JavaScript Badge">
  <img src="https://img.shields.io/badge/Payload-Base64_Embedded-4CAF50" alt="Payload Badge">
  <img src="https://img.shields.io/badge/Backend-None-lightgrey" alt="No Backend Badge">
  <img src="https://img.shields.io/badge/Works-Offline-9C27B0" alt="Offline Badge">
</p>

---

## Overview

**Terminal Decryption** is a single-file birthday site built to feel like cracking into a secure system, not opening a greeting card.

The page boots like a terminal, locks itself behind a passcode only the recipient would know, then glitches open into a warm, personal reveal — a photo and a letter, decrypted in real time. There's no backend, no form submission, no analytics. The whole experience — boot sequence, auth gate, and payload — lives in one HTML file with everything embedded, so it runs the moment it's opened.

*A birthday message, not a template. One recipient, one passcode, one payload.*

---

## Features

- **Boot sequence** — a self-typing terminal log (`[OK]`, `[WARN]`, `[LOCK]`) that sets the scene before anything is revealed.
- **Passcode gate** — a real auth screen with a live denial log. Wrong attempts trigger a shake and an "ACCESS DENIED" message; two wrong attempts surface a hint, never the answer.
- **Glitch transition** — a clip-path + hue-rotate wipe that "shatters" the terminal on correct entry, handing off to the reveal phase.
- **Mood shift on unlock** — the palette itself changes on decrypt, from cold terminal green to a warm tone, so the reveal *feels* different from the breach.
- **Scan-line photo reveal** — the recipient's photo is embedded directly in the page (base64, no external image requests) and unveiled under an animated decrypt sweep.
- **Personal letter** — a custom-written message rendered in a display serif, staged in choreographed fade-ins after unlock.
- **Ambient embers** — a light, continuous particle drift during the reveal phase for atmosphere, without turning into a confetti cannon.
- **Fully offline & private** — no accounts, no network calls except the one Google Fonts request. Everything else — including the photo — ships inside the file itself.

---

## Tech Stack

| Technology | Purpose |
|-----------------------------|------------------------------------------------|
| HTML5 | Single-page structure, no build step |
| CSS3 | All styling, animation, and phase transitions — self-contained, no frameworks |
| Vanilla JavaScript | Boot typewriter, passcode logic, glitch transition, reveal choreography, embers |
| Base64-embedded image | The recipient's photo, inlined directly into the HTML — no image hosting needed |
| Google Fonts (CDN) | JetBrains Mono, Fraunces, Work Sans — the only external request the page makes |

---

## Core Functionality

### Phase 1 — Boot
- A list of boot lines is typed out character-by-character with `setTimeout`, tagged `ok` / `warn` / `dim` / `lock` for color.
- On completion, the page auto-advances to the auth phase and focuses the passcode input.

### Phase 2 — Auth
- The typed passcode is normalized and compared against `CONFIG.PASSCODE`.
- Wrong attempts increment a counter, trigger a CSS shake, and log a denial message; the second wrong attempt appends `CONFIG.HINT`.
- A correct match disables the form and fires the glitch transition.

### Transition — Glitch wipe
- A fixed full-screen overlay animates through clipped, jittered slices with a brief hue-rotate, standing in for the "shatter" moment between terminal and reveal.

### Phase 3 — Reveal
- `document.body` gains a `warm-mode` class, swapping the background/accent palette via CSS custom properties.
- The photo, title, caption, letter, and footer each fade up on staggered delays for a choreographed rather than instant reveal.
- Embers spawn on an interval for the remainder of the session.

---

## Getting Started

### Option 1 — Just open it (fully offline)
1. **Download** `index.html` from this repo.
2. **Double-click it** — it opens in your default browser and works immediately. Everything (including the photo) is embedded in the file; only the fonts need an internet connection.

### Option 2 — Clone the repo
```bash
git clone https://github.com/D-Majumder/Birthday_Wish.git
cd Birthday_Wish
open index.html   # or just double-click it in your file explorer
```

### Option 3 — Host it for a stable link
This is a static file, so any static host works: GitHub Pages, Netlify, Cloudflare Pages, or a folder on your own server.
```bash
# Example: GitHub Pages
# 1. Push this repo to GitHub
# 2. Settings → Pages → Deploy from branch → main / root
# 3. Send the link — the passcode gate does the rest
```
> Note: this is a one-recipient page by design. Don't post the link publicly if the passcode is meant to stay private — treat the URL the way you'd treat the passcode itself.

---

## Customization Tips

- **Change the recipient**: update the `<title>`, the `reveal-title` heading, and the photo `alt` text.
- **Change the passcode & hint**: both live in the `CONFIG` object at the top of the `<script>` block — `CONFIG.PASSCODE` and `CONFIG.HINT`. Pick something only the recipient would know, and don't reuse a real password from elsewhere.
- **Swap the photo**: replace the base64 string in the `<img src="data:image/jpeg;base64,...">` tag. Keep it compressed (a few hundred KB max) so the page stays light.
- **Rewrite the letter**: it's plain HTML inside `<div class="letter">` — no templating engine, just edit the paragraphs directly.
- **Restyle it**: all colors and fonts are CSS custom properties at the top of the `<style>` block (`--term`, `--rose`, `--amber`, etc.) — change the palette without touching layout code.
- **Adjust the boot log**: edit the `BOOT_LINES` array in `CONFIG` to change what scrolls past before the auth gate appears.

---

## License

This project is released under the **MIT License** — free to use, modify, and share.
See the `LICENSE` file for details.

---

## Author

<p align="center">
  <a href="mailto:dhrubamajumder@proton.me" target="_blank">
    <img src="https://img.shields.io/badge/Email-Dhruba%20Majumder-blue?logo=gmail" alt="Email Badge">
  </a>
  <a href="https://www.linkedin.com/in/iamdhrubamajumder/" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-Dhruba%20Majumder-blue?logo=linkedin" alt="LinkedIn Badge">
  </a>
  <a href="https://github.com/D-Majumder" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-D--Majumder-black?logo=github" alt="GitHub Badge">
  </a>
</p>
