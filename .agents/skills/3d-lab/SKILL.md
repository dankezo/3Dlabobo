# 3D Lab

Build and reproduce interactive 3D machine labs as single-file Three.js pages: a hub that only navigates, and one self-contained HTML page per lab.

## When to use this skill

- Add a new lab to the 3D Lab, reproduce Lab 01 or Lab 02 from scratch, or edit the hub.
- Work on a machine teardown, a hydraulic press, or any machine that must be taken apart, pressed, or driven by one solver.
- Do NOT use it to fold a lab back into another lab's page: every lab stays on its own page, and the hub only links to labs, never embeds them.

## Repo map

```
3Dlabobo/
├── index.html                        # Hub - 2 redirect tiles (Lab 01 + Lab 02)
├── labs/
│   ├── lab-01-cat-jelly-press/       # Lab 01 Cat Jelly Press (index.html + press.html)
│   └── lab-02-mecha-cat-teardown/    # Lab 02 Mecha Cat Teardown (index.html + docs)
├── trials.html                       # Trial models (Dragon, Sandworm, Laser Gun, Mega Poro)
├── favicon.png                       # Angular mecha cat head
├── social-preview.jpg                # 1280x640 repo social preview
└── README.md                         # English + links to VI / ZH-CN / ES / RU
```

- Live site: https://dankezo.github.io/3Dlabobo/
- Lab 01 source repo: https://github.com/dankezo/cat-jelly (this repo holds a copy under `labs/lab-01-cat-jelly-press/`; the cat-jelly repo stays the source of truth for the game).
- Lab 02 source: this repo, `labs/lab-02-mecha-cat-teardown/index.html`.

## The labs

### Lab 01 - Cat Jelly Press (press-only)

- Hydraulic press for jelly cats. Hold to press up to 400 bar; cats flatten, crack and burst into material-specific debris.
- Base press is the default; VFX are always on, no FX button. Up to 12 cats, no shrinking, real collision and stacking.
- 7 materials (glass, iron, diamond, jelly, brick, water balloon, toy brick) with distinguishable cracking. Rare Gen objects at 20%: poop, watermelon, Chii, mini press, bomb - all spawn at fixed size 1.4.
- Physics bar: no object may lose physics or pass through the column, platen, table, or another object in any size, material, position, spawn, drop, drag, throw, stack, or just-broken case. Soft liquid cats bounce lightly then settle; hard cats land dead.
- Per-cat HP lives only in the 16-segment ring at the cat's feet. No READY card, only a gentle hint.

### Lab 02 - Mecha Cat Teardown

- Procedural Three.js mecha cat (Mecha Cat MK-IV, quadruped), driven by ONE solver: a single crank/servo phase φ, 0-120 RPM. Gait is a trot (FL+BR at φ+0°, FR+BL at φ+180°), each leg solved with 2-bone IK (law of cosines) from the foot target. Never hand-animate joint angles.
- Take it apart subsystem by subsystem: Head, Energy core, Chassis, Tail, Leg FL/FR/BL/BR, plus Assembled. Explode pushes parts OUTWARD/LATERALLY, never downward. X-Ray fades the armour to reveal frame and core.
- Console: four live charts (servo torque, core temperature, foot lift, power draw) as floating HUD cards over the stage; page locks to one screen with no scroll. MODEL switcher under the header: Ceramic 55 RPM, Stealth 85 RPM (X-Ray skeleton), Hazard 35 RPM (stress 130%, explode 35%).
- Full reproduction pack: `labs/lab-02-mecha-cat-teardown/` holds `MASTER_PROMPT.md` (the whole build, verbatim), `README.md`, `TOOLS.md`, `tour.md`. To reproduce from scratch, paste the master prompt into a coding agent with the tools in `TOOLS.md`.

## Hard rules (learned the expensive way)

- **Angular heads only.** The user hates round/blob heads. Mecha heads are extruded wedge prisms (visor slits, cheek guards, hinged jaw, nose spike, pointed ears, blade crest, antenna). ZERO `SphereGeometry` anywhere.
- **Neck clearance is numeric.** Head counter-pitch dips the skull ~0.022, so every neck part must top out at y≈0.05 with ≥0.025 clearance at full head dip. Verify by numbers, not by eye.
- **Details sit PROUD of surfaces.** Never coplanar with armour, or they z-fight in motion.
- **Whiskers fan OUTWARD.** Build each from an explicit outward direction vector; verify the z-component numerically.
- **Full-screen, no slop.** The main 3D scene runs edge-to-edge, never inside a rounded card or frame. No long intro text; docs live behind one toggle.
- **Ship limit: single HTML file under 2 MB** (user-set 2026-11-12, replacing the old 1 MB rule). Three.js may be inlined.
- **Critic gate before showing anyone:** render stills at every tour beat, press every button and slider yourself, fix what fails, re-render.
- **Tour yields instantly:** any user interaction stops the self-driving tour and hands over control.

## Method reference

- Teardown skill (free, MIT): `npx skills add elvarofficial/teardown` - repo https://github.com/elvarofficial/teardown, demo https://visual-learning.app. Read as the method reference only; do not copy its shipped machines (V8, Cessna landing gear, Strandbeest). The Lab 02 build adapts its recipe to Muse + Three.js.

## Required tools

- Node.js 20+, Three.js (r128, classic build, global `THREE`), Python 3, ffmpeg (video follow-on only), Playwright + Chromium (critic gate).
- Publishing: GitHub Pages from `main`. Split large pushes into one file per commit; verify each commit by read-back and the live URL by hash before calling it live.

## Adding a new lab

1. Write its master prompt, docs, and tools list first, in `labs/<lab-slug>/`, following the Lab 02 pack as the pattern.
2. Build it as ONE self-contained HTML page under the 2 MB ship limit, on its own page.
3. Add one redirect tile to the hub (`index.html`) linking to it. The hub never embeds a lab.
4. Push only the version the user explicitly approved, naming the exact build and the previous live commit.
