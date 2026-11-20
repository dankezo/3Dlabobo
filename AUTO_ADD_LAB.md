# Auto-Add Lab - quy trình thêm lab mới vào 3D Lab Hub

Khi Dũng gửi một link (repo GitHub, bài X, video, bài viết) và bảo nghiên cứu / thêm lab mới, làm theo quy trình này. Không bỏ bước. Không đoán.

## 1. Đọc kỹ cái được gửi

- Repo GitHub: đọc README, mô tả, license, ngôn ngữ, ngày tạo, stars/forks. Ghi lại: tên, làm gì, chạy trên nền tảng nào, license gì.
- Bài X / video / bài viết: đọc toàn bộ bài (dùng browser để đọc trang gốc, không đoán từ tiêu đề). Tìm repo được nhắc tới trong bài, nếu có, và đọc repo đó như bước trên. Ghi lại: ai đăng, nội dung, video/media gì, repo nào được nhắc tới.
- Nếu bài X không đọc được (X chặn, rate limit), nói rõ là chưa đọc được, không bịa nội dung.

## 2. Fork (chỉ khi là repo GitHub)

- Fork về tài khoản dankezo bằng GitHub connector (`fork_repository`).
- Nếu connector báo 403 (App không có quyền fork), dùng browser để fork qua giao diện GitHub web (vào trang repo, bấm Fork, xác nhận). Nếu browser cũng không làm được, bảo Dũng bấm Fork một cái trên GitHub (một click), rồi tiếp tục.
- Không sửa gì trong repo vừa fork. Tag là `raw fork` (chưa modify gì).
- Ghi lại URL fork: `https://github.com/dankezo/<tên-repo>`.

## 3. Thêm tile vào hub

- File: `~/workspace/3dlabobo/index.html` (hub), push qua snapshot-push flow như các lab khác.
- Đánh số lab tiếp theo (Lab 04, 05, ...), cập nhật:
  - Stat `03` -> số lab mới (ví dụ `05`).
  - Dòng `3 LABS // MỞ TAB MỚI` -> số lab mới.
  - Footer `3DLABOBO // 3 LABS` -> số lab mới.
- Tile mới theo đúng cấu trúc tile cũ (`.tile`, `.tile-art`, `.tile-body`, `.tile-tags`, `.tile-url`, `.tile-cta`):
  - `.tile-art`: nếu chưa có video, bỏ `<video>`, chỉ giữ `.tile-veil`, `.tile-num` (LAB / 04), `.tile-giant` (04), `<b>` (tên ngắn, ví dụ `CAT POV`), `.spec` (mô tả ngắn). Nền panel tự hiện, không cần video.
  - Không dùng pill LIVE cho lab raw fork (chưa chạy live). Chỉ dùng LIVE khi lab đã chạy được trên trang riêng.
  - `.tile-body`: `h3` tên lab + `small` tên tiếng Việt, `p` mô tả 1-2 câu (lấy từ README / bài gốc, không bịa), `.tile-tags` gồm ngôn ngữ/nền tảng + `Raw fork`, `.tile-url` là URL fork hoặc URL bài gốc, `.tile-cta` giữ nguyên mẫu.
  - Link tile tới fork (repo) hoặc tới bài gốc (X/video), mở tab mới.
- Ngôn ngữ: tiêu đề và mô tả song ngữ VI/EN như các tile cũ. Dấu gạch ngang ngắn (-) thôi, không dùng gạch dài.

## 4. Kiểm tra và đẩy

- Kiểm tra: số lab khớp ở stat, dòng tiêu đề, footer; không còn `3 LABS` sót lại; link tile mở được; không có gạch dài.
- Push hub qua snapshot-push flow (manifest NUL-delimited, kiểm tra head trước khi push, cập nhật sync record).
- Đợi Pages deploy rồi kiểm tra live bằng hash (curl + sha256sum), xác nhận số lab và tile mới hiện trên trang live.
- Báo Dũng: lab mới tên gì, số mấy, link đâu, fork xong chưa, cái gì chưa xác minh được.

## 5. Ghi nhớ

- Cập nhật `~/MEMORY.md`, `~/workspace/goals/lightwater-world/GOAL.md` (hoặc goal của 3D Lab nếu có), và `~/memory/YYYY-MM-DD.md` với: tên lab, số lab, URL fork/bài gốc, tag (raw fork), ngày thêm.
- Nếu lab là fork, ghi rõ license và nguồn gốc (fork từ ai, repo gốc nào).
- Không tự ý sửa code trong repo fork khi tag là raw fork. Muốn sửa thì hỏi Dũng trước và đổi tag.
