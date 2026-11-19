# Workflow - Lab 2: Disassembly of Making a Mecha Cat

Source: Elvar (@elvar_official), "How I Turn Any Machine Into a 3D Simulator You Can Take Apart", 30 Oct 2026, https://x.com/elvar_official/status/2116174609355571402
Reference skill: teardown (free, MIT), github.com/elvarofficial/teardown - demo site visual-learning.app
Adaptation note: the original skill runs inside Claude Code. This workflow adapts its recipe to Muse + Three.js, the stack already used for Cat Jelly Press. No text from the article is reproduced here beyond short paraphrase; the workflow below is a summary in our own words.

## 0. What Lab 2 is (and is not)

- Lab 2 is a standalone teardown simulator: one interactive 3D mecha cat you can orbit, cut open, x-ray and take apart, subsystem by subsystem.
- It is NOT re-adding the mecha robot cat to Cat Jelly Press. That direction was reversed on 2026-11-03 as too laggy and stays reversed. Cat Jelly Press stays press-only; the mecha cat lives only as its own lab.
- Deliverable: one HTML page, target ~800 KB, works offline, no sign-in, no client-side loading. Same 6 parts as every simulator in the recipe: machine, model, panels, buttons, window, tour.

## 1. Lab structure - 3D Lab (proposed, needs approval)

- New home repo proposed: `dankezo/3Dlabobo` (name exactly as the user wrote it; renaming the existing `cat-jelly` repo instead is an alternative - see open decision below).
- Landing page at repo root: a 3D desk scene - a character sitting at a desk with a large monitor. The monitor is the interactive surface: preview each lab, search/find a lab, navigate into it, go back, fork/test a lab.
- Lab 1 (sub-lab): Cat Jelly Press, moved in as-is under `labs/lab-01-cat-jelly-press/`, keeping its current prod behaviour unchanged.
- Lab 2 (sub-lab): Mecha Cat Teardown, under `labs/lab-02-mecha-cat-teardown/`.
- Every lab ships a reproducibility pack (see §6).

## 2. Workflow steps (adapted from the teardown recipe)

### Step 1 - Set up tools
- Node.js 20+, ffmpeg and Python 3 (video/sound only), Playwright + Chromium (stills + tour recording).
- Read the teardown skill repo as reference (MIT, free). Do not copy its shipped machines; use its recipe only.
- Stack for Lab 2: single HTML + Three.js, same as Cat Jelly Press.

### Step 2 - Pick the machine and one reference
- Machine: mecha cat. One moving input drives everything (proposed: a single crank/servo cycle driving the walk gait - see open decision).
- Find one reference picture before building: a cutaway, patent drawing, photo from any angle, or exploded view of a robot cat / quadruped robot. No reference = generic machine, parts clip through the floor. This step decides everything.
- Define real numbers first and check they agree on paper (same discipline as the article's rack-and-gear example: if the numbers don't agree, compute them before building).

### Step 3 - Build the machine, model first
- Model first: a single solver/function is the source of truth. Gauges, panels and timeline all read the same model, so nothing can drift apart.
- One input poses the whole mechanism. Hand-animating 12 parts separately is not a mechanism.
- Mecha cat subsystems (proposed): head + jaw, torso/chassis, 4 legs (hip/knee/ankle servos), tail, power core, sensor eyes. Every subsystem is a button; pressing it takes that part apart while the rest steps aside to make room.
- Views: normal, x-ray, exploded, cut. Tracked part turns to glass so you can watch the inside work.

### Step 4 - Build the console (1600×900)
- Title + main live number top-left, readable at a glance.
- One live chart per quantity worth watching, each with a moving line plus min/max.
- Bottom button row, always visible: one button per subsystem, plus replay.
- Gauges read the same model as the machine.

### Step 5 - Give it the look
- Clean study model on a pale studio: light background, soft shadows on an invisible floor, thin outlines, one strong accent colour.
- Each part a clean solid with a visible material; thin lines only for hidden detail.
- White/pale/translucent panels, black text.
- Log every look fix as its own correction (e.g. a colour that vanished into the background, a part poking through another part) and read each one before moving on.

### Step 6 - Check it like a critic (gate before showing anything)
1. Render a still at every beat of the tour and read each one: parts passing through each other, missing shadow, gap between floor and foot, cut-off text, a chart that doesn't move, a number that disagrees with the machine.
2. Open the page, click every button and slider yourself, fix anything that doesn't work.
3. Fix, re-render the stills, show only the fixed ones.

### Step 7 - Make it a page you drive
- Autoplay tour on load, with a cursor that moves and clicks by itself; click anywhere and the tour stops - it's yours to drive.
- Full console returns: buttons, gauges, charts. Machine stays inside the frame, camera still.
- Performance gate: 60 fps on an integrated GPU. If it drops (the article's hexapod ran 15 fps before fixes), cut the shadow map and move every moving thing to one Update, then re-test.

### Step 8 - Turn it into a video (optional, after the page works)
- render(t) must be a pure function of time; draw every frame at 60 fps, 1920×1080, keep the camera still, cut to 30 seconds (1,800 frames).
- Score in code on the same timeline with ffmpeg (sound aligned to the machine's cycle).

### Step 9 - Put it online
- HTML under 1 MB; move any large model out as a file next to it.
- Page with buttons + full panel grid, autoplay tour, a "Load this machine" button, no sign-in.
- Test on a phone and on a computer with integrated GPU: instant to read, alive in the first 3 seconds.

### Bonus - Let them break it
- One slider that pushes the machine past its limit (e.g. servo speed / load), model runs live, red warning when it stalls/slips. Whoever pushes past the limit learns what every number does.

## 3. Lab 2 tour (proposed, 25s to learn / 60s to trust)

1. Idle: mecha cat in a walk gait, panels live.
2. Leg 1 isolated, joint by joint, then all 4 legs.
3. Head opens down to its mesh; dome/shell splits into layers.
4. Torso opens; spine/power core bursts into parts.
5. Full x-ray pass over every subsystem, then reset.

## 4. Acceptance criteria (done = all of these)

- [ ] Single HTML, <1 MB, loads offline, no sign-in.
- [ ] One input drives the whole mechanism; gauges/panels/timeline agree with the model.
- [ ] Every subsystem has a button; disassembly works without parts passing through each other.
- [ ] Tour autoplays, click takes control, camera stays still, machine stays in frame.
- [ ] Critic stills pass at every tour beat; every button/slider clicked and working.
- [ ] 60 fps on integrated GPU; phone test passes; alive in the first 3 seconds.
- [ ] Reproducibility pack complete (see §6).

## 5. Open decisions (need the user before / during the run)

1. Repo: create new `dankezo/3Dlabobo` with cat-jelly as Lab 1, OR rename `cat-jelly` to `3Dlabobo`? Renaming changes the repo URL and Pages URL; creating new keeps cat-jelly live untouched. Recommended: create new.
2. Reference image for the mecha cat: user to attach one (cutaway / exploded view / photo), or let Muse pick a robot-quadruped reference and show it for approval before building.
3. The single moving input: proposed walk-gait crank/servo cycle. Alternative: a servo-test cycle (sit → stand → walk).
4. Landing desk scene: character style - reuse the settled avatar style (short bob, big glasses) or a new lab character? Proposed: reuse the settled avatar style for consistency.

## 6. Reproducibility pack - every lab ships this

Per lab, in `labs/<lab>/`:
- `README.md` - full docs: what it is, how it works, how to run it, tour script.
- `MASTER_PROMPT.md` - the master prompt that reproduces the lab (machine definition, model numbers, console, look, critic checklist).
- `TOOLS.md` - required tools / CLI / skills to reproduce it, with versions (Node, ffmpeg, Python, Playwright, Three.js, teardown reference, Muse skills used).
- `tour.md` + critic stills - the tour beats and the stills that passed.
- Source: the single HTML file + any external model files next to it.

## 7. Run rules after approval

- Run the steps in order, 1-9 + bonus, until completion; do not skip the critic gate (Step 6).
- Build in the artifact / workspace first; nothing goes to prod (Pages / new repo) without a separate named-build approval, per the standing release gate.
- Report progress per step with what was verified by hand vs. by code check only.
