# 🔬 3D Lab

> Interactive 3D machine simulators you can take apart. Real physics, real teardown, zero build step.

**English** | [Tiếng Việt](README.vi.md) | [中文](README.zh-CN.md) | [Español](README.es.md) | [Русский](README.ru.md)

[![Live](https://img.shields.io/badge/Live-3D_Lab-brightgreen?style=flat-square)](https://dankezo.github.io/3Dlabobo/)
[![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/dankezo/3Dlabobo?style=flat-square)](https://github.com/dankezo/3Dlabobo/stargazers)

## 🌐 Live demo

**https://dankezo.github.io/3Dlabobo/**

Open it and pick a lab. No install, no build, no account. Works on desktop and phone.

## 🧪 Labs

| Lab | What it is | Try it |
| --- | --- | --- |
| **Lab 01 - Cat Jelly Press** | Hydraulic press for jelly cats. Hold to press up to 400 bar, cats flatten, crack and burst into material-specific debris. 7 materials, rare Gen objects (poop, watermelon, Chii, mini press, bomb), real collision and stacking. | [Open Lab 01](https://dankezo.github.io/3Dlabobo/labs/lab-01-cat-jelly-press/press.html) |
| **Lab 02 - Mecha Cat Teardown** | Procedural Three.js mecha cat driven by one solver (crank phase, trot gait, 2-bone IK legs). Take it apart subsystem by subsystem - head, energy core, chassis, tail, four legs - with live charts, X-Ray and exploded views, and a self-driving tour. 3 machine configs: Ceramic, Stealth, Hazard. | [Open Lab 02](https://dankezo.github.io/3Dlabobo/labs/lab-02-mecha-cat-teardown/) |

Lab 01 source: [dankezo/cat-jelly](https://github.com/dankezo/cat-jelly). Lab 02 source: this repo.

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
├── index.html                       # Hub - 2 redirect tiles, Lab 01 + Lab 02
├── labs/
│   ├── lab-01-cat-jelly-press/      # Cat Jelly Press (index.html + press.html)
│   └── lab-02-mecha-cat-teardown/   # Mecha Cat Teardown
├── trials.html                      # Trial models (Dragon, Sandworm, Laser Gun, Mega Poro)
├── LICENSE
└── README.md
```

## 🛠 Tech

Three.js (r128, CDN) - vanilla JavaScript - single-file HTML - GitHub Pages.

## 📄 License

MIT - see [LICENSE](LICENSE). Made by [dankezo](https://github.com/dankezo).
