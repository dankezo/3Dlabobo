# Required tools · CLI · skills - Lab 02 Mecha Cat Teardown

Everything needed to reproduce this lab from `MASTER_PROMPT.md`, with the
versions the built page was made against. Verbatim from the built page's
"Required tools" card, plus the versions the workflow names.

## Runtime

- Node.js 20+ - check with `node --version`. (Teardown skill requirement;
  the page itself is static HTML + Three.js and needs no Node to run.)

## Method reference

- Teardown skill (free, MIT): `npx skills add elvarofficial/teardown`
  - repo https://github.com/elvarofficial/teardown, demo https://visual-learning.app
  - read as the method reference only; do not copy its shipped machines
  (V8, Cessna landing gear, Strandbeest). The Lab 2 build adapts its recipe
  to Muse + Three.js instead of Claude Code.

## 3D

- Three.js - classic build, global `THREE`, procedural modelling, no external
  model files. Rev 3 inlines Three.js into the single file (1,244,349 bytes
  total), under the 2 MB ship limit set 2026-11-12 (replacing the old 1 MB
  rule). Rev 2 shipped it separately as `assets/three.min.js` (865,452 bytes)
  next to the page; total page + library then was 925,852 bytes.

## Video / audio (step 8, follow-on only)

- ffmpeg - `ffmpeg -version` (score laid in on the same timeline).
- Python 3 - capture helpers for the 60 fps / 1920×1080 / 30 s cut.
- This lab is silent by design: no Web Audio, no sound files.

## QA - critic gate (workflow step 6, mandatory before showing anyone)

- Playwright + Chromium - render stills at every tour beat in `tour.md`,
  press every button and slider by hand, fix what fails, re-render.
- Browser APIs used: WebGL, Canvas 2D (charts).
- Status 2026-11-10 ~02:40 UTC: the automated audit at 02:36-02:37 UTC
  failed (`ok: false`, desktop + mobile capture timeouts, no screenshots),
  so the critic gate has NOT passed yet. See `README.md` and `tour.md`.

## Config

- "Load this machine" accepts a JSON config:
  `{"name","rpm","stress","explode","xray"}`.
