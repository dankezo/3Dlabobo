# Lab 02 - Mecha Cat Teardown

Disassembly of making a mecha cat: a standalone 3D teardown simulator you can
take apart, subsystem by subsystem. Built 2026-11-10 from the workflow in
`../../../WORKFLOW-lab2-mecha-cat-teardown.md`, which converts Elvar's post
"How I Turn Any Machine Into a 3D Simulator You Can Take Apart"
(https://x.com/elvar_official/status/2116174609355571402, 30 Oct 2026)
into a 9-step workflow. Approved by the user 2026-11-10 02:31 UTC, run
immediately after approval.

## What it is

- One interactive 3D mecha cat (Mecha Cat MK-IV, quadruped robot cat).
- One moving input drives everything: a single crank/servo phase φ, 0-120 RPM.
  Gait is a trot: FL+BR at φ+0°, FR+BL at φ+180°. Each leg is solved with
  2-bone IK (law of cosines), never hand-animated joint angles.
- Every subsystem is a button: Head, Energy core, Chassis, Tail, Leg FL / FR /
  BL / BR, plus Assembled. Pressing one detaches that subsystem in an exploded
  move while the rest steps aside; an Explode-all slider drives all of them
  together; an X-Ray toggle fades the armour to reveal frame and core.
- Console: four live charts with running min/max - servo torque (N·m), core
  temperature (°C), foot lift (mm), power draw (W) - as frosted-glass HUD
  cards floating over the 3D stage, torque + foot lift in the left column,
  temperature + power in the right column; the page locks to one screen with
  no scroll. Subsystem buttons (Head, Energy core, Chassis, Tail, Leg
  FL / FR / BL / BR, plus Assembled) detach parts in an exploded move while
  the rest steps aside; an Explode-all slider drives all of them together;
  an X-Ray toggle fades the armour to reveal frame and core. A MODEL
  switcher bar sits directly under the header with three real machine
  configs - Ceramic 55 RPM (standard, assembled), Stealth 85 RPM (dark
  shell, X-Ray on), Hazard 35 RPM (130% stress, 35% exploded view) - each
  switching the machine's look and numbers. Buttons use one system: 6px
  radius, thin borders, dark-ink selected state, single "Load model file"
  button. The "You have the controls - drag to orbit, scroll zoom" caption
  line was removed 2026-11-11. "Load this machine" accepts a JSON config
  `{"name","rpm","stress","explode","xray"}`.
- Self-driving tour on load with a visible fake cursor that presses the real
  buttons; any touch stops the tour and hands over control. Camera stays
  committed, machine stays in frame.
- Bonus: stress slider 100-160 % of rated load; over 135 % the machine visibly
  complains (torque, temperature and warnings climb together).

## What it is NOT

- NOT the mecha robot cat inside Cat Jelly Press. That direction was reversed
  on 2026-11-03 as too laggy and stays reversed. Cat Jelly Press stays
  press-only; the mecha cat lives only as its own lab.
- The step-8 video (render(t), 60 fps, 1920×1080, 30 s cut, ffmpeg score) is a
  follow-on run from this page, not shipped inside it. Sound is Web Audio
  synthesis, no audio files (old-metal clank for the cat, domino clacks for
  the worm).

## Machine numbers (checked on paper before coding)

| Item | Value |
| --- | --- |
| Drive input | 1 crank / servo phase φ, 0-120 RPM |
| Gait | trot · FL+BR φ+0°, FR+BL φ+180° |
| Upper leg L1 / lower leg L2 | 0.55 m / 0.55 m |
| Hip height | 1.02 m |
| Stride length | 0.62 m (±0.31 m) |
| Foot lift | 0.16 m |
| Leg solver | 2-bone IK, law of cosines |
| Body bob | 0.022 m · sin 2φ |
| Tail | 5 segments · travelling wave |
| Stress range | 100-160 % of rated load |
| Rated core temp | ≤ 74 °C at 120 RPM / 100 % |

## How to run it

- Source: the live prod build is a single self-contained file
  `~/workspace/3dlabobo/index.html` - 1,244,349 bytes, commit `f6680c81`
  (2026-11-11 ~17:13 local), Three.js inlined, no separate `three.min.js`
  reference and no external requests. (Rev 2 was 69,016 bytes plus a
  separate `assets/three.min.js` at 865,452 bytes; the file grew past the
  workflow's old 1 MB ship rule when Three.js was inlined - the user set a
  new 2 MB ship limit on 2026-11-12, and the live file fits it - see Status.)
  The Muse artifact source lives at
  `~/workspace/ts-spaces/mecha-cat-teardown/` (`index.html` +
  `assets/three.min.js`).
- Open `index.html` in a browser (WebGL). The tour autoplays; touch anything
  to drive it yourself. Drag to orbit, scroll to zoom.
- To reproduce from scratch: paste `MASTER_PROMPT.md` into a coding agent
  with the tools in `TOOLS.md`, and follow the 9-step workflow in
  `../../../WORKFLOW-lab2-mecha-cat-teardown.md`.

## Tour script

See `tour.md` for the 7 beats, what each one shows, and the critic-still status.

## Status - honest, as of 2026-11-11 ~17:38 local

- **Rev 2 overhaul (2026-11-10 ~04:21-04:27 UTC), built from the user's screenshot:** the user hated the round/blob head, found the neck flickering and the cat walking backwards. Fixed in the artifact build (`index.html`, rebuilt 04:23 UTC, 69,016 bytes): angular wedge-prism head with zero SphereGeometry; neck rebuilt as a gimbal collar with real clearance; appliqué details offset proud of surfaces; gait sign flipped so the stance foot sweeps backward and the head leads. Verified in code only (grep of the built file): no `SphereGeometry`, `fx = -stride * Math.cos(th)` with a comment that the old + sign walked the cat backwards, 7 gimbal/collar mentions, `DIRECTION CHECK` text. NOT verified by eye: the 04:23 audit failed again (`ok: false`, both captures timed out at 15 s navigating, no screenshots), same as the two earlier audits.
- **One planned fix is missing from rev 2:** the overhaul plan said to add a floor chevron/arrow so the walking direction can never be misread again, but the built file contains no `chevron` and no `arrow` - only the DIRECTION CHECK text. Flag before calling the gait done.
  - Update 2026-11-10 17:39 local: a chevron patch is now prepared as a LOCAL DRAFT only in `~/workspace/3dlabobo/index.html` (SHA256 `df1bfa70f296b464915f8a156b1acabdade74e126e30ace7d8169d342a96acd1`, inline JS syntax-checked with `node --check`): three orange `>` chevrons at x=1.25/1.60/1.95, z=+0.95, y=0.004, pointing +X.
  - Update 2026-11-11 00:50 local: chevron PUSHED to prod as commit `1bb29937` (SHA256 `b701eafe…`, 1,223,993 bytes); live fetch matched the local hash exactly. Browser visual check 00:53-00:54: two chevrons fully visible pointing +X, the third (x=1.95) clipped behind the tour caption bar - the caption overlay was the cause, fixed in rev 2.1 by moving the caption below the stage.
  - Update 2026-11-11 02:47 local, rev 2.1, commit `2b213965` (SHA256 `8572aef1…`, 1,225,964 bytes): neck clearance fix - rev-2 slab behind the collar crossed the collar ring and the gimbal block under the jaw was hit by the throat plate every gait cycle (head counter-pitch dips the skull ~0.022); slab replaced by a hub cylinder (r=0.09) inside the ring, block removed, struts/piston lowered and slimmed so every neck part tops out at y≈0.05 with ≥0.025 clearance at full head dip. Layout: tour caption is now a slim static bar under the stage, the subsystem bar is no longer sticky, and the docs section is collapsed behind one toggle button, so the page no longer overflows with text. Live fetch at 02:50 matched the local hash exactly. Browser visual check 02:50-02:54 confirmed the neck fix, caption, subbar, collapsed docs and live tour/solver - but the third chevron still clipped at the stage's bottom edge in the default framing.
  - Update 2026-11-11 02:54 local, rev 2.1.1, commit `a092abbb` (SHA256 `491f6389…`, 1,226,430 bytes): chevron trio moved inward from x=1.25/1.60/1.95 to x=1.05/1.38/1.71 so all three fit the default framing, plus a visible REV 2.1.1 chip in the header. Live fetch at 02:59 matched the local hash exactly. Browser visual re-check 02:59-03:02 passed: all three chevrons fully visible in the on-load assembled view (confirmed in three captures), neck clean, caption below the stage, docs collapsed, cat walking (55 RPM, 0.92 Hz, FPS 20-40). Caveat: the first load served a cached older version (no REV chip, third chevron clipped); a reload showed rev 2.1.1.
- **Rev 3 + prod push (2026-11-11, artifact then prod commit `f6680c81`,
  SHA256 `029e0453…`, 1,244,349 bytes):** the user judged the cat still
  super ugly/rustic vs the teardown projects on X and chose the Elvar
  teardown standard. Rev 3.0 rebuilt the look only (solver, gait, tour,
  explode, X-Ray unchanged): ceramic clearcoat shell over a gunmetal frame,
  longer low predator proportions, hex bolts, cables, twin hydraulic
  pistons per leg, steel-cored core, smoke-slit visor, studio turntable
  with measurement marks, one orange accent. Then, from the user's
  screenshots and notes the same day: HUD stats floated left/right over
  the stage (see "What it is"), page locked to one screen, Lab docs moved
  into a slide drawer, long AI-slop intro removed, main 3D scene full-screen
  edge-to-edge with no rounded card/border/shadow/frame, whiskers rebuilt
  to fan outward (3 per side, backward sweep, tapered tips - verified in
  code: "Whiskers fan OUTWARD and sweep back"), Explode All moved to a
  floating right panel and its explode direction changed from downward to
  lateral so feet no longer sink through the floor, buttons restyled to
  one 6px-radius system, the "You have the controls" caption line removed,
  and a MODEL switcher bar added under the header (Ceramic 55 RPM /
  Stealth 85 RPM with X-Ray / Hazard 35 RPM, 130% stress, 35% exploded).
  Verified against the prod file itself (2026-11-11 ~17:38 local): all
  three MODEL buttons present with their configs, caption 0 occurrences,
  "Rev 3 - Elvar look rebuild" card present, whisker-outward code present,
  no `labstrip`/`cat-jelly` text left in the mecha page. Live byte check
  passed (served file SHA matches the export). NOT verified by eye: the
  automated browser check timed out twice with no screenshot, so the
  switcher position, the restyled buttons and the 3D render on prod still
  need the user's eye check - asked in the main chat at 17:14 local,
  no reply yet. Note: the single file is now 1,244,349 bytes, over the old
  workflow step-8 "single HTML under 1 MB" rule, because Three.js is
  inlined; resolved 2026-11-12 - the user set a new 2 MB ship limit and
  the live file fits it.
- **Prod push landed (supersedes the 11:40 local 404 note):** repo `dankezo/3Dlabobo` was created in the browser at 17:05 local on 2026-11-10 (API creation failed 403), commit `fc65aa84` pushed, Pages deployment #1 ran 17:06-17:07 and the site is live at https://dankezo.github.io/3Dlabobo/ - the 17:07 404 was CDN delay of ~2 minutes. Current prod is commit `f6680c81` (see Rev 3 update above), not rev 2.1.1. User's phone verdict on head-first gait and neck is still pending, plus the new eye check on the MODEL switcher and restyled buttons.
- **Separate pages, not inside the mecha page:** the 3D Lab landing hub
  (character at a desk, big monitor, search, Lab 01 / Lab 02 tabs, per-lab
  preview, "Open lab" in a new tab) was delivered 2026-11-11 as its own
  artifact, and a Trial Models page with four switchable models
  (mechanical dragon, giant sand worm, Mega Laser Gun, Mega Poro, each
  with panel gaps, hex rivets, cables, pistons and its own motion) was
  delivered the same day as its own artifact - neither is pushed to prod,
  and neither is embedded in the mecha page, per the user's instruction
  that each page stays separate and the landing only navigates.
- Critic gate (workflow step 6) STILL NOT passed: three automated audits (02:36, 02:39, 04:23 UTC) all failed with `ok: false` on nav timeouts, no formal stills at every tour beat. The user overrode the gate by ordering a direct prod push so he can check it himself on prod - that is his call, not a pass. The earlier probe (02:39 audit observe screenshots) showed one tour beat only.
- No reference image was supplied: workflow step 2 asks for one cutaway /
  exploded-view reference before building, and the user never answered that
  open decision before approving the run. The cat was modelled procedurally
  with no reference. If the user sends a reference image, the look should be
  re-checked against it before calling the lab finished.
- Repo decision: the user asked whether to rename `cat-jelly` into
  `3Dlabobo`; the workflow recommends creating a new `dankezo/3Dlabobo` repo
  instead so the live cat-jelly Pages site is untouched. At 04:27 UTC Muse
  said it was pushing rev 2 to the new `3Dlabobo` repo - confirmed landed:
  repo created in the browser, commit `fc65aa84`, Pages deployment #1 live,
  now at commit `f6680c81` (Rev 3, see above).
- Landing desk scene (character at a desk, big monitor as the interactive
  surface, preview/search/navigate/back/fork): delivered 2026-11-11 as a
  SEPARATE landing artifact, not inside the mecha page - see the update
  above. It is not pushed to prod yet.

## Files in this pack

- `README.md` - this file.
- `MASTER_PROMPT.md` - the master prompt, verbatim from the built page.
- `TOOLS.md` - required tools / CLI / skills, with versions.
- `tour.md` - tour beats and critic-still status.
- Source page: `~/workspace/3dlabobo/index.html` (prod, commit `f6680c81`)
  and the artifact source `~/workspace/ts-spaces/mecha-cat-teardown/index.html`
  (+ `assets/three.min.js`).
- **Rev 3.1 phone UX (2026-11-11 19:03-19:05 local, commit `3b190793`, SHA256 `dbb60815…`, 1,247,648 bytes):** user phone screenshot (390px) showed the floating HUD columns covering the cat, MODEL and DETACH bars cut off, and detach buttons that could not be exited by tapping again; he also asked where the worm etc. models are. On phones (≤640px) the HUD now leaves the canvas and becomes a plain 2-column strip under the stage, the page scrolls, stage is 54dvh full-width; detach buttons toggle (tap the active one again → Assembled), Assembled stays pinned left in the DETACH bar and Load stays pinned right in the MODEL bar while both bars scroll. Trial Models page published as `trials.html` in this repo (SHA256 `527d35d2…`, copied unchanged from the trial-models artifact: dragon, sand worm, Mega Laser Gun, Mega Poro) and linked from the model bar. Live fetch at 19:05 matched both local hashes exactly; mobile browser check at 390px pending.
