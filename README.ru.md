# 🔬 3D Lab

> Интерактивные 3D-симуляторы машин, которые можно разобрать. Настоящая физика, настоящая разборка, ноль шагов сборки.

[English](README.md) | [Tiếng Việt](README.vi.md) | [中文](README.zh-CN.md) | [Español](README.es.md) | **Русский**

[![Live](https://img.shields.io/badge/Live-3D_Lab-brightgreen?style=flat-square)](https://dankezo.github.io/3Dlabobo/)
[![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/dankezo/3Dlabobo?style=flat-square)](https://github.com/dankezo/3Dlabobo/stargazers)

## 🌐 Живое демо

**https://dankezo.github.io/3Dlabobo/**

Откройте и выберите лабораторию. Без установки, без сборки, без аккаунта. Работает на компьютере и на телефоне.

## 🧪 Лаборатории

| Лаборатория | Что это | Попробовать |
| --- | --- | --- |
| **Lab 01 - Пресс для желейных котов** | Гидравлический пресс для желейных котов. Удерживайте нажатие до 400 бар: коты сплющиваются, трескаются и разлетаются на осколки, свои для каждого материала. 7 материалов, редкие объекты Gen (какашка, арбуз, Chii, мини-пресс, бомба), настоящие столкновения и складывание. | [Открыть Lab 01](https://dankezo.github.io/3Dlabobo/labs/lab-01-cat-jelly-press/press.html) |
| **Lab 02 - Разборка меха-кота** | Процедурный меха-кот на Three.js, управляемый одним решателем (фаза коленвала, рысь, ноги с IK из 2 костей). Разбирайте его по подсистемам - голова, энергоядро, шасси, хвост, четыре ноги - с живыми графиками, рентгеном, видом в разборе и автотуром. 3 конфигурации: Ceramic, Stealth, Hazard. | [Открыть Lab 02](https://dankezo.github.io/3Dlabobo/labs/lab-02-mecha-cat-teardown/) |

Исходник Lab 01: [dankezo/cat-jelly](https://github.com/dankezo/cat-jelly). Исходник Lab 02: этот репозиторий.

## ✨ Почему это интересно

- **Настоящая физика, а не видео** - давите, таскайте, бросайте, складывайте и ломайте своими руками.
- **Разбирайте машины** - каждая подсистема снимается, есть рентген и вид в разборе.
- **Живая телеметрия** - момент сервопривода, подъём лапы, температура ядра и мощность, графики в реальном времени.
- **Один HTML-файл на лабораторию** - чистый Three.js, без фреймворков, без сборки, ничего устанавливать не нужно.
- **Сначала телефон** - каждая лаборатория помещается на один экран телефона, с сенсорным управлением.

## 🚀 Запуск локально

```bash
git clone https://github.com/dankezo/3Dlabobo.git
cd 3Dlabobo
python3 -m http.server 8000
# откройте http://localhost:8000
```

Или просто откройте `index.html` в браузере. Подойдёт любой статический хостинг, включая GitHub Pages.

## 🧱 Добавьте свою лабораторию

Каждая лаборатория идёт с полной документацией, мастер-промптом и списком нужных инструментов / CLI / навыков, чтобы её можно было воспроизвести в точности. Смотрите образец в `labs/lab-02-mecha-cat-teardown/` и держите каждую лабораторию на отдельной странице - хаб только навигирует, он никогда не встраивает лабораторию.

## 🗂 Карта репозитория

```
3Dlabobo/
├── index.html                       # Хаб - 2 карточки-перехода, Lab 01 + Lab 02
├── labs/
│   ├── lab-01-cat-jelly-press/      # Пресс для желейных котов (index.html + press.html)
│   └── lab-02-mecha-cat-teardown/   # Разборка меха-кота
├── trials.html                      # Пробные модели (Дракон, Песчаный червь, Лазерная пушка, Мега Поро)
├── LICENSE
└── README.md
```

## 🛠 Технологии

Three.js (r128, CDN) - чистый JavaScript - один HTML-файл - GitHub Pages.

## 📄 Лицензия

MIT - см. [LICENSE](LICENSE). Автор: [dankezo](https://github.com/dankezo).
