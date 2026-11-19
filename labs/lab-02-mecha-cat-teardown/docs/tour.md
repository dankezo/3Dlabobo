# Tour - Lab 02 Mecha Cat Teardown

Self-driving tour, 7 beats, ~2.9 s per beat, loops until the user touches
anything. Any pointer interaction stops the tour instantly and hands over
control. Camera is committed during the tour; the machine never leaves the
frame. (Verbatim from the built page's `tourSteps`, in order.)

## Beats

1. **Crank spins up** - "The crank spins up - one input (φ) drives all four
   legs through the IK solver." Sets crank to 55 RPM.
2. **Energy core** - "Energy core - press its button and the reactor, rings
   and lens covers detach while the cat keeps walking." Detaches `core`.
3. **Head** - "Head - skull, ears, eyes, muzzle, whiskers and the sensor
   grille separate as one subsystem." Detaches `head`.
4. **Front-left leg** - "Front-left leg - hip motor, upper leg, knee, shin
   and paw split apart mid-stride." Detaches `legFL`.
5. **X-Ray** - "X-Ray - armour fades so the frame, ribs and core show
   through." X-Ray on.
6. **Stress test at 150 %** - "Stress test at 150 % - stride, torque and core
   temperature all climb past rating. Watch the charts." Stress 150 %.
7. **Reset** - "Back to rated load, X-Ray off, machine reassembled. The tour
   restarts in a moment - or touch anything to drive it yourself."
   Stress 100 %, X-Ray off, Assembled. Then the tour loops.

## Critic stills - status

- Required by workflow step 6: a still rendered at every beat above, read for
  parts passing through each other, missing shadow, gap between floor and
  foot, cut-off text, a chart that doesn't move, a number that disagrees with
  the machine - then every button and slider pressed by hand, fix, re-render.
- Status 2026-11-10 ~04:40 UTC: **no formal stills exist yet**. Three automated audits
  (02:36, 02:39 and 04:23 UTC - the last one on the rev-2 overhaul build) all
  failed (`ok: false`) - desktop and mobile captures timing out at 15 s, no
  screenshots were produced
  (`~/workspace/ts-spaces/mecha-cat-teardown/audits/2026-11-10T04-23-37Z-525446117/report.json`).
  The second audit's observe screenshots do show the page rendering on
  mobile: `observe-001.png` captures the Head beat (head detached, live
  charts, FPS badge 20 in software WebGL), and `observe-002.png` /
  `act-001.png` capture the controls and docs sections with Energy core
  selected. That is one tour beat only - no stills for core, leg, x-ray,
  stress or reset, and no desktop still. Until stills pass at every beat,
  the critic gate is open and Lab 2 is not done - the user has overridden
  this by ordering direct prod pushes so he can check it himself on prod
  (repo `dankezo/3Dlabobo`, live at https://dankezo.github.io/3Dlabobo/,
  current prod commit `f6680c81` as of 2026-11-11; the 404 noted at 11:40
  local on 2026-11-10 was CDN delay after deployment #1). The Rev 3
  automated checks also timed out twice with no screenshot, so the critic
  gate is still open for the current prod build too.
  Also note from
  `observe-002.png`: on the 390 px view the "DETACH →" label at the left of
  the subsystem bar looks clipped/overflowing - worth a hand check on a
  real phone.
