
#!/usr/bin/env python3

# Opp 07 – NoLai (Offline Debt & Interest Manager)

## 1. Tóm tắt cơ hội

- **Bài toán:** Quản lý cho vay nợ lãi cần **tính lãi chuẩn**, **nhắc thu/đòi nợ theo quy trình**, **báo cáo nhanh**, nhưng **không muốn phụ thuộc internet** và **đòi hỏi bảo mật dữ liệu rất cao**.
- **Giải pháp:** App **offline-first** (ưu tiên offline tuyệt đối), có **backup/sync kiểu “user-controlled”** (file backup đã mã hoá, người dùng tự lưu vào Drive/iCloud/USB), hỗ trợ đa nền tảng.
- **Định vị:** “Công cụ quản lý công nợ & thu hồi công nợ” (workflow + audit + bảo mật) thay vì spreadsheet.

## 2. Persona & phạm vi khách hàng mục tiêu

- **Persona A (1 người):** cá nhân/nhóm nhỏ tự quản khoản vay, cần app nhanh gọn, không rườm rà.
- **Persona B (2–10 người):** nhóm thu/thu hộ (có phân công), cần lịch sử thao tác, phân quyền, và audit.

## 3. Điểm khác biệt so với Excel/G-Sheets

Excel/G-Sheets mạnh ở linh hoạt & nhập nhanh, nhưng yếu ở:

- **Độ đúng:** 1 lỗi công thức/copy là lệch tiền.
- **Workflow:** không có trạng thái hồ sơ, lịch sử tương tác, task list “hôm nay phải thu ai”.
- **Nhắc việc:** không phải hệ thống nhắc nợ theo khoản vay.
- **Bảo mật:** file dễ share/forward; Sheets phụ thuộc internet/tài khoản.
- **Audit:** khó truy vết ai sửa gì lúc nào.
- **Scale:** 1–3k khoản là báo cáo/lọc bắt đầu cực khó.

NoLai thắng bằng:

- **Chuẩn hoá cách tính lãi + khoá logic tính** (giảm sai lệch).
- **Task-driven thu/đòi nợ** (hôm nay/tuần này phải làm gì).
- **Timeline tương tác** (đã gọi/nhắn/hẹn/trễ bao lâu).
- **Bảo mật mặc định** (mã hoá DB + khoá app + backup mã hoá).
- **Audit log & phân quyền** (khi lên bản team).

## 4. Phạm vi nghiệp vụ (yêu cầu bạn đã chốt)

- **Đa kiểu lãi:** lãi ngày, %/tháng, góp theo kỳ (ngày/tuần/tháng), lãi nhập gốc; có thể mở rộng theo cấu hình.
- **Làm tròn:** cấu hình (100/1,000/không làm tròn).
- **Thu nợ:** vừa có lịch thu theo kỳ, vừa hỗ trợ thu linh hoạt.
- **Nhắc nợ/đòi nợ:** theo trạng thái hồ sơ + lịch sử tương tác.
- **Đa nền tảng:** mobile + desktop (mục tiêu dài hạn).
- **Sync:** ưu tiên **sync nội bộ / user-controlled sync**, hạn chế public internet.
- **Bảo mật:** yêu cầu mức cao (PIN/biometric, mã hoá DB, chống copy DB, audit, panic mode).

## 5. Core modules (MVP → Pro)

### 5.1 Data model tối thiểu

- **Customer**: thông tin định danh, nhiều số liên hệ, ghi chú.
- **Loan**: gốc, ngày giải ngân, phương thức tính lãi, làm tròn, trạng thái.
- **Schedule** (optional theo loại khoản vay): danh sách kỳ thu dự kiến.
- **Payment**: phiếu thu (gốc/lãi/phí), ngày thu, người thu, chứng từ.
- **Interaction log**: gọi/nhắn/gặp, nội dung, hẹn ngày, kết quả.
- **Audit log** (bản Team): ai tạo/sửa/xoá gì, trước/sau.

### 5.2 Màn hình/luồng chính

- **Dashboard:** phải thu hôm nay, trễ hạn, tổng thu, tổng dư nợ.
- **Customer 360:** danh sách khoản vay + timeline tương tác + lịch thu.
- **Loan detail:** lịch thu, tính lãi, cập nhật trạng thái, phiếu thu.
- **Task list:** “Hôm nay gọi ai / thu ai / hồ sơ nào trễ”.
- **Reports:** aging report, thu theo ngày/tuần/tháng, top nợ, vòng quay thu.

### 5.3 Workflow đòi nợ (đề xuất chuẩn hoá)

- Trạng thái: **Mới** → **Đang thu** → **Đến hạn** → **Trễ** → **Hứa trả** → **Đã tất toán** → **Xấu**.
- Quy tắc nhắc: cấu hình theo trạng thái (trước hạn X ngày, trễ Y ngày, hứa trả đến Z ngày).

## 6. Offline-first & kiến trúc bảo mật (mức “production để bán”)

### 6.1 Nguyên tắc

- **Mặc định offline:** app chạy đầy đủ khi không có mạng.
- **Không public backend:** không có server SaaS bắt buộc.
- **User-controlled backup/sync:** sync qua file backup đã mã hoá; người dùng tự chọn nơi lưu.

### 6.2 Mã hoá dữ liệu

- **Database encryption at-rest:** dùng SQLite + SQLCipher.
- **App lock:** PIN + biometric; auto-lock theo idle.
- **Key management:**
  - Khoá mã hoá DB lưu trong Keychain/Keystore.
  - Tùy chọn “Master Password” để:
    - khôi phục khi đổi máy
    - tạo file backup E2E encrypted.
- **Chống copy DB:** nếu không có key trên thiết bị/mật khẩu thì file DB/backup không đọc được.

### 6.3 Backup/sync (khuyến nghị triển khai theo tầng)

- **Tier 1 (MVP, an toàn & dễ ship):**
  - Export/import file backup **đã mã hoá**.
  - Người dùng tự lưu vào:
    - USB / ổ cứng
    - AirDrop
    - Drive/iCloud/OneDrive (chỉ như nơi chứa file, không đọc được nếu thiếu key).
- **Tier 2 (sau MVP):**
  - “2 thiết bị của 1 người” dùng chung: đồng bộ bằng cách cùng trỏ vào 1 file backup + cơ chế merge theo phiên bản.
- **Tier 3 (Enterprise):**
  - Multi-user sync nội bộ: cần conflict resolution + audit + phân quyền nâng cao.

### 6.4 Audit & chống sai

- **Immutable receipts:** phiếu thu sau khi “chốt” chỉ cho phép “đảo/void” thay vì sửa trực tiếp.
- **Audit log:** bắt buộc cho bản team (ai sửa gì, timestamp, trước/sau).
- **Validation:** chặn nhập sai (lãi âm, ngày thu trước ngày vay, làm tròn không hợp lệ, v.v.).

### 6.5 Panic mode (tuỳ chọn)

- Ẩn dữ liệu ngay (mask UI) và yêu cầu xác thực lại.
- Tuỳ chọn xoá nhanh (chỉ nếu người dùng bật và hiểu rủi ro).

## 7. Đa nền tảng: tech stack đề xuất

- **UI/App:** Flutter.
- **DB:** SQLite + SQLCipher.
- **State management:** chọn 1 trong các hướng phổ biến (Bloc/Riverpod) để maintain dài hạn.
- **Crypto:** libs chuẩn, ưu tiên AES-GCM cho file backup.
- **Export reports:** PDF + CSV/XLSX offline.

Lộ trình platform:

- Ưu tiên: **Android**.
- Sau đó: iOS.
- Sau cùng: Windows/macOS nếu nhu cầu thật.

## 8. Gói sản phẩm (đóng gói bán như “Soft Tools”)

### 8.1 Gói Basic (Offline – 1 người)

- Customer/Loan/Payment/Report cơ bản.
- Nhắc việc nội bộ (task list trong app).
- PIN/biometric + DB mã hoá.
- Backup/restore file mã hoá.

### 8.2 Gói Pro (Workflow thu/đòi nợ)

- Workflow trạng thái + lịch sử tương tác.
- Aging report + báo cáo nâng cao.
- Template nhắc (kịch bản gọi/nhắn) theo trạng thái.
- Quy tắc “chốt phiếu thu” chống sửa.

### 8.3 Gói Team/Enterprise (2–10 người)

- Multi-user + phân quyền.
- Audit log đầy đủ.
- Cơ chế đồng bộ (Tier 2/3 theo nhu cầu).
- Chính sách export dữ liệu + watermark.

## 9. Licensing/đóng gói phát hành

- **License theo thiết bị** (hợp offline):
  - Kích hoạt bằng key.
  - Cho phép dùng offline sau khi kích hoạt.
- **Nâng cấp phiên bản:**
  - Basic: cập nhật minor miễn phí X tháng.
  - Pro/Team: gói bảo trì năm.
- **Chính sách dữ liệu:**
  - Dữ liệu thuộc user.
  - App hỗ trợ export/backup chuẩn (mã hoá).

## 10. Định giá đề xuất (VN)

Mô hình giá ưu tiên để dễ bán (offline-first): **license vĩnh viễn theo thiết bị** + add-on dịch vụ + bảo trì tuỳ chọn.

- **NoLai Basic (offline):** 1.490.000 VND / thiết bị (vĩnh viễn).
- **NoLai Pro (workflow + report mạnh):** 2.990.000 VND / thiết bị (vĩnh viễn).
- **Team/Enterprise:** tạm hoãn ở Phase 3 (khi có multi-user + audit + sync nâng cao).

## 10.1 Bảo trì/nâng cấp (bao gồm cả update kỹ thuật + support)

Bảo trì là gói “đảm bảo dùng được lâu dài” cho app offline: vừa **update kỹ thuật**, vừa **hỗ trợ vận hành dữ liệu**.

- **Maintenance Standard:** 499.000 VND / năm / thiết bị.
  - Bugfix + ổn định + tương thích Android/iOS mới.
  - Cập nhật bảo mật (vá thư viện/crypto khi cần).
  - Hỗ trợ qua chat (best-effort trong giờ hành chính): hướng dẫn backup/restore, import/export, xử lý lỗi thường gặp.
- **Maintenance Priority:** 999.000 VND / năm / thiết bị.
  - Tất cả Standard.
  - Ưu tiên xử lý ticket nhanh hơn.
  - Hỗ trợ “cầm tay chỉ việc” cho các ca import/restore phức tạp (giới hạn theo số lần/tháng).

Giới hạn/phạm vi không bao gồm (để tránh nổ scope):

- Không bao gồm phát triển tính năng “theo yêu cầu riêng từng khách” (báo giá dự án).
- Không bao gồm triển khai backend/cloud/server riêng.
- Không cam kết khôi phục dữ liệu nếu người dùng mất cả backup và quên master password (do E2E encryption).
- Không bao gồm can thiệp vào thiết bị/hạ tầng của khách ngoài phạm vi hướng dẫn.

Add-on hợp lý:

- Import dữ liệu từ Excel + chuẩn hoá template: 500.000 – 3.000.000 VND.
- Onboarding 1:1 (60–90 phút): 300.000 – 800.000 VND.

## 11. Đánh giá tiềm năng doanh thu (kịch bản)

Kịch bản tham chiếu (tập trung ngách offline + mã hoá + chuyển từ Excel):

- **90 ngày (khả thi cho solo):** 20 Basic + 10 Pro + add-on import/onboarding.
  - License: 20 × 1.49tr + 10 × 2.99tr ≈ ~60tr.
  - Add-on: ~10tr.
  - **Tổng 90 ngày:** ~70tr.
- **12 tháng (khả thi nếu có kênh CTV/đại lý):** 200 Basic + 100 Pro.
  - License: 200 × 1.49tr + 100 × 2.99tr ≈ ~597tr.
  - Add-on: ~84tr.
  - Bảo trì (giả sử 30% mua gói 699k): ~63tr.
  - **Tổng năm 1:** ~740tr.

Điểm quyết định để “phủ rộng”:

- Kênh phân phối (đại lý/cộng đồng/đối tác kế toán/cầm đồ).
- Tài liệu + onboarding + support.
- Niềm tin về bảo mật (offline + mã hoá mặc định).

## 11.1 Update chiến lược (VN) – ngách & định vị ưu tiên

Chọn hướng cạnh tranh tối ưu cho điều kiện solo:

- **Ngách:** “Sổ công nợ/cho vay offline + mã hoá + chuyển đổi từ Excel”.
- **Không đánh trực diện:** phần mềm cầm đồ dạng cloud + SMS/Email tự động (thị trường đã có người làm mạnh).
- **Sync ưu tiên (Phase 1):** backup/restore file **đã mã hoá**; người dùng tự lưu vào Drive/iCloud/USB (user-controlled).

Thông điệp marketing đề xuất:

- “Sổ công nợ offline, dữ liệu nằm trong máy bạn.”
- “Backup cũng mã hoá: lưu Drive chỉ là cất file, không ai đọc được.”
- “Task list thu tiền hôm nay + tính lãi chuẩn + báo cáo 1 chạm.”

Kênh bán khả thi nhất:

- Nhóm Facebook/Zalo về sổ nợ/công nợ/bán chịu/cầm đồ (định vị “công nợ”, tránh ngôn ngữ nhạy cảm).
- CTV/đại lý (hoa hồng 20–30%) trong hệ sinh thái POS/kế toán/tiệm.
- Video demo 60–90 giây (1 flow end-to-end) để thay sales.

## 12. MVP plan (solo + production đóng gói)

Khuyến nghị chia pha để ra hàng nhanh mà vẫn “production”:

- **Phase 1 (4–6 tuần):** Android + offline + DB mã hoá + backup mã hoá + nhắc việc + báo cáo + 2–3 kiểu lãi phổ biến.
- **Phase 2 (3–5 tuần):** workflow đầy đủ + import/export Excel + polishing + iOS.
- **Phase 3 (4–8 tuần):** team + audit mạnh + sync nâng cao.

## 13. Rủi ro & lưu ý

- **Pháp lý/đạo đức:** cần định vị “quản lý công nợ” và tránh tính năng bị lạm dụng (spam/quấy rối).
- **Sync đa thiết bị/team:** tăng độ phức tạp mạnh; nên bắt đầu bằng backup mã hoá.
- **Support:** nhóm khách này hay cần hướng dẫn; nên chuẩn bị FAQ + video ngắn.

## 14. Next steps

- Chốt 2 quyết định:
  - Sync mục tiêu: **backup Drive/iCloud (Tier 1)** hay cần **2 thiết bị/Team** ngay.
  - Platform ưu tiên: Android trước hay Android+iOS.
- Viết PRD ngắn cho Phase 1 (screens + rules tính lãi top 3).
- Đóng gói bản demo: 1–2 flow end-to-end (tạo khoản vay → nhắc thu → ghi nhận thu → báo cáo).

