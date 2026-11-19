# Lab 01 - Cat Jelly Press

> Hydraulic press for jelly cats. Hold to press (400 bar default), flatten, crack and burst cats into material-specific debris. One HTML file, no build, no install.

**English** | [Tiếng Việt](#tiếng-việt)

[![Live](https://img.shields.io/badge/Live-Cat_Jelly_Press-brightgreen?style=flat-square)](https://3dlabobo.dannyphan.me/labs/lab-01-cat-jelly-press/press.html)
[![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](../../LICENSE)

## Live demo

**https://3dlabobo.dannyphan.me/labs/lab-01-cat-jelly-press/press.html**

Part of [3D Lab](https://3dlabobo.dannyphan.me/) (Lab 01). Open it and press. Works on desktop and phone.

## English

### What it is

Cat Jelly Press is a hydraulic press simulator for jelly cats. Press, drag, throw and stack cats with real collision and material physics. Each material cracks, breaks and scatters differently - by the cracking alone you can tell the materials apart, not just by colour.

### Specs

| Item | Value |
| --- | --- |
| Max press | 400 bar (default; slider 100-600 bar) |
| Materials | 7 - Glass, Iron, Diamond, Jelly, Brick, Water Ball, Toy Brick |
| Cats | Up to 12 at once, no shrinking, real collision and stacking |
| Rare Gen objects | 20% chance per Gen: poop, watermelon, Chiikawa-style creature, mini press, bomb - fixed size 1.4 |
| Cat HP | 16-segment ring at each cat's feet (no HP box) |
| File | One self-contained HTML file, 4,341,289 bytes (`press.html`; `index.html` is an identical copy) |

### Presses

| Press | Power | Note |
| --- | --- | --- |
| Base Press | Same | Default. Plain hydraulic press. |
| Fire Dragon | Same | Distinctive effect only. |
| Hell Press | Same | Distinctive effect only. |
| Angel Press | Same | Distinctive effect only. |

Special presses bring only a distinctive effect, never superior power.

### Controls

| Input | Action |
| --- | --- |
| Hold | Press down (must touch a cat before it counts) |
| Drag a cat | Move that cat |
| Drag empty space | Rotate the camera |
| Throw | Toss a cat onto the platen |
| Gen | Spawn a new cat (20% rare object) |
| Vacuum / trash bin | Clean debris (bin appears at 12+ debris pieces) |

### How to run

Open `press.html` in a browser (WebGL). Or serve the folder with any static server. No build step.

### Tech

Three.js (r128, CDN) - vanilla JavaScript - single-file HTML - GitHub Pages.

### Source

Game source: [dankezo/cat-jelly](https://github.com/dankezo/cat-jelly). This lab is an exact copy of the live Cat Jelly Press build (#47).

### Scope note

Press-only. No blender, no grinder, no roaming mecha cat - that direction was reversed on 2026-11-03 as too laggy. Cats stay put until pressed, dragged, thrown or reset.

## Tiếng Việt

### Mô tả

Cat Jelly Press là máy ép thủy lực cho mèo thạch. Ép, kéo, ném và xếp mèo với va chạm và vật lý vật liệu thật. Mỗi vật liệu nứt, vỡ và văng khác nhau - chỉ nhìn cách nứt vỡ đã phân biệt được vật liệu, không chỉ nhờ màu sắc.

### Thông số

| Hạng mục | Giá trị |
| --- | --- |
| Áp ép tối đa | 400 bar (mặc định; thanh trượt 100-600 bar) |
| Vật liệu | 7 loại - Thủy tinh, Sắt, Kim cương, Thạch, Gạch, Bóng nước, Gạch đồ chơi |
| Mèo | Tối đa 12 con cùng lúc, không thu nhỏ, va chạm và xếp chồng thật |
| Vật hiếm khi Gen | 20% mỗi lần Gen: phân, dưa hấu, sinh vật kiểu Chiikawa, máy ép mini, bom - cỡ cố định 1.4 |
| HP mèo | Vòng 16 đoạn dưới chân mỗi con mèo (không có hộp HP) |
| File | Một file HTML duy nhất, 4.341.289 byte (`press.html`; `index.html` là bản sao giống hệt) |

### Các máy ép

| Máy ép | Sức mạnh | Ghi chú |
| --- | --- | --- |
| Base Press | Như nhau | Mặc định. Máy ép thủy lực thường. |
| Fire Dragon | Như nhau | Chỉ khác hiệu ứng. |
| Hell Press | Như nhau | Chỉ khác hiệu ứng. |
| Angel Press | Như nhau | Chỉ khác hiệu ứng. |

Máy ép đặc biệt chỉ khác hiệu ứng, không mạnh hơn.

### Điều khiển

| Thao tác | Kết quả |
| --- | --- |
| Giữ | Ép xuống (phải chạm vào mèo mới tính) |
| Kéo một con mèo | Di chuyển con mèo đó |
| Kéo khoảng trống | Xoay camera |
| Ném | Ném mèo lên bàn ép |
| Gen | Sinh mèo mới (20% ra vật hiếm) |
| Hút bụi / thùng rác | Dọn mảnh vụn (thùng hiện khi có từ 12 mảnh trở lên) |

### Cách chạy

Mở `press.html` bằng trình duyệt (WebGL). Hoặc chạy thư mục này bằng bất kỳ static server nào. Không cần build.

### Công nghệ

Three.js (r128, CDN) - JavaScript thuần - một file HTML - GitHub Pages.

### Mã nguồn

Mã nguồn game: [dankezo/cat-jelly](https://github.com/dankezo/cat-jelly). Lab này là bản sao chính xác của bản Cat Jelly Press đang live (#47).

### Phạm vi

Chỉ ép. Không máy xay, không máy trộn, không mèo mecha đi lang thang - hướng đó đã bỏ ngày 2026-11-03 vì quá lag. Mèo đứng yên cho tới khi bị ép, kéo, ném hoặc reset.
