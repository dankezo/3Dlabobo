# 🔬 3D Lab

> Simuladores 3D interactivos de máquinas que puedes desarmar. Física real, desarme real, cero pasos de compilación.

[English](README.md) | [Tiếng Việt](README.vi.md) | [中文](README.zh-CN.md) | **Español** | [Русский](README.ru.md)

[![Live](https://img.shields.io/badge/Live-3D_Lab-brightgreen?style=flat-square)](https://dankezo.github.io/3Dlabobo/)
[![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/dankezo/3Dlabobo?style=flat-square)](https://github.com/dankezo/3Dlabobo/stargazers)

## 🌐 Demo en vivo

**https://dankezo.github.io/3Dlabobo/**

Ábrelo y elige un laboratorio. Sin instalación, sin compilación, sin cuenta. Funciona en escritorio y en teléfono.

## 🧪 Laboratorios

| Lab | Qué es | Probar |
| --- | --- | --- |
| **Lab 01 - Prensa de gatos de gelatina** | Prensa hidráulica para gatos de gelatina. Mantén presionado hasta 400 bar, los gatos se aplastan, se agrietan y estallan en fragmentos propios de cada material. 7 materiales, objetos raros de Gen (caca, sandía, Chii, mini prensa, bomba), colisiones y apilado reales. | [Abrir Lab 01](https://dankezo.github.io/3Dlabobo/labs/lab-01-cat-jelly-press/press.html) |
| **Lab 02 - Desarme del gato mecha** | Gato mecha procedural en Three.js, movido por un solo solucionador (fase de cigüeñal, trote, piernas IK de 2 huesos). Desármalo subsistema por subsistema - cabeza, núcleo de energía, chasis, cola, cuatro patas - con gráficos en vivo, vista de rayos X y vista explotada, y un tour automático. 3 configuraciones: Ceramic, Stealth, Hazard. | [Abrir Lab 02](https://dankezo.github.io/3Dlabobo/labs/lab-02-mecha-cat-teardown/) |

Código de Lab 01: [dankezo/cat-jelly](https://github.com/dankezo/cat-jelly). Código de Lab 02: este repositorio.

## ✨ Por qué es divertido

- **Física real, no un video** - prensa, arrastra, lanza, apila y rompe cosas con tus propias manos.
- **Desarma las máquinas** - cada subsistema se separa, con rayos X y vista explotada.
- **Telemetría en vivo** - par del servo, elevación del pie, temperatura del núcleo y consumo, graficados en tiempo real.
- **Un archivo HTML por laboratorio** - Three.js puro, sin framework, sin compilación, nada que instalar.
- **Primero el teléfono** - cada laboratorio cabe en una sola pantalla de teléfono, con controles táctiles.

## 🚀 Ejecutarlo en local

```bash
git clone https://github.com/dankezo/3Dlabobo.git
cd 3Dlabobo
python3 -m http.server 8000
# abre http://localhost:8000
```

O simplemente abre `index.html` en el navegador. Cualquier hosting estático sirve, GitHub Pages incluido.

## 🧱 Añade tu propio laboratorio

Cada laboratorio trae documentación completa, un prompt maestro y la lista de herramientas / CLI / skills necesarias, para reproducirlo con exactitud. Mira el patrón en `labs/lab-02-mecha-cat-teardown/`, y mantén cada laboratorio en su propia página - el hub solo navega, nunca incrusta un laboratorio.

## 🗂 Mapa del repo

```
3Dlabobo/
├── index.html                       # Hub - 2 tarjetas de redirección, Lab 01 + Lab 02
├── labs/
│   ├── lab-01-cat-jelly-press/      # Prensa de gatos de gelatina (index.html + press.html)
│   └── lab-02-mecha-cat-teardown/   # Desarme del gato mecha
├── trials.html                      # Modelos de prueba (Dragón, Gusano de arena, Pistola láser, Mega Poro)
├── LICENSE
└── README.md
```

## 🛠 Tecnología

Three.js (r128, CDN) - JavaScript puro - HTML de un solo archivo - GitHub Pages.

## 📄 Licencia

MIT - ver [LICENSE](LICENSE). Hecho por [dankezo](https://github.com/dankezo).
