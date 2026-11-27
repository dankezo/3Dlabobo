# 🔬 3D Lab

> Open-source library for testing 3D and motion by Danny.

**English** | [Tiếng Việt](README.vi.md) | [中文](README.zh-CN.md) | [Español](README.es.md) | [Русский](README.ru.md)

[![Live](https://img.shields.io/badge/Live-3D_Lab-brightgreen?style=flat-square)](https://3dlabobo.dannyphan.me/)
[![Three.js](https://img.shields.io/badge/Three.js-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/dankezo/3Dlabobo?style=flat-square)](https://github.com/dankezo/3Dlabobo/stargazers)

## 🌐 Live demo

**https://3dlabobo.dannyphan.me/**

Open it and pick a lab. No install, no build, no account. Works on desktop and phone.

## 🧪 Labs

| Lab | What it is | Try it |
| --- | --- | --- |
| **Lab 01 - Cat Jelly Press** | Hydraulic press for jelly cats. Hold to press up to 400 bar, cats flatten, crack and burst into material-specific debris. 7 materials, rare Gen objects (poop, watermelon, Chii, mini press, bomb), real collision and stacking. | [Open Lab 01](https://3dlabobo.dannyphan.me/labs/lab-01-cat-jelly-press/press.html) |
| **Lab 02 - Mecha Cat Teardown** | Procedural Three.js mecha cat driven by one solver (crank phase, trot gait, 2-bone IK legs). Take it apart subsystem by subsystem - head, energy core, chassis, tail, four legs - with live charts, X-Ray and exploded views, and a self-driving tour. 3 machine configs: Ceramic, Stealth, Hazard. | [Open Lab 02](https://3dlabobo.dannyphan.me/labs/lab-02-mecha-cat-teardown/) |
| **Lab 03 - Lightwater World** | Procedural WebGPU underwater world, forked from Noniv/abyssal-garden (MIT). Swim third-person as a gold fish with a glowing stripe, meet glowing jellyfish, an 8-segment mecha worm and new fish schools in bright aqua water. No engine, no model files. | [Open Lab 03](https://dankezo.github.io/lightwaterworld/) |
| **Lab 04 - Rental Cat POV** | 20-second cat-eye short film in C++ and Metal, raw fork of rockeymen/rental-cat-pov, unmodified: a cat bats a yarn ball, stalks a goldfish, then naps on the sofa. Mac-only. | [Open Lab 04](https://github.com/dankezo/rental-cat-pov) |
| **Lab 05 - Papertrails** | Endless papercraft pop-up world by Shikhar (@xikhar): flat paper tiles fold up ahead of you as you walk and fold flat behind. Built with Fable 5.2 and Opus 5.5, runs in the browser with three.js. MIT, reference only - not our repo. | [Open Lab 05](https://xikhar.github.io/papertrails/) |

Lab 01 source: [dankezo/cat-jelly](https://github.com/dankezo/cat-jelly). Lab 02 source: this repo. Lab 03 source: [dankezo/lightwaterworld](https://github.com/dankezo/lightwaterworld). Lab 04 source: [dankezo/rental-cat-pov](https://github.com/dankezo/rental-cat-pov) (raw fork). Lab 05 source: [xikhar/papertrails](https://github.com/xikhar/papertrails) (reference, MIT).

## ✨ Why it is fun

- **Real physics, not a video** - press, drag, throw, stack and break things with your own hands.
- **Take machines apart** - every subsystem detaches, with X-Ray and exploded views.
- **Live telemetry** - servo torque, foot lift, core temperature and power draw, charted in real time.
- **One HTML file per lab** - plain Three.js, no framework, no build step, nothing to install.
- **Phone first** - every lab fits one phone screen, touch controls included.

## 🚀 Run it locally

```bash
git clone https://github.com/dankezo/3Dlabobo.git
cd 3Dlabobo
python3 -m http.server 8000
# open http://localhost:8000
```

Or just open `index.html` in a browser. Any static host works, GitHub Pages included.

## 🧱 Add your own lab

Every lab ships with full documentation, a master prompt, and a required tools / CLI / skills list, so it can be reproduced exactly. See `labs/lab-02-mecha-cat-teardown/` for the pattern, and keep each lab on its own page - the hub only navigates, it never embeds a lab.

## 🗂 Repo map

```
3Dlabobo/
├── index.html                       # Hub - 5 redirect tiles, Lab 01 + Lab 02 + Lab 03 + Lab 04 + Lab 05
├── labs/
│   ├── lab-01-cat-jelly-press/      # Cat Jelly Press (press.html + README.md)
│   └── lab-02-mecha-cat-teardown/   # Mecha Cat Teardown (index.html + README.md + docs/)
├── WORKFLOW-lab2-mecha-cat-teardown.md  # 9-step build workflow for Lab 02
├── trials.html                      # Trial models (Dragon, Sandworm, Laser Gun, Mega Poro)
├── DESIGN.md                        # Hub design system
├── LICENSE
└── README.md
```

## 🛠 Tech

Three.js (inlined, no CDN) - vanilla JavaScript - single-file HTML - GitHub Pages.

## 📄 License

MIT - see [LICENSE](LICENSE). Made by [dankezo](https://github.com/dankezo).
