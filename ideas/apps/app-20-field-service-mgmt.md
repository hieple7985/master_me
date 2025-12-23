# App #20 — Field Service Management (FSM) cho đội kỹ thuật onsite + invoice

- **Positioning (định vị)**
  - “Job dispatch + mobile app cho kỹ thuật + biên bản/ảnh/POD + thu tiền + xuất hoá đơn” cho SME dịch vụ kỹ thuật.
  - Mục tiêu: biến quy trình Excel/Zalo/điện thoại → quy trình có SLA, có bằng chứng hiện trường, chốt tiền nhanh.

- **ICP (ai mua, ai dùng)**
  - Doanh nghiệp dịch vụ kỹ thuật onsite: điện lạnh, lọc nước, thiết bị gia dụng, thang máy, điện/điện nước, solar, PCCC, camera, máy in/IT service, cửa cuốn.
  - Quy mô: 5–200 kỹ thuật; 1–10 điều phối; 1–10 kế toán/thu ngân.
  - Buyer: chủ doanh nghiệp/COO/Operations Manager.
  - Champion: trưởng điều phối (đau vì missed appointment, không nắm được ai đang làm gì) hoặc kế toán (đau vì đối soát & thu tiền).

- **Pain (điểm đau rõ nhất)**
  - Điều phối rối: nhận việc qua Zalo/điện thoại, lịch chồng, không tối ưu tuyến.
  - Không đo được SLA: phản hồi/chốt lịch/chạy hiện trường phụ thuộc cá nhân.
  - Thiếu bằng chứng: ảnh, biên bản, chữ ký khách, POD/ghi chú bị thất lạc.
  - Thu tiền & đối soát chậm: COD/QR, công nợ phát sinh, thiếu minh bạch chi phí vật tư.
  - Không trace được warranty/serial: khách gọi lại nhiều lần, lịch sử phân mảnh.

- **Wedge (MVP) — bán được bằng demo**
  - 1) Nhận yêu cầu → tạo job → điều phối → kỹ thuật nhận việc trên mobile
  - 2) Onsite checklist + ảnh + chữ ký khách + vật tư tiêu hao
  - 3) Thu tiền (tiền mặt/QR) hoặc ghi công nợ
  - 4) Xuất biên bản + gửi PDF/Zalo + (tuỳ giai đoạn) xuất hoá đơn điện tử

- **Core modules (phạm vi sản phẩm)**
  - Dispatch & scheduling
    - Lịch công việc theo ngày/tuần; drag & drop
    - Assignment: manual + rule đơn giản (khu vực, kỹ năng, ca trực)
    - Trạng thái job: new → scheduled → en-route → on-site → completed → invoiced/closed
  - Mobile app cho kỹ thuật
    - Nhận/nhắc job; điều hướng; check-in/check-out theo thời gian
    - Checklist thao tác; ghi chú; ảnh/video; chữ ký khách
    - Vật tư sử dụng; phí dịch vụ; đề xuất phát sinh
  - Customer & asset history
    - Hồ sơ khách + địa chỉ + site
    - Lịch sử job; lỗi thường gặp; ảnh trước/sau
    - Asset/serial/warranty (tuỳ chọn nhưng nên có sớm cho ngành thiết bị)
  - Payments & invoicing
    - Thu tiền: cash/transfer/QR; ghi công nợ
    - Báo cáo đối soát theo ngày/kỹ thuật
    - Xuất invoice/receipt nội bộ; eInvoice tích hợp làm sau nếu cần
  - Reporting
    - SLA, backlog, missed appointment, first-time-fix, revenue per tech
    - Export CSV

- **Workflow mẫu (as-is → to-be)**
  - As-is
    - Khách nhắn Zalo/phone → điều phối ghi sổ/Excel → gọi kỹ thuật → kỹ thuật báo miệng → kế toán tự đối soát
  - To-be
    - Ticket/job tạo từ form/Zalo/CSKH → auto-tag theo loại việc/khu vực → schedule/assign → mobile execution (checklist + ảnh + sign) → thu tiền/công nợ → xuất biên bản/invoice → báo cáo SLA & doanh thu

- **Data model tối thiểu (để build nhanh nhưng mở rộng được)**
  - Tenant
  - User (dispatcher/technician/accounting) + Role
  - Customer + Site/Location
  - Asset (optional) + Warranty
  - Job/WorkOrder
    - Type, priority, promised window, assigned tech, status history
    - Checklist items, photos, signature, notes
  - ServiceCatalog (dịch vụ) + PriceBook đơn giản
  - PartsUsage (vật tư) + Inventory (optional, phase 2)
  - Payment + Invoice (internal)
  - EventLog/Audit

- **MVP 4–6 tuần (scope chặt để triển khai được)**
  - Dispatcher web
    - Tạo job + gán kỹ thuật + lịch ngày
    - Search/filter theo trạng thái/khu vực
  - Technician mobile (PWA trước cũng được)
    - Nhận job + check-in/out + checklist + ảnh + chữ ký
  - Customer profile + lịch sử job
  - Thu tiền/công nợ cơ bản + biên bản PDF
  - 6 báo cáo lõi
    - On-time rate (% đúng hẹn)
    - Time-to-schedule (từ tạo job → chốt lịch)
    - First-time-fix rate
    - Jobs per tech/day
    - Revenue per tech/week
    - Aging công nợ (nếu cho phép ghi nợ)

- **Tích hợp (ưu tiên theo thứ tự để bán nhanh ở VN)**
  - Maps
    - Google Maps hoặc Mapbox: geocode, route, ETA (phase 2)
  - Messaging
    - Zalo OA/ZNS hoặc SMS: nhắc lịch, thông báo kỹ thuật đang đến, gửi biên bản
  - Payments
    - QR chuyển khoản: hỗ trợ “dán QR”/hướng dẫn; payment gateway tích hợp sau
  - eInvoice
    - Tích hợp nhà cung cấp hoá đơn điện tử phổ biến (khi có nhu cầu rõ)
  - Accounting/ERP
    - Export CSV; API/webhook để đồng bộ đơn/hoá đơn (phase 3)

- **Pricing gợi ý (để chốt nhanh)**
  - Starter
    - Theo số kỹ thuật active/tháng (bundle 5–10)
  - Pro
    - Theo kỹ thuật + dispatch seat + SLA nâng cao + automation
  - Add-ons
    - Multi-branch, inventory xe/kho, warranty/serial nâng cao, ZNS/SMS pack, eInvoice integration, onboarding

- **North-star metrics & KPI**
  - % jobs đúng hẹn (on-time)
  - First-time-fix rate
  - Avg jobs/tech/day
  - % jobs có đủ bằng chứng (ảnh + chữ ký)
  - Days to cash (từ completed → thu tiền)
  - Repeat jobs theo asset/khách (warranty signal)

- **Moat (làm sâu để giữ khách & tăng ARPA)**
  - Template checklist/biên bản theo ngành (điện lạnh, lọc nước, thang máy…)
  - Dữ liệu lịch sử lỗi theo model/serial → gợi ý chuẩn đoán/định mức vật tư
  - Benchmark SLA theo khu vực/ngành (ẩn danh) + playbook giảm missed appointment

- **Rủi ro & cách giảm**
  - Adoption khó nếu mobile UX kém
    - Giảm: ưu tiên thao tác 1 tay, offline-lite (cache job), upload ảnh nền
  - Khách đòi tích hợp eInvoice/kế toán quá sớm
    - Giảm: export chuẩn + pricing add-on rõ; chỉ build integration khi có 3–5 khách cùng nhu cầu
  - “Field service” dễ trùng với CMMS
    - Giảm: định vị wedge = dispatch + proof + cash/invoice (khác CMMS nặng bảo trì định kỳ)

- **GTM experiment 14 ngày (validate nhanh)**
  - 10 cuộc phỏng vấn
    - 4 điện lạnh/điện nước, 3 lọc nước/thiết bị gia dụng, 3 thang máy/solar
  - 3 pilot trả phí nhẹ
    - 2–5 triệu/tháng, triển khai 3 giờ, đo KPI: giảm missed appointment 30% hoặc rút “days to cash” 20%
  - Kênh
    - Hội nhóm Zalo/Facebook ngành kỹ thuật, đơn vị cung cấp vật tư/đại lý, referral kỹ thuật trưởng nhóm