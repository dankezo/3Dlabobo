# 3D Lab Hub - DESIGN.md

Design system for the hub at https://3dlabobo.dannyphan.me/ (repo dankezo/3Dlabobo, root index.html).
Style reference: https://dannyphan.me/ (measured 2026-11-19, full note in ~/workspace/research_notes/3-x-links-dannyphan-style-20261119.md).
Rework approved by the user 2026-11-19: steel-workshop style replaced by the dannyphan.me deck style.

## Tokens

| Token | Value | Use |
|---|---|---|
| `--bg` | #080A0D | Page background |
| `--panel` | #131417 | Tile background |
| `--panel-2` | #0B0E11 | Tile art background |
| `--ink` | #F2EEE4 | Headings, primary text (warm white, never pure white) |
| `--muted` | #A3ABA4 | Body text, tags |
| `--dim` | #8A928C | Mono labels, URLs, hints |
| `--accent` | #9FE035 | Lime - the ONE accent (buttons, live dots, hero line 2, focus ring) |
| `--accent-ink` | #0B0E06 | Text on lime buttons |
| `--line` | rgba(242,238,228,.14) | Hairline borders |
| `--line-soft` | rgba(242,238,228,.08) | Soft hairlines |
| `--radius` | 4px | Cards (near-square, like dannyphan.me) |
| Pills | 999px | Buttons, tags, live pill |
| `--ease` | cubic-bezier(.22,1,.36,1) | Ease-out, 150-200ms |

Contrast (computed 2026-11-19): lime #9FE035 on #080A0D = 12.45:1, muted #A3ABA4 = 8.42:1, dim #8A928C = 6.20:1, ink #F2EEE4 = 17.11:1, accent-ink on lime = 12.21:1. All pass 4.5:1.

## Type

- Display: Be Vietnam Pro 900, uppercase, tracking -0.02em. Hero clamp(56px, 9vw, 120px), two lines, line 2 lime.
- Body: Be Vietnam Pro 400/500/600, 14-18px, line-height 1.6.
- Labels/numbers/URLs: IBM Plex Mono 500/600/700, 11-12px, letter-spacing .1-.14em, uppercase. Mono separators use `//`, never middle dots.
- One type scale, one button system, one radius per level.

## Layout

- Fixed header 64px, blurred dark, brand left ("● 3DLABOBO // LAB"), nav center (LABS / GITHUB / DANNYPHAN.ME), status right ("HÀ NỘI, VN - ĐANG MỞ", hidden under 860px).
- Content max-width 1440px, left-aligned, padding 24px (16px on phone).
- Hero: kicker mono, huge 2-line title, one sentence, 3-stat row (03 labs / 400 bar max press / Rev 3.9.4 latest). All numbers real.
- Tiles: 2-column grid (1 column under 860px), 2 redirect tiles only, no embedded tests, links open in a new tab.
- Footer: hairline top, redirect-only note + "3DLABOBO // 3 LABS // VI / EN".

## Tile art (typographic until GIFs arrive)

- No drawn SVG previews, no fake imagery. Tile art is a flat panel with: LIVE pill, LAB / 01 code, one big display value (400 BAR / REV 3.9.4 / WEBGPU), one mono spec line, one giant faint number (01 / 02 / 03 at 5% ink).
- GIF slot: when the user's two 3-5s gameplay clips arrive, process them (LosslessCut trim without re-encode + Real-ESRGAN upscale) into GIFs and replace the `.tile-art` content. Keep the LIVE pill and LAB code. Do not ship a drawn preview in the meantime.
- Favicon: favicon.png wired in `<head>` (was `data:,` before this rework). Social preview: social-preview.jpg via og:image.

## Motion

- Ease-out 150-200ms only. Hover: tile lifts 2px, border turns lime-faint. One 200ms fade on the hero at load, nothing else.
- No tilt, no sparks, no canvas, no JavaScript on the hub at all (static redirect page).
- `prefers-reduced-motion`: all animation and transitions off, hover lift off.

## Hero video

- Files: `assets/hero-workshop-press.mp4` (1280x720, 10s, h264, no audio track, 4.4 MB) + poster `assets/hero-workshop-press-poster.jpg` (frame at 1s, 78 KB).
- Generated 2026-11-19: hydraulic press flattening a translucent jelly cat in a dark 3D workshop, lime rim light, blurred background. Chosen by the user for the hero; the mecha variant ships on the Lab 02 tile (see Tile videos).
- Behaviour: autoplay, muted, loop, playsinline, no sound, on every screen (the old `<source media="(min-width: 861px)">` desktop-only gate was removed 2026-11-19 after the user found the phone showed only the poster still). Poster still shows while the video loads. CSS blur 3px + scale 1.06 + flat dark veil rgba(8,10,13,.62) so hero text stays readable. prefers-reduced-motion hides the video entirely.
- Loop is a forward replay: press flattens the cat, the video ends with the cat re-inflated, so the loop cut is small. The dark veil + blur soften it further; it reads as a workshop replay.
- Binary files: push-files rejects binaries, so the mp4 + poster go up through the browser web-UI upload, index.html through push-files. Never include the unused mecha video in a push.

## Tile videos

- Lab 01 tile: same `assets/hero-workshop-press.mp4` + poster (reused, one download serves hero + tile). Lab 02 tile: `assets/hero-workshop-mecha.mp4` (1280x720, 10s, h264, no audio, 3.7 MB) + poster `assets/hero-workshop-mecha-poster.jpg`. Lab 03 tile: `assets/lab03-lightwater-tour.mp4` (1280x720, 10s, h264, no audio, 10.0 MB) + poster `assets/lab03-lightwater-tour-poster.jpg` - the same clip as the lightwaterworld fallback tour video.
- Mecha video generated 2026-11-19: angular mecha cat with wedge-prism head on a workbench in a dark 3D workshop, lime circuit lines, slow camera drift, blurred background. Red eyes are the cat's own accent.
- Behaviour: same as hero video (autoplay, muted, loop, playsinline, on every screen since 2026-11-19, poster still while loading, hidden under prefers-reduced-motion). No blur on tile videos - they are the illustration, sharp; flat dark veil rgba(8,10,13,.45) keeps the big value + spec line readable. Typographic value + LIVE pill + LAB code stay on top of the video.
- Real gameplay GIFs still replace these AI videos when the user's 3-5s clips arrive (LosslessCut trim + Real-ESRGAN upscale).

## Rules (house)

- Short hyphens only (-), never long dashes. One accent (lime), one grey family, one icon treatment (text arrows `->`, no icon set needed).
- No gradients, no glass cards, no emoji, no feature-list walls, no invented numbers.
- Phone: 1 column, no horizontal overflow, CTA full width, hit targets min 48px.

## QA gate

- Spec checklist (this file) confirmed by the user before building.
- Independent QA reads the file against the checklist element by element.
- Live check after push: deployment timestamp advances + hard reload, desktop render + 390px phone check on the user's device (his eye is the deciding check).
