# 🔬 3D Lab

> Phòng lab mô phỏng máy 3D tương tác, tháo rời được từng bộ phận. Vật lý thật, tháo máy thật, không cần build.

[English](README.md) | **Tiếng Việt** | [中文](README.zh-CN.md) | [Español](README.es.md) | [Русский](README.ru.md)

[![Live](https://img.shields.io/badge/Live-3D_Lab-brightgreen?style=flat-square)](https://dankezo.github.io/3Dlabobo/)
[![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/dankezo/3Dlabobo?style=flat-square)](https://github.com/dankezo/3Dlabobo/stargazers)

## 🌐 Xem trực tiếp

**https://dankezo.github.io/3Dlabobo/**

Mở lên và chọn một lab. Không cần cài đặt, không cần build, không cần tài khoản. Chạy tốt trên cả máy tính và điện thoại.

## 🧪 Các lab

| Lab | Nội dung | Chơi thử |
| --- | --- | --- |
| **Lab 01 - Máy ép mèo thạch** | Máy ép thủy lực ép mèo thạch. Giữ để ép tới 400 bar, mèo bẹp dần, nứt rồi vỡ thành mảnh vụn riêng theo từng vật liệu. 7 vật liệu, vật phẩm hiếm khi Gen (phân, dưa hấu, Chii, máy ép mini, bom), va chạm và xếp chồng thật. | [Mở Lab 01](https://dankezo.github.io/3Dlabobo/labs/lab-01-cat-jelly-press/press.html) |
| **Lab 02 - Tháo rời mèo mecha** | Mèo mecha 3D dựng bằng Three.js, chạy bằng một solver duy nhất (pha trục khuỷu, dáng đi trot, chân IK 2 khớp). Tháo rời từng hệ thống - đầu, lõi năng lượng, khung gầm, đuôi, bốn chân - kèm biểu đồ trực tiếp, chế độ X-Ray, xem tách rời và tour tự chạy. 3 cấu hình máy: Ceramic, Stealth, Hazard. | [Mở Lab 02](https://dankezo.github.io/3Dlabobo/labs/lab-02-mecha-cat-teardown/) |

Mã nguồn Lab 01: [dankezo/cat-jelly](https://github.com/dankezo/cat-jelly). Mã nguồn Lab 02: repo này.

## ✨ Điểm hay

- **Vật lý thật, không phải video** - tự tay ép, kéo, ném, xếp chồng và làm vỡ mọi thứ.
- **Tháo máy ra xem** - từng bộ phận đều tháo rời được, có X-Ray và chế độ xem tách rời.
- **Số liệu trực tiếp** - mô-men servo, độ nhấc chân, nhiệt độ lõi và công suất, vẽ biểu đồ theo thời gian thực.
- **Mỗi lab một file HTML** - Three.js thuần, không framework, không bước build, không gì phải cài.
- **Ưu tiên điện thoại** - lab nào cũng vừa đúng một màn hình điện thoại, điều khiển cảm ứng đầy đủ.

## 🚀 Chạy trên máy của bạn

```bash
git clone https://github.com/dankezo/3Dlabobo.git
cd 3Dlabobo
python3 -m http.server 8000
# mở http://localhost:8000
```

Hoặc mở thẳng file `index.html` bằng trình duyệt. Host tĩnh nào cũng chạy được, GitHub Pages cũng vậy.

## 🧱 Thêm lab của riêng bạn

Mỗi lab đều có tài liệu đầy đủ, master prompt và danh sách công cụ / CLI / skill cần thiết, để tái tạo chính xác từng bước. Xem mẫu ở `labs/lab-02-mecha-cat-teardown/`, và giữ mỗi lab một trang riêng - trang hub chỉ điều hướng, không nhúng lab vào trong.

## 🗂 Sơ đồ repo

```
3Dlabobo/
├── index.html                       # Hub - 2 ô redirect, Lab 01 + Lab 02
├── labs/
│   ├── lab-01-cat-jelly-press/      # Máy ép mèo thạch (index.html + press.html)
│   └── lab-02-mecha-cat-teardown/   # Tháo rời mèo mecha
├── trials.html                      # Model thử nghiệm (Rồng, Sâu cát, Súng laser, Mega Poro)
├── LICENSE
└── README.md
```

## 🛠 Công nghệ

Three.js (r128, CDN) - JavaScript thuần - file HTML đơn - GitHub Pages.

## 📄 Giấy phép

MIT - xem [LICENSE](LICENSE). Làm bởi [dankezo](https://github.com/dankezo).
