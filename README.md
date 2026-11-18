# AWS re:Invent Booth Screen: Agent Governance Mini-Theater

A self-contained, zero-dependency booth screen for the AWS re:Invent mini-theater. One HTML file carries a 16-scene agent-governance narrative in a 102.4-second attract loop (6.4 seconds per scene), plus a presenter mode for booth staff. Everything runs offline in kiosk Chromium: no network requests, no build step, no frameworks.

**Live page:** https://ccondado-cell.github.io/rhai-agentic-ai-booth-screen/

## What it is

The screen tells one story in three movements: agents are multiplying faster than controls (market), Red Hat AI runs five controls on every agent (spine: Sandbox, Gateway, Traceability, Proof, Identity), and the platform scales from 10 to 1,000 agents under one control plane (scale). Copy is locked at v3.7; headlines max 7 words, support lines max 12, one calm continuous animation per scene, 3-second read per scene.

- 16 scenes, 6.4s each, 102.4s loop
- Vanilla HTML/CSS/JS in a single `index.html`
- All assets local (fonts, official Red Hat AI 3D backdrops, Red Hat icon repository glyphs, generated art)
- Attract loop (auto-advancing) and presenter mode (manual control)

## Run it

Open `index.html` in any modern browser. No server needed.

For the booth kiosk (Chromium, no mouse, starts fullscreen on the loop):

```bash
chromium-browser --kiosk --noerrdialogs --disable-infobars \
  --check-for-update-interval=31536000 \
  file:///path/to/reinvent-booth-screen/index.html
```

## Controls

| Input | Action |
|---|---|
| Right arrow / Space / PageDown | Next scene (enters presenter mode) |
| Left arrow / PageUp | Previous scene |
| P | Pause the loop / resume |
| F | Toggle fullscreen |
| Click right half of screen | Next scene |
| Click left half of screen | Previous scene |
| Double tap (touch) | Toggle fullscreen |

Presenter mode takes over after any manual input; the pause pill in the corner toggles back to the attract loop.

## Repository layout

```
index.html          The screen (everything: HTML, CSS, JS)
assets/             Backdrops, generated art, icon repository glyphs, logo
fonts/              Red Hat Display / Red Hat Text (woff2)
docs/               Design brief, locked copy document, implementation addendum
```

Design record lives in `docs/`: the scene-by-scene brief, the copy document with version history (v3.1 through v3.7), and the implementation addendum (asset manifest, motion decisions, measured geometry).

## Asset credits and usage

- **3D scene backdrops:** official Red Hat AI brand assets.
- **Environment and DevOps icons:** the official Red Hat Icon Repository (app-on-server, virtual-server-stack, cloud, cloud-private, sovereign-cloud, edge, devops glyphs).
- **Generated art (scene 7, 8, 14 backdrops):** created with Gemini image generation.
- **Fonts:** Red Hat Display and Red Hat Text.

These brand assets are Red Hat property and are provided here for this Red Hat project only; they are not licensed for reuse under the repository code license. See `LICENSE`.

## Maintenance

The screen is copy-locked: any wording change needs a word-count check (headline <= 7 words, support <= 12, no em or en dashes) and a pass over the validation rules recorded in `docs/addendum.md`. Keep `index.html` self-contained: no external requests, no build tools.
