# Drillory: Luyện nhanh. Nhớ lâu.

## 1) Mục tiêu
- Tạo app học ngoại ngữ theo dạng “micro-lesson + quiz” để tăng tốc ghi nhớ từ vựng/ngữ pháp/mẫu câu.
- Có QnA/thảo luận theo từng câu hỏi hoặc bài học để người học hỏi – đáp nhanh, tăng “độ dính”.
- Nhắm 2 trục nội dung: English (CEFR/IELTS/TOEIC) và Chinese (HSK + giao tiếp).

## 2) Đối tượng người dùng (persona)
- Người bận rộn (18–35): muốn học 5–10 phút/lần, cần nhắc học và lộ trình rõ.
- Học sinh/sinh viên: luyện đề theo cấp độ, cần thống kê tiến bộ.
- Người tự học: cần giải thích “vì sao đúng/sai”, ví dụ, phát âm, và ôn tập theo Spaced Repetition.
- Giáo viên/mentor (giai đoạn sau): muốn tạo bộ câu hỏi, giao bài, xem kết quả lớp.

## 3) “Pain” cần giải
- Học rời rạc, không ôn đúng lúc → quên nhanh.
- Quiz nhiều nhưng thiếu giải thích, thiếu ví dụ.
- Hỏi đáp phân tán (group/chat) → khó tra lại theo ngữ cảnh.
- Không biết nên học gì tiếp theo, thiếu lộ trình/cấp độ.

## 4) Giá trị khác biệt (USP)
- Quiz kèm “giải thích + ví dụ + mẹo” cho từng lựa chọn (đúng & sai).
- QnA gắn theo từng câu hỏi/item (thread) → tìm lại kiến thức cực nhanh.
- Ôn tập theo lịch SRS + quiz “trộn” để chống học vẹt.
- Nội dung có “điểm chuẩn” theo cấp độ (CEFR A1–C1 / HSK 1–6) và mục tiêu (thi/giao tiếp).

## 5) Luồng học (happy path)
1) Onboarding: chọn ngôn ngữ (EN/ZH), mục tiêu (thi/giao tiếp), cấp độ, thời gian/ngày.
2) Home: “Bài hôm nay” gồm: Learn (3–5 thẻ) → Quiz (5–10 câu) → Review (SRS).
3) Sau quiz: xem giải thích + lưu lỗi sai vào “Review queue”.
4) Nếu thắc mắc: mở QnA của câu → đọc thread/đặt câu hỏi.

## 6) MVP (đủ ra bản dùng thật)
- Tài khoản + onboarding cơ bản (có thể cho guest trước).
- Bộ nội dung mẫu: tối thiểu 10 bài/level cho 1 track (ví dụ: English A1 hoặc HSK1).
- Quiz engine:
  - Multiple choice (từ vựng/ngữ pháp)
  - Cloze (điền từ)
  - Listening MCQ (nếu có audio)
- Review theo SRS:
  - Lịch “due” theo item
  - Nút “Again/Hard/Good/Easy”
- QnA thread cho từng câu hỏi:
  - Tạo câu hỏi, trả lời, upvote
  - Report nội dung xấu
- Thống kê tối thiểu:
  - Streak, số câu làm, tỉ lệ đúng theo tag/level

## 6.1) Định vị VN-first (cá nhân trước)
- VN 2026: ưu tiên “luyện đúng lỗi sai + nhớ lâu” hơn là “course đầy đủ”.
- Pack-first để ra tiền nhanh, sau đó mở subscription khi có library đủ lớn.

## 6.2) Monetization (Pack-first)
- Pack A (TOEIC): Bootcamp 30 ngày (Part 5/6 trọng tâm)
  - Giá gợi ý: 199k
  - Nội dung tối thiểu để bán: 300 câu Part 5 + 50 câu Part 6 (per-choice explanation + tags)
- Pack B (HSK): Starter 14 ngày (HSK1–HSK2)
  - Giá gợi ý: 99k
  - Nội dung tối thiểu để bán: 400 items (vocab/cloze/mẫu câu)
- Upsell (sau 2–4 tuần, khi có data): Pro Monthly 49k–99k
  - Full SRS (không giới hạn/ngày)
  - Analytics theo tag + error mining
  - Unlock full library (khi mở rộng)

## 6.3) A/B test thị trường (14 ngày)
- Mục tiêu: chọn nhánh nào ra tiền nhanh hơn (paid / intent-to-pay), không tối ưu thứ cấp.
- A: TOEIC 450–700 (Part 5/6)
  - Hook content: bẫy grammar/vocab (90% chọn sai vì...)
  - CTA: làm test 3 phút / nhận 20 câu free
- B: HSK 1–3
  - Hook content: cấu trúc dễ nhầm (了/在/不/没...) + từ HSK gặp hàng ngày
  - CTA: nhận deck 7 ngày
- KPI tối thiểu:
  - Activation: hoàn thành onboarding + xong session đầu
  - Retention: D2/D7 (quay lại làm due)
  - Monetization proxy: paywall views, start checkout, purchases
  - Quy tắc quyết định: nhánh nào paid nhanh hơn 2x → tập trung nhánh đó.

## 6.4) App Store/Play copy (nháp)
- Drillory: Quiz + Ôn tập SRS
- Luyện 10 phút/ngày: quiz có giải thích bẫy + ôn đúng lúc để nhớ lâu.
- Mỗi câu có giải thích cho cả đáp án đúng & sai, lưu lỗi sai vào hàng ôn tập.

## 7) Out of scope (để tránh phình)
- Marketplace nội dung UGC phức tạp
- Voice speaking chấm tự động (để phase sau)
- Chat AI “tổng quát” (nếu có thì chỉ ở vai trò giải thích câu hỏi)

## 8) Mô hình nội dung (content model)
### 8.1 “Item” (đơn vị học nhỏ nhất)
- prompt: câu hỏi/đề bài
- choices: danh sách đáp án + giải thích per-choice
- answer: đáp án đúng + rationale ngắn
- examples: 1–3 ví dụ + dịch (tuỳ track)
- tags: topic (food/travel…), skill (grammar/vocab/listening), level (A1/HSK1…)
- media: audio/image (optional)

### 8.2 “Lesson/Deck”
- title, level, mục tiêu bài
- list items (10–30 items/bài)
- prerequisite (optional)

## 9) Chấm điểm & feedback (cảm giác “học được”)
- Sau mỗi câu:
  - Hiện giải thích ngắn (1–2 dòng) + nút “xem chi tiết”
  - Nếu sai: nêu lý do sai theo distractor, gợi ý mẹo tránh
- Sau 1 session:
  - Tổng kết lỗi theo tag + đề xuất bài ôn/luyện thêm

## 10) SRS / Ôn tập (điểm sống còn)
- Mỗi item có “stability/interval” và “dueAt”.
- Ưu tiên hiển thị:
  - due items trước
  - lặp lại lỗi sai gần đây
  - trộn item mới với item ôn để tránh mệt
- Đề xuất thuật toán:
  - Bắt đầu bằng biến thể SM-2 đơn giản (Again/Hard/Good/Easy)
  - Sau có data thì chuyển sang adaptive (theo accuracy/response time)

## 11) QnA/Discussion (để tăng retention)
- Thread theo item (một câu hỏi = một “phòng” thảo luận).
- Cho phép:
  - hỏi “tại sao”, xin ví dụ, hỏi phát âm
  - vote câu trả lời hữu ích
  - ghim câu trả lời chuẩn (role admin/teacher)
- Chống spam:
  - rate limit, report, ẩn theo score, lọc từ khoá cơ bản

## 12) Gamification (nhẹ, không làm loãng học)
- Streak + mục tiêu ngày
- XP theo session + bonus khi ôn due
- Badge theo milestone (7 ngày streak, 100 câu đúng…)

## 13) Monetization (gợi ý)
- Freemium:
  - Free: track cơ bản + SRS giới hạn/ngày
  - Pro: full track + thống kê nâng cao + offline + teacher mode (sau)
- B2B nhẹ (phase sau): lớp học/nhóm, giao bài, leaderboard nhóm

## 13.1) Dự trù doanh thu 2026 (VN-first, cá nhân trước)
### Công thức
- Monthly Revenue ≈ (New Users / month) × (Paid Conversion) × (ARPPU)

### Giả định giá (để tính nhanh)
- ARPPU (pack): 149k–199k (tuỳ mix TOEIC/HSK + discount)

### Kịch bản (thay số được)
#### Conservative
- New users/month: 5,000
- Paid conversion: 1.0%
- ARPPU: 149k
- Revenue/month: ~7.45M
- Revenue/year: ~89M

#### Base
- New users/month: 20,000
- Paid conversion: 1.5%
- ARPPU: 169k
- Revenue/month: ~50.7M
- Revenue/year: ~608M

#### Bull (làm tốt nội dung + kênh organic mạnh)
- New users/month: 60,000
- Paid conversion: 2.0%
- ARPPU: 199k
- Revenue/month: ~238.8M
- Revenue/year: ~2.87B

### Ghi chú
- Đây là forecast “pack-first” (cashflow sớm). Nếu thêm subscription sau Q2, tổng doanh thu có thể tăng, nhưng phụ thuộc retention.
- Paid conversion phụ thuộc nhiều vào độ sắc của offer (pack theo mục tiêu) và chất lượng “giải thích distractor + SRS”.

## 14) KPI cần theo dõi
- Activation: hoàn thành onboarding + làm session đầu
- Retention: D1/D7/D30, streak distribution
- Learning: accuracy theo tag, số due hoàn thành/ngày
- Community: % session mở QnA, câu trả lời hữu ích/tuần

## 15) Lộ trình đề xuất
- Phase 0 (1–2 tuần): xác định track đầu tiên + viết 200–400 items chất lượng
- Phase 1 (3–6 tuần): MVP quiz + SRS + QnA + basic analytics
- Phase 2 (4–8 tuần): content authoring tool + teacher mode nhẹ + đa ngôn ngữ UI
- Phase 3: adaptive learning, speaking, marketplace nội dung

## 16) Bộ câu hỏi để mình hỏi bạn (để chốt hướng nhanh)
- Bạn muốn ưu tiên English hay Chinese cho MVP đầu tiên?
- Nhắm “thi” (IELTS/TOEIC/HSK) hay “giao tiếp” trước?
- Bạn muốn QnA dạng cộng đồng mở, hay chỉ trong nhóm/lớp?
- Bạn có sẵn nguồn nội dung (tự viết, mua, import) hay cần pipeline tạo mới?
