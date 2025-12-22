# app-04

## Tóm tắt

App cho hệ **barber / nail / hair salon** ở VN. Cơ hội có thật nếu tránh làm “marketplace đặt lịch” (đốt tiền) và tập trung vào **phần mềm vận hành + tăng doanh thu** cho chủ tiệm.

Brand:

- `Studio Flow`: Salon OS (barber-first, mở rộng nail/hair).
- `Beauty Flow`: sản phẩm spa riêng (tách app/brand, share core services theo Phương án B).

2 hướng chính:

- **Management (Studio Flow)**: lịch hẹn, khách hàng, nhân viên, hoa hồng, dịch vụ/combo, tồn kho, thu chi, nhắc lịch qua Zalo/SMS.
- **AI image**: tư vấn/try-on kiểu tóc/màu tóc/nail style để chốt đơn nhanh hơn và upsell.

## Thực trạng & nỗi đau ở VN

### Nỗi đau vận hành

- Lịch hẹn lộn xộn: ghi sổ, Excel, chat Zalo/Facebook, dễ trùng lịch, quên hẹn.
- Quản lý nhân viên/hoa hồng/ca làm: khó minh bạch, dễ thất thoát.
- Không có CRM đúng nghĩa: khách cũ không quay lại đều, chăm sóc sau dịch vụ yếu.
- Thu chi/tồn kho: thuốc nhuộm, hóa chất, sản phẩm chăm sóc… thất thoát khó kiểm soát.

### Nỗi đau tăng trưởng

- Ads ngày càng đắt, phụ thuộc Facebook/TikTok.
- Khách “walk-in” nhiều nhưng không convert thành khách quay lại.
- Review/UGC quan trọng nhưng không có quy trình xin đánh giá/nhắc lịch.

### Vì sao nhu cầu thật

- Ngành làm đẹp phân mảnh, nhiều tiệm nhỏ; chủ tiệm muốn **đơn giản + dùng được ngay trên điện thoại**.
- Chủ tiệm sẵn sàng trả tiền nếu phần mềm giúp:
  - tăng tỉ lệ quay lại
  - giảm trùng lịch/nhỡ lịch
  - minh bạch hoa hồng
  - giảm thất thoát

## Market nhìn như thế nào

### Phân khúc nên nhắm (ICP)

- **Nail salon**: số lượng lớn, quy trình dịch vụ rõ, booking dày.
- **Barber shop**: lịch hẹn/nhân viên/hoa hồng đơn giản, dễ triển khai.
- **Hair salon**: tồn kho + dịch vụ nhiều biến thể (màu/uốn/duỗi), upsell tốt.
- **Spa nhỏ / clinic mini**: cần nhắc lịch tái khám/tái liệu trình (LTV cao) nhưng đòi hỏi quy trình.

Ưu tiên: nail + barber + hair nhỏ (1-10 nhân sự), vì triển khai nhanh và ít yêu cầu tùy biến.

### Cạnh tranh (quan sát thực tế)

- Thường có các phần mềm POS/booking trong nước, nhưng hay gặp vấn đề:
  - UI rối, dùng khó trên mobile
  - thiếu kết nối Zalo/automation chăm sóc
  - báo cáo không “ra tiền” (không chỉ ra hành động)

## Hướng sản phẩm khả thi

### Option A (khuyến nghị): Salon OS + Zalo-first CRM

Giá trị cốt lõi: **đưa mọi tương tác khách hàng về 1 nơi** và tự động hoá các việc lặp lại.

Module:

- Booking: lịch theo nhân viên/ghế/giường, chặn trùng, đặt trước.
- Khách hàng (CRM): lịch sử dịch vụ, ghi chú, tag, ngày sinh, thói quen.
- Nhắc lịch: template tin nhắn, nhắc trước 24h/2h, follow-up sau dịch vụ.
- Nhân viên: ca làm, KPI, hoa hồng, tip.
- Tồn kho cơ bản: nhập-xuất, cảnh báo tồn.
- Thu chi + báo cáo: doanh thu theo dịch vụ/nhân viên/khung giờ, tỉ lệ quay lại.

Điểm khác biệt nên có:

- Tối ưu cho **điện thoại**.
- “Actionable metrics”: mỗi báo cáo gợi ý hành động (ví dụ nhóm khách 30 ngày chưa quay lại).

### Option B: AI image (try-on) để chốt đơn & upsell

Use-case:

- Khách chọn kiểu tóc/màu tóc/nail: “thử” nhanh trước khi làm.
- Tạo catalog cá nhân hoá cho khách: trước/sau, style gợi ý theo khuôn mặt/tông da.

Định vị hợp lý:

- Bán như **add-on** cho Salon OS (tăng ARPU), không nên làm app AI standalone ngay.

### Option C: Marketplace đặt lịch

Rủi ro cao:

- Phải đốt tiền để kéo cả supply lẫn demand.
- “Multi-home”: tiệm vẫn bán đa kênh, khó độc quyền.

Chỉ nên làm khi đã có mạng lưới salon dùng OS đông và có dữ liệu/quan hệ.

## MVP đề xuất (8-12 tuần)

### MVP 1: Booking + CRM + nhắc lịch

- Tạo dịch vụ + nhân viên
- Đặt lịch + check-in + hoàn thành
- Lưu khách + lịch sử
- Nhắc lịch (bắt đầu bằng SMS/email; hoặc Zalo OA nếu triển khai được)

### MVP 2: Hoa hồng + báo cáo quay lại

- Hoa hồng theo dịch vụ / theo %
- Nhóm khách theo RFM đơn giản: gần đây / tần suất / tổng chi

## Mô hình doanh thu

- SaaS theo tháng:
  - Starter: 199k-299k/tháng (1-3 nhân sự)
  - Pro: 499k-799k/tháng (4-10 nhân sự)
  - Add-on AI: +199k-499k/tháng tuỳ quota
- Phí tin nhắn: pass-through theo usage (SMS/Zalo)

## Go-to-market (VN)

- Bán theo cụm địa phương: Q/TP (HCM, HN, ĐN, HP), tập trung 1-2 quận trước.
- Kênh:
  - cộng tác với nhà cung cấp mỹ phẩm/thiết bị (họ đã có mạng lưới chủ tiệm)
  - cộng đồng Facebook/Zalo ngành nail/hair
  - TikTok content “quản lý tiệm tăng doanh thu” (case study)
- Onboarding: làm “done-for-you” 1-2 tuần đầu (import khách, set dịch vụ, template chăm sóc).

## Sales pitch (barber-first) cho Studio Flow

### ICP để chốt nhanh

- Barber shop 2-8 thợ
- Có nhận đặt lịch qua Zalo/Facebook, hay bị trùng lịch/no-show
- Chủ tiệm trực tiếp quản lịch, chưa có CRM

### Offer

- Setup done-for-you trong 60-90 phút
- Chuẩn hoá dịch vụ + thời lượng + thợ
- Đưa lịch hẹn vào 1 nơi, tránh trùng lịch
- Nhắc lịch trước 24h và 2h, follow-up sau cắt

### Pricing đề xuất

- `499k/tháng` (tối đa 8 thợ)
- Add-on tin nhắn: tính theo usage (pass-through)
- Tuỳ chọn: miễn phí setup nếu thanh toán 3 tháng

### Mục tiêu pilot 14 ngày (5 tiệm)

- 5 tiệm dùng thật
- 2 tiệm trả tiền ngay trong tuần 2
- 3 chỉ số thành công:
  - giảm số lịch bị trùng/nhỡ
  - giảm no-show
  - tăng số khách quay lại trong 30 ngày

### Script nhắn Zalo (ngắn)

- Mở đầu:
  - “Anh/chị ơi, em thấy tiệm mình đông, lịch đặt qua chat dễ bị trùng/nhỡ. Em có tool giúp quản lịch theo thợ + nhắc lịch tự động để giảm no-show.”
- Mồi số liệu:
  - “Chỉ cần giảm 1-2 khách no-show/tuần là đủ tiền phần mềm.”
- CTA:
  - “Em qua set up giúp 60 phút, dùng thử 14 ngày. Nếu không giúp tiệm đỡ rối lịch thì thôi.”

### Objection thường gặp

- “Anh đang dùng sổ/Excel quen rồi”
  - “Em không bắt anh đổi hết. Em chỉ gom lịch vào 1 nơi để khỏi trùng và có nhắc lịch. Anh vẫn có thể ghi chú như cũ.”
- “Sợ nhân viên không dùng”
  - “Thợ chỉ cần xem lịch của mình, còn chủ tiệm là người chốt lịch. Em set quyền để thợ không phải thao tác nhiều.”
- “Đắt”
  - “Chỉ cần giảm 1 khách no-show là hoà vốn. Nếu không ra hiệu quả trong 14 ngày thì mình dừng.”

### Onboarding checklist

- Tạo chi nhánh, giờ mở cửa
- Thêm thợ, phân quyền
- Set dịch vụ + thời lượng
- Import khách top 50-200 (tối thiểu: tên + số)
- Set template nhắc lịch + follow-up

## Phương án B (Studio Flow + Beauty Flow): checklist core services dùng chung

Mục tiêu: 2 app/2 brand tách hẳn, nhưng dùng chung “engine” để không nhân đôi công sức.

### B1 (default): share CRM + Messaging + Billing, booking tách

Share:

- Org/Branch/Staff: tài khoản, phân quyền, nhiều chi nhánh
- Customer (CRM core): hồ sơ khách, tag/segment, lịch sử tương tác
- Messaging: template, lịch nhắc, log gửi, giới hạn spam cơ bản
- Billing: gói tháng, trial, invoice, trạng thái thanh toán
- Audit: log thay đổi dữ liệu quan trọng

Tách riêng:

- Booking/Calendar: logic lịch hẹn, resource (ghế/giường/phòng), flow check-in/done
- Vertical modules:
  - Studio Flow: hoa hồng, tip, dịch vụ theo thợ
  - Beauty Flow: liệu trình/phác đồ, tái liệu trình, hồ sơ chi tiết

### B2 (optional): share thêm Booking core

Khi nào chọn B2:

- Beauty Flow và Studio Flow có thể dùng chung mô hình `Appointment`/`Resource` mà không cần custom quá nhiều
- Bạn muốn báo cáo/CRM có lịch sử dịch vụ thống nhất từ cả 2 app

Share thêm:

- Appointment core: đặt lịch, trạng thái, thời lượng, hủy/no-show
- Resource core: staff/room/chair (mỗi app map resource theo vertical)

### Ranh giới data để không bị “đụng nhau”

- Dùng chung: `Organization`, `Branch`, `Staff`, `Customer`, `MessageTemplate`, `MessageLog`, `Subscription`
- Tách riêng: mọi thứ liên quan nghiệp vụ đặc thù (treatment plan, commission rules, product stock nâng cao)

### Thứ tự migrate an toàn (khuyến nghị)

- Bước 1: share Billing
- Bước 2: share Customer/CRM
- Bước 3: share Messaging
- Bước 4: cân nhắc Booking core (chỉ khi cần, chuyển theo từng nhóm tiệm)

## Kế hoạch kiếm 5 tiệm barber đầu tiên (thực chiến)

Mục tiêu: trong 14 ngày có 5 tiệm dùng pilot và chốt tối thiểu 2 tiệm trả tiền.

### Funnel mục tiêu

- Lead list: 60-100 tiệm
- Contacted: 40-70
- Book demo: 10-15
- Pilot: 5
- Paid: 2+

### Kênh lấy lead (VN)

- Google Maps: tìm “barber”, “barbershop” theo quận
- Facebook: page tiệm + group barber địa phương
- TikTok: tiệm có clip đều, comment xin contact
- Hỏi nhà cung cấp sáp vuốt tóc/ghế cắt/đào tạo barber (deal referral)

### Chỉ tiêu hoạt động mỗi ngày (7 ngày đầu)

- 15-20 tiệm được add vào lead list
- 10-15 tin nhắn Zalo/Facebook
- 5 cuộc gọi
- 1-2 lịch hẹn demo

### Script gọi nhanh (60 giây)

- “Em đang làm `Studio Flow` giúp tiệm giảm trùng lịch/no-show và nhắc lịch tự động. Anh/chị cho em hỏi tiệm mình đang nhận đặt lịch qua Zalo hay khách tự đến là chính?”
- Nếu họ có nhận đặt lịch:
  - “Em xin 10 phút demo. Nếu không giúp tiệm đỡ rối lịch thì thôi.”
- Chốt lịch:
  - “Em qua tiệm hoặc call video 10 phút, anh/chị rảnh khung nào hôm nay/mai?”

### Script nhắn follow-up sau khi họ seen

- “Em gửi 1 ảnh demo lịch theo thợ + mẫu nhắc lịch. Nếu anh/chị ok, em qua set 60 phút, dùng thử 14 ngày.”

### Tracking sheet (cột tối thiểu)

- Tên tiệm
- Địa chỉ/quận
- Quy mô (số thợ)
- Kênh contact (Zalo/FB/phone)
- Tình trạng (new/contacted/seen/replied/demo/pilot/paid/lost)
- Pain chính (trùng lịch/no-show/hoa hồng)
- Ngày demo
- Ngày bắt đầu pilot
- Kết quả tuần 1 (đỡ trùng lịch? nhắc lịch chạy?)
- Note

### Checklist chạy pilot 14 ngày (để không fail)

- Ngày 0: setup dịch vụ + thợ + giờ mở cửa
- Ngày 1-2: đưa toàn bộ lịch mới vào `Studio Flow`
- Ngày 3: bật nhắc lịch 24h + 2h
- Ngày 7: review số no-show, chỉnh template nhắc lịch
- Ngày 10: gửi report ngắn cho chủ tiệm (3 dòng + 1 đề xuất hành động)
- Ngày 14: chốt gói trả phí

### Cách chốt trả phí (cực ngắn)

- “14 ngày rồi anh/chị thấy lịch có đỡ trùng/nhỡ không? Nếu ok mình vào gói `499k/tháng`, em giữ setup + template nhắc lịch cho tiệm.”

## Cách validate nhanh (không code nhiều)

- Phỏng vấn 15-25 chủ tiệm, hỏi:
  - hiện quản lịch thế nào
  - thất thoát/nhỡ lịch xảy ra bao nhiêu lần/tuần
  - có đo tỉ lệ khách quay lại không
  - họ đang trả bao nhiêu cho phần mềm hiện tại (nếu có)
- Làm landing + demo Figma + chốt “đặt cọc tháng đầu” với 5-10 tiệm.
- Pilot 2 tuần: đo 3 chỉ số
  - số lịch bị trùng/nhỡ
  - số khách quay lại sau 30 ngày
  - thời gian chủ tiệm dành cho sắp lịch mỗi ngày

## Rủi ro & cách né

- Rủi ro “custom theo từng tiệm”: giới hạn cấu hình, không nhận feature lệch lõi.
- Rủi ro tích hợp Zalo: chuẩn bị phương án fallback SMS.
- Rủi ro churn: cần báo cáo “ra tiền” + automation chăm sóc để giữ giá trị.

 