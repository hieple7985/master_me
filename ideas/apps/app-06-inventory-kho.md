# app-06: KhoChuẩn – Quản lý kho + barcode + audit (VN 2026)
 
## Tóm tắt
 
Một SaaS quản lý kho cho SME tại VN, định vị theo kết quả:
- Kiểm kê nhanh hơn.
- Giảm tồn ảo/xuất nhầm.
- Truy trách nhiệm thao tác (audit log).
 
Hướng đi bền vững: Cloud SaaS + thu phí onboarding (remote) để có cashflow sớm và chuẩn hoá vận hành.
 
## Bối cảnh & cơ hội (VN 2026)
 
- Phần lớn SME vẫn dùng Excel hoặc phần mềm chỉ “nhập-xuất-tồn” nhưng không giải được bài toán kiểm kê/nhầm lẫn/thất thoát.
- Nhu cầu barcode hoá và quy trình kiểm kê tăng do chi phí nhân công, thất thoát, và áp lực vận hành nhiều kho/ca kíp.
- Cạnh tranh mạnh ở phần “suite” (POS/ERP), vì vậy định vị cần né cạnh tranh trực diện bằng việc đóng đinh vào kiểm kê + barcode + audit.
 
## ICP (khách hàng mục tiêu)
 
### ICP chính (Phase 1)
- Đại lý vật tư/phụ tùng/thiết bị (B2B thương mại).
- 1,000 - 20,000 mã hàng.
- 2+ nhân sự kho.
- Đau vì tồn ảo, xuất nhầm, kiểm kê mất nhiều ngày.
 
### Không ưu tiên ở giai đoạn đầu
- Retail POS (đụng các suite lớn).
- Sản xuất có BOM phức tạp (triển khai nặng).
 
## Offer chốt (để ra tiền nhanh nhưng bền)
 
- Gói duy nhất trong 90 ngày đầu: “Kho + Barcode + Kiểm kê”.
- Triển khai remote 7-14 ngày.
- Cam kết theo KPI vận hành (giảm thời gian kiểm kê, giảm sai sót), không cam kết “giống ERP/POS”.
 
## Sản phẩm (MVP) - 8 đến 12 tuần
 
### Tính năng bắt buộc
- Danh mục: hàng hoá, đơn vị tính + quy đổi, kho, vị trí (kệ/ô), nhà cung cấp, khách hàng.
- Nghiệp vụ kho: nhập, xuất, chuyển kho, điều chỉnh.
- Kiểm kê: theo kho/vị trí, ghi nhận chênh lệch, chốt kiểm kê.
- Barcode/QR: tạo mã, in tem (template), quét bằng điện thoại.
- Phân quyền (RBAC) + audit log (ai làm gì, khi nào).
- Import/Export Excel theo template chuẩn.
- Báo cáo: tồn theo kho/vị trí, xuất/nhập theo thời gian, chênh lệch kiểm kê.
 
### Lựa chọn kỹ thuật (chốt để ra nhanh)
- PWA (mobile web) cho barcode thay vì native app.
- Cloud multi-tenant, cấu hình đơn giản, ưu tiên time-to-value.
 
### Không làm ở MVP
- Kế toán/hạch toán full.
- BOM sản xuất nâng cao.
- Tích hợp sâu đa hệ thống (chỉ làm export + API tối thiểu ở Phase 2).
 
## Định giá (bền vững)
 
### Onboarding (thu một lần)
- 12,000,000đ / công ty.
- Bao gồm: setup hệ thống, import dữ liệu theo template, cấu hình kho/vị trí, barcode template cơ bản, 3-4 buổi training, hỗ trợ go-live 14-30 ngày.
 
### SaaS (thu hàng tháng)
- 2,500,000đ / tháng / công ty (gói chuẩn).
- Thu đầu kỳ; giảm giá khi trả 12 tháng.
 
### Nguyên tắc phạm vi để không quá tải
- Onboarding chỉ bao gồm 1 lần import theo template; dữ liệu “bẩn”/làm lại nhiều lần tính phí.
- Các yêu cầu tuỳ biến đặc thù được đưa vào backlog Phase 2 và định giá theo hạng mục.
 
## Demo 20 phút (kịch bản chốt)
 
- 0-3 phút: nhắc lại nỗi đau của khách (kiểm kê lâu/tồn ảo/xuất nhầm).
- 3-10 phút: luồng nhập -> in tem -> dán tem -> quét xuất.
- 10-16 phút: kiểm kê theo vị trí -> chốt -> xem chênh lệch.
- 16-20 phút: audit log + phân quyền + chốt onboarding 7-14 ngày.
 
## Onboarding remote 7-14 ngày (playbook)
 
- Ngày 1: kick-off, chốt phạm vi, chốt owner dữ liệu bên khách.
- Ngày 2-3: khách điền template (mã hàng/đvt/quy đổi/kho/vị trí).
- Ngày 4: import + mapping + sửa lỗi dữ liệu.
- Ngày 5-7: training nhập/xuất/chuyển + phân quyền.
- Ngày 8-10: chạy song song + fix quy trình.
- Ngày 11-14: go-live + training kiểm kê + bàn giao.
 
Chính sách support:
- 1 kênh support chính, trong giờ hành chính.
- Go-live support 14-30 ngày; ngoài phạm vi tính phí.
 
## Funnel & go-to-market (toàn VN)
 
### Kênh 1 (chính): Outbound
- Nhắm đúng ICP: đại lý vật tư/phụ tùng/thiết bị.
- Qualify bằng 5 câu hỏi: số mã hàng, số kho, số user kho, pain kiểm kê, người quyết định.
 
### Kênh 2: Đối tác
- Kế toán dịch vụ / IT địa phương / đơn vị bán máy in tem - máy quét.
- Chính sách chia sẻ: 20-30% MRR trong 6-12 tháng hoặc fee theo deal.
 
## KPI kiểm chứng (30 ngày)
 
- 1 khách pilot trả onboarding.
- 2 demo / tuần.
- 50 lead lạnh / ngày (5 ngày/tuần).
- 1 case study có số liệu trước/sau (thời gian kiểm kê, chênh lệch, lỗi xuất nhầm).
 
## Dự phóng 12 tháng (mục tiêu bền)
 
Giả định:
- Onboarding: 12m/khách.
- SaaS: 2.5m/khách/tháng.
- Mục tiêu: 30 khách/năm.
 
Kết quả:
- Onboarding: 30 x 12m = 360m.
- MRR cuối năm: 30 x 2.5m = 75m/tháng.
- Tổng doanh thu năm 1 (xấp xỉ): ~810m.
 
## Roadmap 12 tháng
 
### Phase 1 (0-3 tháng): MVP + 5 khách đầu
- Hoàn thiện kho/vị trí, kiểm kê, barcode PWA.
- Chuẩn hoá template dữ liệu + playbook onboarding.
- Case study thật.
 
### Phase 2 (4-6 tháng): giữ khách + upsell
- Lô/hạn dùng hoặc serial (tuỳ nhu cầu phổ biến).
- Báo cáo nâng cao (tuổi tồn, cảnh báo).
- API/export chuẩn để kết nối phần mềm kế toán.
 
### Phase 3 (7-12 tháng): scale kênh đối tác
- Portal đối tác, tracking lead, chia sẻ doanh thu.
- SLA/support policy rõ ràng.
 
## Moat (lợi thế bền)
 
- Playbook triển khai/chuẩn hoá dữ liệu và quy trình kiểm kê.
- Audit log + quy trình kiểm kê biến thành “kỷ luật vận hành”.
- Dữ liệu vận hành (mẫu sai sót) giúp tối ưu UX và kiểm soát lỗi.
 
## Rủi ro & giảm rủi ro
 
- Cạnh tranh suite lớn: định vị kiểm kê + barcode + audit, không ôm POS/ERP.
- Quá tải support: giới hạn phạm vi onboarding, chuẩn hoá template, tính phí tuỳ biến.
- Dữ liệu bẩn: bắt buộc theo template; có gói làm sạch dữ liệu tính phí.