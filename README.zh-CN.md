# 🔬 3D Lab

> 可拆解的交互式 3D 机器模拟实验室。真实物理、真实拆解、零构建步骤。

[English](README.md) | [Tiếng Việt](README.vi.md) | **中文** | [Español](README.es.md) | [Русский](README.ru.md)

[![Live](https://img.shields.io/badge/Live-3D_Lab-brightgreen?style=flat-square)](https://dankezo.github.io/3Dlabobo/)
[![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/dankezo/3Dlabobo?style=flat-square)](https://github.com/dankezo/3Dlabobo/stargazers)

## 🌐 在线演示

**https://dankezo.github.io/3Dlabobo/**

打开并选择一个实验室。无需安装、无需构建、无需账号。桌面和手机都可以使用。

## 🧪 实验室

| 实验室 | 内容 | 试一试 |
| --- | --- | --- |
| **Lab 01 - 果冻猫液压机** | 果冻猫液压机。按住加压至 400 bar,果冻猫被压扁、开裂,最后碎成与材质对应的碎片。7 种材质,Gen 稀有物品(便便、西瓜、Chii、迷你液压机、炸弹),真实碰撞与堆叠。 | [打开 Lab 01](https://dankezo.github.io/3Dlabobo/labs/lab-01-cat-jelly-press/press.html) |
| **Lab 02 - 机甲猫拆解** | 程序化 Three.js 机甲猫,由单一求解器驱动(曲柄相位、小跑步态、双骨骼 IK 腿)。可逐个子系统拆解 - 头部、能量核心、底盘、尾巴、四条腿 - 附实时图表、X 光与爆炸视图,以及自动导览。3 种机型配置:Ceramic、Stealth、Hazard。 | [打开 Lab 02](https://dankezo.github.io/3Dlabobo/labs/lab-02-mecha-cat-teardown/) |

Lab 01 源码:[dankezo/cat-jelly](https://github.com/dankezo/cat-jelly)。Lab 02 源码:本仓库。

## ✨ 亮点

- **真实物理,不是视频** - 亲手按压、拖拽、投掷、堆叠、打碎一切。
- **拆开机器看** - 每个子系统都可拆下,带 X 光与爆炸视图。
- **实时遥测** - 舵机扭矩、抬脚高度、核心温度与功耗,实时绘图。
- **每个实验室一个 HTML 文件** - 纯 Three.js,无框架、无构建步骤、无需安装。
- **手机优先** - 每个实验室刚好占满一个手机屏幕,支持触屏操作。

## 🚀 本地运行

```bash
git clone https://github.com/dankezo/3Dlabobo.git
cd 3Dlabobo
python3 -m http.server 8000
# 打开 http://localhost:8000
```

也可以直接用浏览器打开 `index.html`。任何静态托管都可用,包括 GitHub Pages。

## 🧱 添加你自己的实验室

每个实验室都附有完整文档、主提示词以及所需的工具 / CLI / 技能清单,可以一步不差地复现。参考 `labs/lab-02-mecha-cat-teardown/` 的结构,每个实验室保持独立页面 - 首页只做导航,绝不内嵌实验室。

## 🗂 仓库结构

```
3Dlabobo/
├── index.html                       # 首页 - 2 个跳转卡片,Lab 01 + Lab 02
├── labs/
│   ├── lab-01-cat-jelly-press/      # 果冻猫液压机 (index.html + press.html)
│   └── lab-02-mecha-cat-teardown/   # 机甲猫拆解
├── trials.html                      # 试验模型 (龙、沙虫、激光枪、Mega Poro)
├── LICENSE
└── README.md
```

## 🛠 技术

Three.js (r128, CDN) - 原生 JavaScript - 单文件 HTML - GitHub Pages。

## 📄 许可证

MIT - 见 [LICENSE](LICENSE)。作者 [dankezo](https://github.com/dankezo)。
