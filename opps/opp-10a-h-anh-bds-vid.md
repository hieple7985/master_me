# Opp 10A — Hoang Anh — Automation Video BĐS (VN/Hải Phòng)

- Tài liệu đối tác: https://docs.google.com/document/d/1fp13d8RmQLjbN4E5kiqXZ3r73sUhd6J_1ypopymhuos/edit?tab=t.0

## Phản hồi gửi đối tác (vendor-style)

Chào anh/chị, bên em đã đọc tài liệu mô tả “Real Estate Video Automation / Core Engine”. Đánh giá nhanh: ý tưởng khả thi tại thị trường VN (bao gồm Hải Phòng) nếu triển khai theo hướng MVP “semi-auto” trước để đảm bảo tốc độ ra hàng, kiểm soát chất lượng brand và tránh các rủi ro API/bản quyền.

Bên em đề xuất lộ trình như sau.

## 1) Độ khả thi tại VN/Hải Phòng

- MVP làm được: Sale gửi ảnh + thông số lô đất qua Zalo → hệ thống tạo kịch bản + giọng đọc + dựng video theo template brand → trả video + link duyệt trên web mobile.
- “Core Engine” trong thực tế là pipeline điều phối job (hàng đợi, SLA, retry), quản trị template/brand, QA chất lượng và nhật ký vận hành. Không cần “viện” để ra MVP, nhưng cần thiết kế đúng quy trình + governance.
- Mốc “120 giây” có thể tiệm cận nếu template ổn định, input chuẩn hóa, render tối ưu và hạ tầng scale. Với MVP rẻ nhất, nên cam kết SLA thực tế hơn để tránh oversell.

## 2) Chuẩn video ngành BĐS VN (đề xuất)

- Chuẩn mặc định: 9:16, 1080×1920, 30fps, MP4 H.264, thời lượng 45 giây.
- Nhịp nội dung: 6–10 cảnh/slide, caption lớn dễ đọc, CTA rõ ràng (gọi/Zalo/đăng ký xem).
- Biến thể ngay trong MVP:
  - “Nguồn ngộp / cần chốt nhanh”: 25–30 giây
  - “Dự án/nhà phố (nhiều thông tin)”: 55–60 giây

## 3) Quy tắc pháp lý/tuân thủ hiển thị (tối thiểu để an toàn)

- Luôn có footer disclaimer (1–2 dòng):
  - “Thông tin mang tính tham khảo. Giá/hiện trạng có thể thay đổi.”
  - “Pháp lý: … (Sổ đỏ/đang chờ/…); Vui lòng kiểm tra hồ sơ trước giao dịch.”
- Hạn chế các claim “cam kết lợi nhuận”, “chắc chắn ra sổ”, “bao vay 100%”… nếu không có căn cứ/giấy tờ.
- Watermark brand + mã lô/tên dự án bắt buộc để giảm rủi ro bị reup và thuận tiện truy vết nguồn.

## 4) Nhạc/chi phí tiết kiệm (phù hợp bối cảnh VN)

- MVP tiết kiệm và sạch bản quyền nhất: dùng thư viện nhạc commercial-free (mua pack) hoặc nhạc có license sẵn.
- Nhạc “trend” TikTok/Reels thường vướng bản quyền/API. Giai đoạn 1 khuyến nghị: hệ thống gợi ý vibe/tempo, sale chọn thủ công khi đăng.

## 5) SLA/Throughput đề xuất cho pilot

- Thiết kế MVP cho quy mô: 20–80 sale, peak tối/cuối tuần.
- Mục tiêu pilot hợp lý: 100–300 video/ngày (tùy nguồn hàng và tần suất đăng).
- SLA đề xuất để ký:
  - Pilot: median 3–5 phút/video, p95 < 10 phút
  - Sau tối ưu + scale: median 90–180 giây, p95 < 5 phút

## 6) Quy trình vận hành MVP (Semi-auto)

1. Sale gửi input qua Zalo theo format chuẩn.
2. Hệ thống tạo nháp video + caption + hashtag.
3. Duyệt tay trên web mobile (approve/reject, chỉnh sửa nhanh text/giọng/template nếu cần).
4. Xuất file + metadata theo từng nền tảng, hỗ trợ lịch đăng; thao tác đăng có thể giữ “human-in-the-loop” để phù hợp hạn chế API.

## 7) Báo cáo (đủ ý nghĩa cho người dùng cuối)

- Leader/Chủ sàn: số video/ngày theo team, tỉ lệ đúng guideline, thời gian xử lý (SLA), top template/giọng, lỗi thường gặp.
- Sale: lịch sử job, link tải/duyệt, thời gian xử lý, template/giọng đã dùng, cảnh báo input thiếu/ảnh mờ.
- Quyền truy cập: Sale thấy của mình; Leader thấy team; Admin thấy toàn hệ thống + cấu hình brand.

## 8) Google AI Studio / Gemini có làm được không?

- AI Studio/Gemini phù hợp làm LLM cho copywriting và thử nghiệm prompt nhanh.
- Tuy nhiên AI Studio không phải hệ thống production end-to-end. Để chạy thật cần build pipeline quanh Gemini API: Zalo ingest + hàng đợi job + TTS + render + web duyệt + log/SLA.
- Nếu chọn stack Google: Gemini API (kịch bản/caption), Google Cloud Text-to-Speech (giọng Việt), chạy pipeline trên Cloud Run/VM, lưu trữ video trên object storage và phát link duyệt.

## 9) Đề xuất phạm vi MVP rẻ nhất (để ra hàng nhanh)

Bao gồm:
- Zalo ingest (chuẩn hóa format input + validation)
- 2–3 template brand (intro/outro/logo/color/font/watermark)
- 2–4 giọng tiếng Việt (ưu tiên giọng sale dễ nghe, chọn theo vùng miền theo ngữ cảnh)
- Auto subtitle + caption + hashtag
- Web mobile duyệt/tải + log trạng thái job
- Báo cáo cơ bản + phân quyền

Chưa bao gồm (giai đoạn sau):
- Auto-post 100% lên mọi nền tảng (do hạn chế API/bản quyền)
- Fine-tune voice riêng theo thương hiệu (nếu cần sẽ làm sau)
- “Trend music” tự động lấy từ nền tảng

## 10) Báo giá MVP (tham chiếu thị trường Hải Phòng/VN)

Mô hình tính phí đề xuất: 1 lần triển khai (one-time) + phí vận hành theo tháng (monthly) vì có chi phí biến đổi AI/TTS/render.

### Gói MVP Pilot (khuyến nghị để triển khai đúng và không “oversell”)

- One-time: 80–120 triệu VNĐ
- Monthly: 12–25 triệu VNĐ/tháng
- Quota hợp lý: 3.000–8.000 video/tháng (vượt quota tính thêm theo video)
- SLA: median 3–5 phút, p95 < 10 phút (giai đoạn pilot)

### Gói “Rẻ nhất để chốt nhanh” (đổi lại scope tối giản)

- One-time: 60–80 triệu VNĐ
- Monthly: 8–15 triệu VNĐ/tháng
- Giới hạn: 1 template, 1–2 giọng, báo cáo tối giản, SLA không cam kết 120 giây

## 11) Thông tin cần xác nhận để chốt scope trong ngày

- Format input Zalo: trường bắt buộc (giá/DT/pháp lý/vị trí/ưu điểm/CTA) và số ảnh tối đa.
- Brand kit: logo, màu, font, watermark, intro/outro (nếu chưa có, bên em dựng theo mẫu).
- Bộ “từ cấm/từ nhạy cảm” (claim pháp lý/lợi nhuận) và disclaimer chuẩn của sàn.
- Quota dự kiến/tháng và peak/ngày (để tư vấn cấu hình cloud tại VN).

Nếu anh/chị đồng ý theo MVP pilot ở trên, bên em có thể gửi SOW (Statement of Work) + timeline triển khai 3–4 tuần và demo sớm sau 7–10 ngày làm việc (bản alpha).

## Notes nội bộ (để mình gửi nhanh)

- Mấu chốt bán: “semi-auto để ra hàng nhanh + kiểm soát brand + giảm rủi ro API/bản quyền”, tránh hứa 120 giây ngay từ đầu.
- Nếu đối tác insist “120s”, mình chốt “best-effort + điều kiện input chuẩn + template cố định + quota/peak giới hạn”.

## Zalo Sending Text

```sh
“Automation Video BĐS / Core Engine”. Đánh giá: làm được tại VN (Hải Phòng) nếu triển khai MVP semi-auto trước để ra hàng nhanh và kiểm soát chất lượng.

Luồng MVP: Sale gửi ảnh + thông số lô đất qua Zalo (theo format chuẩn) → hệ thống tự viết kịch bản/caption, chọn giọng đọc tiếng Việt theo vùng miền, dựng video theo template thương hiệu → trả video + link duyệt trên web mobile. Duyệt xong là tải/đăng ngay.

Chuẩn video đề xuất: 9:16, 45s (có bản 25–30s cho “nguồn ngộp” và 55–60s cho dự án). Luôn kèm watermark + disclaimer pháp lý để an toàn nội dung.

SLA pilot thực tế: trung bình 3–5 phút/video (p95 < 10 phút). Sau tối ưu có thể tiệm cận 90–180s tùy input và tải hệ thống.

Báo giá MVP:

- Gói Pilot khuyến nghị: 80–120tr triển khai + 12–25tr/tháng (quota 3.000–8.000 video/tháng).
- Gói rẻ nhất: 60–80tr triển khai + 8–15tr/tháng (scope tối giản, không cam kết 120s).
Nếu anh/chị ok, bên em gửi SOW + timeline 3–4 tuần và demo bản alpha sau 7–10 ngày làm việc.
```