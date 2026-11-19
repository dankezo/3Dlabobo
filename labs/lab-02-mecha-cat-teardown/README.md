# Lab 02 - Mecha Cat Teardown

> Take apart a procedural 3D mecha cat, subsystem by subsystem. One solver drives everything: crank phase, trot gait, 2-bone IK legs. Rev 3.8.

**English** | [Tiếng Việt](#tiếng-việt)

[![Live](https://img.shields.io/badge/Live-Mecha_Cat_Teardown-brightgreen?style=flat-square)](https://3dlabobo.dannyphan.me/labs/lab-02-mecha-cat-teardown/)
[![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](../../LICENSE)

## Live demo

**https://3dlabobo.dannyphan.me/labs/lab-02-mecha-cat-teardown/**

Part of [3D Lab](https://3dlabobo.dannyphan.me/) (Lab 02). Open it and take the cat apart. Works on desktop and phone.

## English

### What it is

Mecha Cat Teardown is a 3D teardown simulator for a procedural mecha cat. Tap any subsystem to detach it in an exploded move while the rest steps aside, fade the armour with X-Ray to reveal the frame and core, and watch four live charts (servo torque, foot lift, core temperature, power draw) while the machine walks. The head is an angular wedge prism with zero SphereGeometry - no round or blob heads, ever.

### Models

| Model | Config | Notes |
| --- | --- | --- |
| Cat - Ceramic | 55 RPM | Standard, assembled |
| Cat - Stealth | 85 RPM | Dark shell, X-Ray on |
| Cat - Hazard | 35 RPM | 130% stress, 35% exploded view |
| Worm WORM-09 | - | Built-in worm model |
| Gun SL-01 | - | Super Laser Gun |
| Load | - | Load a machine from a JSON config (`name`, `rpm`, `stress`, `explode`, `xray`) |

### Controls

| Input | Action |
| --- | --- |
| Tap a part | Detach that subsystem |
| Tap empty stage / outside the cat | Reassemble |
| Model row | Scroll to switch Cat / Worm / Gun and variants (Load pinned at the end) |
| X-Ray | Fade the armour to reveal frame and core |
| Replay | Restart the self-driving tour (it also starts automatically 700 ms after load, unless reduced motion) |
| Drag / scroll | Orbit / zoom |

### Specs

| Item | Value |
| --- | --- |
| Revision | Rev 3.8 |
| File | One self-contained HTML file, 1,292,612 bytes (ship limit 2 MB) |
| Head | Angular wedge prism, zero SphereGeometry |
| Solver | 1 crank / servo phase, 0-120 RPM, trot gait, 2-bone IK legs |
| Charts | Live servo torque, foot lift, core temperature, power draw |
| Stress | Red OVER-LIMIT flag above 135% (stress-test state, not an error; the tour demos it at 150%) |
| Phone | One viewport (100svh), no scroll |

### How to run

Open `index.html` in a browser (WebGL). Or serve the folder with any static server. No build step.

### Tech

Three.js (r128, CDN) - vanilla JavaScript - single-file HTML - GitHub Pages.

### Reproduce it

- `docs/` holds the original build record (Nov 2026, Rev 2-3 era): README, MASTER_PROMPT, TOOLS, tour script. It describes the build as it was then; current Rev 3.8 behaviour is described above.
- `../../WORKFLOW-lab2-mecha-cat-teardown.md` is the 9-step workflow that built this lab from Elvar's teardown post ([How I Turn Any Machine Into a 3D Simulator You Can Take Apart](https://x.com/elvar_official/status/2116174609355571402)).
- Method reference: [teardown skill](https://github.com/elvarofficial/teardown) (free, MIT) - read as the method reference only, do not copy its shipped machines.

### Scope note

NOT the mecha robot cat inside Cat Jelly Press. That direction was reversed on 2026-11-03 as too laggy and stays reversed. Cat Jelly Press stays press-only; the mecha cat lives only as its own lab.

## Tiếng Việt

### Mô tả

Mecha Cat Teardown là máy mô phỏng tháo rời mèo mecha 3D. Bấm vào từng bộ phận để tháo rời, bật X-Ray để nhìn khung và lõi bên trong, xem 4 biểu đồ trực tiếp (mô-men servo, độ nâng chân, nhiệt độ lõi, công suất tiêu thụ) trong lúc máy bước đi. Đầu mèo là lăng kính nêm góc cạnh, không dùng SphereGeometry - không bao giờ đầu tròn hay blob.

### Các model

| Model | Cấu hình | Ghi chú |
| --- | --- | --- |
| Mèo - Ceramic | 55 RPM | Chuẩn, lắp ráp đầy đủ |
| Mèo - Stealth | 85 RPM | Vỏ tối, bật X-Ray |
| Mèo - Hazard | 35 RPM | 130% tải, tách 35% |
| Sâu WORM-09 | - | Model sâu có sẵn |
| Súng SL-01 | - | Súng Laser Siêu cấp |
| Load | - | Nạp máy từ file JSON (`name`, `rpm`, `stress`, `explode`, `xray`) |

### Điều khiển

| Thao tác | Kết quả |
| --- | --- |
| Bấm vào một bộ phận | Tháo rời bộ phận đó |
| Bấm vào sân trống / ngoài con mèo | Lắp ráp lại |
| Hàng Model | Cuộn để đổi Mèo / Sâu / Súng và các biến thể (Load nằm cuối) |
| X-Ray | Làm mờ vỏ giáp để lộ khung và lõi |
| Replay | Chạy lại tour tự động (tour cũng tự chạy 700 ms sau khi tải trang, trừ khi bật giảm chuyển động) |
| Kéo / cuộn | Xoay / zoom camera |

### Thông số

| Hạng mục | Giá trị |
| --- | --- |
| Bản hiện tại | Rev 3.8 |
| File | Một file HTML duy nhất, 1.292.612 byte (giới hạn 2 MB) |
| Đầu | Lăng kính nêm góc cạnh, không dùng SphereGeometry |
| Bộ giải | 1 trục / pha servo, 0-120 RPM, dáng đi trot, chân IK 2 khớp |
| Biểu đồ | Mô-men servo, độ nâng chân, nhiệt độ lõi, công suất - trực tiếp |
| Tải | Cờ đỏ OVER-LIMIT khi trên 135% (trạng thái test tải, không phải lỗi; tour demo ở 150%) |
| Điện thoại | Một màn hình (100svh), không cuộn |

### Cách chạy

Mở `index.html` bằng trình duyệt (WebGL). Hoặc chạy thư mục này bằng bất kỳ static server nào. Không cần build.

### Công nghệ

Three.js (r128, CDN) - JavaScript thuần - một file HTML - GitHub Pages.

### Tái hiện lại

- `docs/` là hồ sơ build gốc (tháng 11/2026, thời Rev 2-3): README, MASTER_PROMPT, TOOLS, kịch bản tour. Nó mô tả bản build lúc đó; hành vi Rev 3.8 hiện tại được mô tả ở trên.
- `../../WORKFLOW-lab2-mecha-cat-teardown.md` là quy trình 9 bước đã dựng lab này từ bài teardown của Elvar ([How I Turn Any Machine Into a 3D Simulator You Can Take Apart](https://x.com/elvar_official/status/2116174609355571402)).
- Tham khảo phương pháp: [teardown skill](https://github.com/elvarofficial/teardown) (miễn phí, MIT) - chỉ đọc để học phương pháp, không sao chép máy mẫu của họ.

### Phạm vi

KHÔNG phải mèo robot mecha trong Cat Jelly Press. Hướng đó đã bỏ ngày 2026-11-03 vì quá lag và vẫn bỏ. Cat Jelly Press chỉ ép; mèo mecha chỉ sống trong lab riêng của nó.
