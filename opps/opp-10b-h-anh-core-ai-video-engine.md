# Opp 10b - Hoang Anh

- Link: https://docs.google.com/document/d/1xzzuJy6t-MW6ApK8b387MQxDL-Vtkl9VaJCxbbhw4fw/edit?tab=t.0

## Tóm tắt nhanh

- Khách hàng: (chưa rõ)
- Bối cảnh: Sàn BĐS nhiều sale, cần sản xuất video hàng loạt, tránh nghẽn khi đồng thời.
- Mục tiêu kinh doanh: “Nhà máy” tạo video, sale thao tác tối giản, quản trị tập trung, thu phí theo gói/quota.
- Deadline: (chưa rõ)

## Yêu cầu/đầu bài (raw)

- Sale bấm “Tạo video” đồng thời → hệ thống vẫn chạy mượt, không crash.
- Có cơ chế “xếp hàng” và trả kết quả theo kiểu callback khi xong.
- Có kế hoạch triển khai 3 giai đoạn: Alpha → Beta → Launch để chốt deadline.

## Giả định

- Khách không quan tâm kỹ thuật chi tiết, chỉ cần cam kết trải nghiệm, tốc độ, chất lượng, quản trị.
- “Core AI” là hộp đen đã có sẵn; phần còn lại là hạ tầng, điều phối và vận hành.
- “Batch 20” là cách nói về giới hạn xử lý song song, có thể thay đổi theo đo đạc.

## Rủi ro & điểm cần xác minh

- “Batch 20” mơ hồ: batch gom 20 job vào 1 call hay chỉ là concurrency limit = 20.
- Queue chỉ giúp xếp hàng, không tự tạo thêm năng lực; cần plan scale theo tải thực tế.
- Rate limit/quota từ dịch vụ render/TTS/LLM mới là bottleneck chính, không chỉ n8n.
- Webhook/Callback thiếu yêu cầu tin cậy: retry, idempotency, chữ ký bảo mật, trạng thái lỗi.
- Storage “URL công khai” có rủi ro; cần pre-signed URL hoặc cơ chế truy cập có hạn.

## Hướng tiếp cận đề xuất

- MVP: điều phối job bất đồng bộ + web mobile duyệt + quản trị tối thiểu + đo đạc SLA/chi phí.
- Giai đoạn 2: tối ưu latency, autoscale theo queue depth, priority job, báo cáo nâng cao, tích hợp CRM sâu.
- Loại trừ: auto-post 100% đa nền tảng ngay từ đầu, nhạc trend tự động, fine-tune giọng thương hiệu (làm sau).

## Câu hỏi chốt scope (để trả lời trong ngày)

- Mục tiêu trải nghiệm: “ra video trong X phút” hay “ra video trong 120s” (best-effort)?
- Peak load: số sale đồng thời / số video/ngày / video/tháng.
- Đầu ra cần gì: 9:16 bắt buộc? có cần 1:1 / 16:9 không?
- Có duyệt tay không? Nếu có thì ai duyệt và cần chỉnh sửa gì trên web mobile?
- Quy tắc brand/pháp lý bắt buộc hiển thị (watermark, disclaimer, từ cấm).
- Cách tính phí mong muốn: theo quota video/tháng hay theo số sale?

## Lọc insight non-tech từ Part 1–2 (cái “đúng” để nói chuyện với khách)

- Nỗi đau: nhiều sale thao tác đồng thời làm hệ thống “ngộp”, trải nghiệm tệ, mất cơ hội chốt nhanh.
- Kỳ vọng: bấm tạo video xong là “đang xử lý”, không phải ngồi chờ; xong cái nào trả cái đó.
- Giá trị: hệ thống chạy bền 24/7, có “xếp hàng đến lượt”, không phụ thuộc kỹ năng dựng video của sale.
- Quản trị: dữ liệu/video tập trung về doanh nghiệp (CRM/drive), không nằm rải rác trên máy sale.
- Chuẩn hóa: logo/màu/font/format đồng nhất để giữ nhận diện và uy tín thương hiệu.
- Cam kết nên nói: có SLA rõ ràng, có báo cáo vận hành, có lộ trình Alpha/Beta/Launch.

## Tiêu chuẩn thực sự của “Core AI Engine” (định nghĩa để làm và để bán)

### 1) Tiêu chuẩn sản phẩm (đầu vào/đầu ra)

- Input tối thiểu: text bán hàng + 3–10 ảnh + preset thương hiệu + tuỳ chọn giọng vùng miền.
- Output tối thiểu: video MP4 9:16 + caption/subtitle + metadata (mã lô/dự án, CTA) + link tải.
- Chất lượng: chữ dễ đọc trên mobile, giọng Việt tự nhiên, watermark/disclaimer chuẩn.

### 2) Tiêu chuẩn trải nghiệm (SLA thực tế)

- Người dùng: tạo job < 3 giây (nhận “đang xử lý”).
- Render: cam kết theo 2 tầng
  - Pilot: median 3–5 phút/video, p95 < 10 phút
  - Scale: median 90–180 giây, p95 < 5 phút (khi đủ hạ tầng + quota)
- Minh bạch: có trạng thái job, có thông báo khi xong, có lỗi rõ ràng khi fail.

### 3) Tiêu chuẩn vận hành (reliability & scale)

- Bất đồng bộ: job queue + worker với concurrency limit cấu hình được.
- Idempotent: request_id/job_id chống chạy trùng gây tốn tiền.
- Retry có kiểm soát: lỗi tạm thời retry, lỗi dữ liệu đưa vào hàng lỗi để xử lý.
- Scale theo tải: tăng worker/core theo queue depth và quota dịch vụ render/TTS/LLM.

### 4) Tiêu chuẩn quản trị (governance)

- Brand preset versioning: template/logo/font/màu/disclaimer quản lý tập trung.
- Policy nội dung: từ cấm/từ nhạy cảm, disclaimer bắt buộc, watermark bắt buộc.
- Quota theo team/user: chống spam, ưu tiên job “nguồn nóng”.

### 5) Tiêu chuẩn bảo mật (bắt buộc nếu thương mại hóa)

- Storage: link ảnh/video có hạn (pre-signed), không public bừa.
- Webhook: chữ ký HMAC + HTTPS + retry; secret rotate; tách dev/stg/prod.
- Audit log: ai tạo job/ai duyệt/ai tải.

### 6) Tiêu chuẩn đo đạc (để tối ưu chi phí và chứng minh giá trị)

- Metric: queue depth, time-in-queue, p50/p95 render time, success rate, cost/video, rate-limit events.
- Báo cáo: theo ngày/tuần/tháng cho leader; cá nhân hoá cho sale.

## Bảng chi phí “thực tế” để triển khai Core Engine + IT (VN/Hải Phòng)

Mục đích bảng này là phản biện kỳ vọng kiểu “một viện nào đó đóng gói xong là xài được”. Phần “đóng gói AI” chỉ là một mảnh nhỏ; cái tốn tiền là hạ tầng sản phẩm hoá, chịu tải, bảo mật và vận hành.

### 1) Chi phí nhân sự build (one-time)

Giả định: dùng dịch vụ sẵn có cho LLM/TTS/render; đội mình làm hệ thống điều phối + sản phẩm hoá.

- MVP thu tiền (semi-auto, có web duyệt, SLA pilot): 4–6 tuần
  - 1 Tech Lead/Backend
  - 1 Backend (jun/mid)
  - 0.5 Frontend (part-time)
  - 0.25 DevOps (part-time)
  - Tổng effort: ~2.0–3.0 người-tháng
  - Chi phí HP (ước tính): 80–160 triệu
- V1 production (multi-tenant cơ bản, quota, audit, monitoring, runbook): 8–12 tuần
  - 1 Tech Lead
  - 2 Backend
  - 1 Frontend
  - 0.5–1 DevOps/SRE
  - 0.5 QA (part-time)
  - Tổng effort: ~6–10 người-tháng
  - Chi phí HP (ước tính): 250–600 triệu
- “Xịn xò enterprise” (99.9%, HA, compliance, autoscale chuẩn, billing): 4–6 tháng
  - 8–12 người, 25–45 người-tháng
  - Chi phí HP (ước tính): 1.2 – 2.8 tỷ

### 2) Chi phí hạ tầng vận hành (monthly, chưa tính cost AI theo video)

Các hạng mục khiến “Core Engine + IT” không đơn giản:

- Compute cho API/worker/queue
- Storage ảnh/video + băng thông/CDN
- Observability: log/metric/alert
- Bảo mật: secrets, rotation, tách môi trường, audit log
- Dự phòng lỗi: retry, DLQ, backup

Ước tính tối thiểu theo quy mô:

- MVP/pilot: 5–20 triệu/tháng
- V1 production: 20–80 triệu/tháng
- Enterprise/HA: 80–250+ triệu/tháng

### 3) Chi phí biến đổi theo sản lượng (per-video)

Tuỳ nhà cung cấp và preset, chi phí biến đổi thường gồm:

- LLM: viết kịch bản/caption
- TTS: giọng đọc tiếng Việt
- Render: ghép video/hiệu ứng/subtitle

Ước tính “rổ chi phí” thực tế (VN) cho 1 video: 1.500 – 8.000đ/video.

Ví dụ:

- 3.000 video/tháng: 4.5 – 24 triệu/tháng
- 10.000 video/tháng: 15 – 80 triệu/tháng

### 4) Kết luận để nói với khách (ngắn gọn)

- Một hệ thống “core engine thương mại hoá” = sản phẩm + hạ tầng + vận hành, không chỉ là workflow AI.
- Với mức “đủ thu tiền” ở VN/Hải Phòng, chi phí thực tế thường rơi vào:
  - One-time: 80–160 triệu (MVP) hoặc 250–600 triệu (V1 production)
  - Monthly: 5–20 triệu (MVP) + cost theo video (tuỳ sản lượng)

## Dung lượng thị trường & mô hình thu phí (HP/VN)

Phần này để định giá theo “giá trị tạo ra”, tránh bị kéo về cuộc chơi “tool AI rẻ”.

### 1) Cách ước tính nhanh (đủ để ra quyết định)

Thực tế nhu cầu bùng lên từ sàn/đội sale có thói quen đăng short-video đều đặn.

- 1 sale đăng: 0.5–1.5 video/ngày (khi có nguồn hàng và kỷ luật)
- 1 sàn có N sale → nhu cầu tháng ~ N * (15–45) video/tháng

Ví dụ:

- Sàn 20 sale: 300–900 video/tháng
- Sàn 50 sale: 750–2.250 video/tháng
- Sàn 100 sale: 1.500–4.500 video/tháng

### 2) Định vị sản phẩm để bán được (không sa vào “AI tool”)

- Bạn không bán video editor, bạn bán: tốc độ ra hàng + chuẩn hoá brand + quản trị tập trung + báo cáo + giảm chi phí nhân sự media.
- Cách tính phù hợp nhất: theo quota video/tháng + overage (có thể add-on seat, nhưng không nên seat là chính).

### 3) Khung giá đề xuất (đủ biên lợi nhuận ở VN)

Giả định cost biến đổi 1.500–8.000đ/video, cần biên để support/ops/rủi ro quota.

- Setup (one-time):
  - Standard: 120–180 triệu
  - Fast-track (gấp, nhiều tuỳ biến brand): 180–300 triệu
- Subscription theo quota (monthly):
  - Starter 2.000 video: 18–28 triệu/tháng
  - Growth 5.000 video: 35–55 triệu/tháng
  - Pro 10.000 video: 65–99 triệu/tháng
  - Enterprise: deal theo peak + SLA + HA
- Overage: 4.000–7.000đ/video (tuỳ tier)

### 4) Ước tính doanh thu khả dĩ (kịch bản thực dụng)

Không cần biết chính xác “bao nhiêu sàn ở HP”; chỉ cần giả định tỷ lệ chốt và size khách.

- Hải Phòng (năm 1):
  - Chốt 5 sàn vừa (tier Growth 5.000 video, ~45tr/tháng) + 5 sàn nhỏ (Starter 2.000 video, ~22tr/tháng)
  - MRR ~ (5*45 + 5*22) = 335 triệu/tháng
  - ARR ~ 4.0 tỷ/năm
  - Setup fee (10 khách * 150tr trung bình) ~ 1.5 tỷ
  - Tổng năm 1 (gross) ~ 5.5 tỷ
- Việt Nam (năm 2, sau khi product ổn):
  - Chốt 30 sàn nhỏ + 20 sàn vừa + 5 sàn lớn (Pro/Enterprise)
  - MRR mục tiêu thực tế: 1.5 – 3.5 tỷ/tháng (tuỳ tỷ lệ khách lớn)

### 5) Điểm cần nhớ khi “chốt giá” với khách

- Giá phải gắn với KPI: số video/tháng, SLA, chuẩn brand, báo cáo, và giảm chi phí đội media.
- Nếu khách ép “rẻ như tool”, đưa họ về “giới hạn SLA/quota/tuỳ biến” thay vì giảm giá vô tội vạ.

## Zalo Chat Sending

```sh
(Vấn Đề 2: Opp-10b) Core Engine + IT không hề đơn giản

- Nếu “viện” chỉ đưa workflow AI (n8n/LLM/TTS/render) thì đó mới là 20–30% câu chuyện. Phần tốn tiền là sản phẩm hoá + chịu tải + bảo mật + vận hành (queue, storage, webhook tin cậy, RBAC, audit, monitoring, retry/DLQ, quota/priority…).
Chi phí build (one-time) theo bối cảnh VN/Hải Phòng (ước tính)

- V1 production “đúng bài” (multi-tenant cơ bản, quota, audit, monitoring, runbook) : 8–12 tuần, ~6–10 người-tháng ⇒ 250–600 triệu
- Enterprise “xịn xò” (99.9%, HA, compliance, autoscale chuẩn, billing) : 4–6 tháng, ~25–45 người-tháng ⇒ 1.2 – 2.8 tỷ
Chi phí vận hành (monthly, chưa tính AI theo video)

- V1 production: 20–80 triệu/tháng
- Enterprise/HA: 80–250+ triệu/tháng
Chi phí biến đổi theo sản lượng (per-video)

- LLM + TTS + render: ~1.500 – 8.000đ/video (tuỳ độ dài, số ảnh, preset, nhà cung cấp)
- Ví dụ:
  - 3.000 video/tháng: 4.5 – 24 triệu/tháng
  - 10.000 video/tháng: 15 – 80 triệu/tháng
```
