 # App quản lý cho thuê nhà (Hải Phòng + toàn quốc) — Idea #22
 
 ## 0) Chốt nhanh (decisions)
 - **Idea ID**: #22
 - **Umbrella brand (công ty)**: **KTS** (Kiến Tạo Số)
 - **Tên sản phẩm**: **LetsStay**
 - **Định hướng sản phẩm**: làm **PMS quản lý vận hành** trước (thuê dài hạn), mở rộng **serviced apartment** rồi mới cân nhắc **hotel/OTA**.
 - **Go-to-market chính**: **content/SEO + programmatic SEO** (kèm referral/CTV nhẹ khi cần).
 
 ## 1) Mục tiêu
 Xây app giúp **chủ nhà/nhà trọ/đơn vị quản lý** quản lý vận hành cho thuê (khách, hợp đồng, thu tiền, nhắc nợ, bảo trì, báo cáo) và (tuỳ giai đoạn) hỗ trợ **đăng tin/đầy phòng**.
 
 ## 2) Bối cảnh & giả định
 - **Hải Phòng**: thị trường cho thuê đa dạng (công nhân khu công nghiệp, sinh viên, hộ gia đình thuê dài hạn, nhà nguyên căn, căn hộ dịch vụ). Nhu cầu quản lý tăng khi chủ nhà có nhiều phòng/căn, hoặc làm “bán chuyên”.
 - **Toàn quốc**: cạnh tranh cao ở mảng **đăng tin/marketplace**, nhưng mảng **property management (PMS) cho cá nhân/SMB** vẫn còn dư địa nếu làm tốt trải nghiệm và phù hợp vận hành VN.
 - Nút thắt phổ biến: quản lý bằng Excel/Zalo/sổ tay, thu tiền thủ công, thiếu nhắc hạn, tranh chấp do hợp đồng không rõ, khó tổng hợp dòng tiền.

 ## 2.1) Nghiên cứu thị trường (đào sâu)
 ### 2.1.1) Chuỗi giá trị & người mua thực sự
 Thị trường “cho thuê nhà” có nhiều vai:
 - **Chủ tài sản (landlord)**: người quyết định hệ thống quản lý (buyer). Giá trị họ mua là **giảm thời gian + giảm thất thoát + giảm rủi ro tranh chấp**.
 - **Người thuê (tenant)**: thường không trả tiền cho PMS; họ hưởng trải nghiệm (minh bạch hoá đơn, nhận thông báo, biên nhận).
 - **Người vận hành (quản lý/thu tiền)**: là “user” chính, ảnh hưởng mạnh tới việc tiếp tục dùng hay không.
 
 Kết luận: đây là bài toán **B2SMB** (bán cho chủ trọ/chủ nhà vừa), không phải consumer app.

 ### 2.1.2) Phân khúc theo loại tài sản & quy mô vận hành
 (Cách phân khúc này giúp bạn chọn ngách có WTP cao và churn thấp)
 - **Nhà trọ phòng đơn**:
   - Đặc điểm: nhiều phòng, chu kỳ thu tiền đều, điện nước tính theo chỉ số.
   - Pain: nhắc nợ, chốt điện nước, công nợ, turnover khách.
   - WTP: tốt nhất trong nhóm cá nhân/SMB.
 - **Căn hộ dịch vụ/mini apartment**:
   - Đặc điểm: giá cao hơn, thường có dịch vụ kèm (dọn phòng, bảo trì).
   - Pain: booking/đặt cọc, lịch dọn/bảo trì, báo cáo.
   - WTP: cao, nhưng yêu cầu quy trình nhiều.
 - **Nhà nguyên căn cho thuê dài hạn**:
   - Đặc điểm: ít hợp đồng, ít kỳ thu, giá trị mỗi hợp đồng lớn.
   - Pain: hợp đồng, nhắc gia hạn/tăng giá, biên bản bàn giao.
   - WTP: trung bình; ưu tiên tính đơn giản.
 - **Môi giới/đơn vị quản lý thuê ngoài**:
   - Đặc điểm: multi-owner, cần phân quyền + đối soát.
   - Pain: báo cáo chủ nhà, tracking task, lịch thanh toán.
   - WTP: cao nhưng chu kỳ bán dài.

 ### 2.1.3) Driver nhu cầu (vì sao nhu cầu “quản lý” tăng)
 - **Tăng mật độ nhà trọ quanh KCN/ĐH**: nhiều phòng => quản lý thủ công bắt đầu “vỡ”.
 - **Chi phí thời gian**: mỗi tháng chốt điện nước + thu tiền + nhắc nợ có thể chiếm vài buổi.
 - **Minh bạch & tranh chấp**: hoá đơn/biên nhận không rõ dễ gây cãi nhau.
 - **Tăng kỳ vọng số hoá**: người thuê quen nhận hoá đơn, chuyển khoản, QR.
 
 ### 2.1.4) Hành vi hiện tại (thực tế thị trường)
 - “Stack” phổ biến nhất của chủ trọ: **Zalo + Excel + sổ tay + chuyển khoản**.
 - Lý do chưa dùng phần mềm:
   - ngại nhập dữ liệu ban đầu,
   - sợ phức tạp, sợ mất dữ liệu,
   - không tin phần mềm “có dùng được hàng ngày không”,
   - một số chủ trọ lớn đã có người thu tiền nên chưa thấy đau.
 - Hệ quả cho sản phẩm: phải thắng bằng **onboarding** (import, mẫu sẵn) và **tác vụ lõi siêu nhanh**.

 ### 2.1.5) Jobs-to-be-done (JTBD) theo chu kỳ tháng
 - **Đầu kỳ**: tạo kỳ thu, cập nhật giá/khuyến mãi/phí.
 - **Trong kỳ**: ghi nhận thanh toán, nhắc nợ, xử lý khất nợ.
 - **Chốt kỳ**: nhập chỉ số điện nước, xuất hoá đơn/biên nhận, đối soát.
 - **Ngoài chu kỳ**: khách vào/ra, gia hạn, tăng giá, hoàn cọc, bàn giao, bảo trì.

 ### 2.1.6) Ước lượng quy mô thị trường (TAM/SAM/SOM) – khung tính
 Mục tiêu phần này không phải “ra số đẹp”, mà để bạn kiểm tra: **có đủ khách trả tiền để nuôi sản phẩm không**.
 
 **Cách 1 – Bottom-up (khuyến nghị cho giai đoạn sớm)**
 - Giả sử bạn nhắm ICP-A: chủ trọ **10–200 phòng**.
 - Đặt biến:
   - `N_hp`: số chủ trọ phù hợp tại Hải Phòng.
   - `ARPA`: doanh thu bình quân/chủ trọ/tháng (ví dụ 49k–199k–499k tuỳ gói).
   - `Pen`: tỷ lệ thâm nhập thực tế 2–3 năm.
 - `SOM_hp ≈ N_hp * ARPA * Pen`
 
 Bạn có thể ước lượng `N_hp` bằng khảo sát thực địa:
 - chọn 10 phường/xã trọng điểm quanh KCN/ĐH,
 - đếm số dãy trọ (Google Maps + đi thực tế),
 - ước lượng số chủ trọ, quy mô phòng, rồi suy ra toàn thành phố.
 
 **Cách 2 – Top-down (chỉ để sanity check)**
 - `TAM_vn = số đơn vị cho thuê chuyên nghiệp/ bán chuyên * ARPA * 12`.
 - Rào cản top-down: số liệu “chủ trọ/chủ nhà có nhiều phòng” không sẵn, nên vẫn phải quay lại bottom-up.
 
 **Kỳ vọng thực tế**
 - Nếu chỉ riêng Hải Phòng bạn tìm được vài nghìn chủ trọ quy mô 10+ phòng thì thị trường địa phương đã đủ để đạt doanh thu ban đầu.
 - Nếu không đạt, bạn cần mở rộng địa lý sớm hoặc chuyển sang tệp B (đơn vị quản lý).

 ### 2.1.7) Willingness-to-pay (WTP) & ngưỡng “đủ đau để trả tiền”
 WTP thường phụ thuộc “giá trị thời gian + giảm thất thoát”. Một khung hỏi/định giá nhanh:
 - Bạn mất bao nhiêu giờ/tháng để chốt điện nước + thu tiền?
 - 1 giờ công của bạn đáng giá bao nhiêu?
 - Mỗi tháng có thất thoát/nợ xấu trung bình bao nhiêu?
 
 Ngưỡng hay gặp:
 - **1–5 căn**: chỉ trả nếu rất rẻ hoặc có tính năng “hợp đồng/nhắc hạn” cực tiện.
 - **10–50 phòng**: dễ trả nếu app giúp giảm 3–6 giờ/tháng + nhắc nợ.
 - **50–200 phòng**: có thể trả cao hơn nếu có phân quyền, báo cáo, import, export.

 ### 2.1.8) Cạnh tranh – ma trận (chọn tiêu chí để thắng)
 So sánh theo 6 tiêu chí người dùng quan tâm:
 - **Tốc độ thao tác lõi** (chốt điện nước/thu tiền)
 - **Onboarding/import**
 - **Nhắc nợ đa kênh** (in-app/Zalo/SMS)
 - **Minh bạch chứng từ** (hoá đơn/biên nhận PDF)
 - **Báo cáo & công nợ**
 - **Đa cơ sở/phân quyền**
 
 Chiến lược thắng hợp lý cho đội nhỏ:
 - Không đánh “traffic/rao vặt” ở giai đoạn đầu.
 - Thắng bằng **UX + onboarding + automation** (nhắc nợ, kỳ thu, mẫu sẵn).
 
 ### 2.1.9) Kết luận sơ bộ về thị trường
 - Nhu cầu **có thật** và lặp lại theo tháng.
 - Đối thủ lớn nhất là **Excel/Zalo**, nghĩa là bạn phải làm “nhanh hơn, chắc hơn, khỏi quên”.
 - Độ khó không nằm ở thuật toán, mà nằm ở **thói quen + triển khai + giữ chân**.

 ### 2.1.10) Giả thuyết riêng cho Hải Phòng (để bạn đi khảo sát)
 (Mục tiêu: biến “nghiên cứu thị trường” thành checklist có thể đo)
 - Giả thuyết H1: khu vực quanh **KCN** có mật độ nhà trọ cao, vận hành thiên về “thu tiền đúng ngày” và nhắc nợ.
 - Giả thuyết H2: khu vực quanh **ĐH** turnover cao (ra/vào liên tục), chủ trọ đau nhất ở khâu bàn giao, hoàn cọc, tính điện nước.
 - Giả thuyết H3: chủ trọ HP dùng **Zalo** làm kênh chính, nên thông báo/nhắc hạn nếu “Zalo-friendly” sẽ tăng giữ chân.
 - Giả thuyết H4: ngưỡng “đủ đau để trả tiền” bắt đầu từ **10+ phòng**.

 ### 2.1.11) Cạnh tranh chi tiết: PMS vs Marketplace (lý do chọn PMS)
 - Marketplace thắng ở:
   - nhu cầu người thuê lớn,
   - dễ tạo traffic nếu có vốn/đội growth.
 - Marketplace thua ở giai đoạn sớm:
   - đòi hỏi **two-sided** (cả người thuê lẫn chủ),
   - cạnh tranh trực diện với nền tảng rao vặt lớn,
   - rủi ro CAC cao.
 - PMS thắng ở:
   - bán cho **1 bên** (chủ nhà),
   - giá trị lặp lại hàng tháng => retention tốt,
   - có thể đi từ **địa phương** rồi nhân rộng.
 
 Kết luận: nếu mục tiêu là “độ khả thi” và bạn chưa có ngân sách lớn, PMS là đường đi an toàn hơn.

 ### 2.1.12) Ma trận đối thủ (khung điền khi bạn khảo sát)
 Bạn có thể chọn 5–8 đối thủ/giải pháp mà chủ trọ đang dùng và chấm theo thang 1–5:
 - **Excel/sổ tay**
 - **Zalo/nhắc lịch thủ công**
 - **Phần mềm quản lý nhà trọ A/B/C** (bạn điền tên sau)
 - **Giải pháp “kế toán/thu chi”** (nếu chủ trọ dùng)
 
 Tiêu chí chấm (đúng thứ người dùng quan tâm):
 - T1: tạo kỳ thu + ghi nhận thanh toán nhanh
 - T2: chốt điện nước nhanh + ít sai
 - T3: nhắc nợ (tuỳ biến câu chữ, lịch)
 - T4: xuất hoá đơn/biên nhận/hợp đồng
 - T5: import/export Excel
 - T6: đa cơ sở + phân quyền
 - T7: hỗ trợ triển khai (cầm tay chỉ việc)
 
 Khoảng trống phổ biến để bạn “win”:
 - T5 + T1 + T2 + T7 (triển khai tốt) thường là combo tạo chuyển đổi mạnh từ Excel.

 ### 2.1.13) Kiểm tra giá (pricing test) – cách làm nhanh, ít tốn
 Trước khi build sâu, bạn nên test 3 mức giá (anchor):
 - `P1` (entry): 49k–99k/tháng/cơ sở
 - `P2` (core): 149k–299k/tháng/cơ sở
 - `P3` (pro): 399k–699k/tháng/cơ sở (phân quyền/đa cơ sở/báo cáo)
 
 Cách hỏi để giảm “nói cho vui”:
 - “Nếu tuần sau có bản dùng được, bạn có sẵn sàng chuyển từ Excel sang không?”
 - “Bạn chọn gói nào trong 3 gói này? Nếu không chọn gói nào, lý do cụ thể là gì?”
 - “Bạn có đặt cọc/đặt lịch để mình qua setup giúp không?” (đo intent mạnh)
 
 ## 3) Khách hàng mục tiêu (ICP)
 ### ICP-A (ưu tiên MVP): Chủ nhà trọ / chủ nhà có 10–200 phòng
 - Pain points:
   - Thu tiền, nhắc nợ, chốt điện nước mỗi tháng mất thời gian.
   - Lưu hồ sơ khách rời rạc; thất lạc CCCD, tạm trú.
   - Hợp đồng thiếu mẫu chuẩn; gia hạn/tăng giá không kiểm soát.
 - Sẵn sàng trả tiền: trung bình đến cao nếu tiết kiệm thời gian và giảm thất thoát.
 
 ### ICP-B: Đơn vị quản lý nhà cho thuê (20–500 căn/phòng)
 - Pain points:
   - Cần phân quyền nhân viên, log thao tác, báo cáo chủ.
   - Chuẩn hoá quy trình bàn giao, bảo trì, kiểm kê.
 - Sẵn sàng trả: cao hơn, nhưng yêu cầu tính năng nhiều hơn.
 
 ### ICP-C: Chủ nhà cho thuê 1–5 căn
 - Pain points:
   - Quên lịch thu, quên ngày hết hợp đồng; thiếu mẫu hợp đồng.
 - Sẵn sàng trả: thấp; phù hợp gói free/low-cost.
 
 ## 4) Phân khúc bài toán & lựa chọn “điểm rơi”
 - **Quản lý vận hành (PMS)**: ít phụ thuộc marketing, giữ chân tốt, CAC thấp hơn (bán trực tiếp/giới thiệu).
 - **Đăng tin/đầy phòng (marketplace/lead gen)**: thị trường lớn nhưng cạnh tranh trực diện với các nền tảng rao vặt lớn; cần ngân sách và tăng trưởng mạng lưới.
 
 Khuyến nghị: bắt đầu bằng **PMS cho chủ nhà trọ/SMB**, sau đó mới mở rộng sang đăng tin/lead.
 
 ## 5) Đối thủ & khoảng trống
 ### Nhóm 1: Marketplace/rao vặt
 - Ưu: traffic lớn, nhu cầu thuê cao.
 - Nhược: không giải quyết vận hành sau khi đã có khách.
 - Khoảng trống: “sau khi chốt khách thì quản lý thế nào?”
 
 ### Nhóm 2: Phần mềm quản lý nhà trọ/cho thuê hiện có
 - Ưu: có tính năng quản lý cơ bản.
 - Nhược thường gặp (cơ hội): UX khó dùng, quy trình cứng, mobile yếu, thiếu tự động hoá nhắc nợ, thiếu tuỳ biến mẫu hợp đồng/biên bản.
 
 ### Nhóm 3: Tự làm bằng Excel/Zalo
 - Đối thủ thực tế lớn nhất.
 - Cơ hội: “import từ Excel”, “Zalo-first” (gửi thông báo), thao tác 1 chạm.
 
 ## 6) USP (điểm khác biệt) đề xuất
 - **Setup 15 phút**: tạo nhà/phòng, nhập khách, import Excel.
 - **Thu tiền + nhắc nợ tự động**: lịch thu, nhắc trước hạn/quá hạn qua Zalo/SMS/email (tùy gói).
 - **Chốt điện nước nhanh**: nhập chỉ số, tự tính hoá đơn, lưu lịch sử.
 - **Mẫu hợp đồng/biên bản chuẩn**: ký số ở giai đoạn sau; trước mắt là xuất PDF.
 - **Báo cáo dòng tiền theo nhà/phòng**: doanh thu, công nợ, tỉ lệ lấp đầy.
 
 ## 7) MVP đề xuất (phiên bản 0.1)
 Mục tiêu MVP: giải quyết 80% vận hành cho ICP-A.
 - Quản lý tài sản: Nhà -> Tầng -> Phòng (hoặc Nhà -> Căn).
 - Khách thuê: hồ sơ, ngày vào/ra, người ở cùng.
 - Hợp đồng: ngày bắt đầu/kết thúc, giá thuê, cọc, điều khoản cơ bản.
 - Thu tiền hàng tháng: tạo kỳ thu, trạng thái (chưa thu/đã thu/khất), ghi nhận phương thức.
 - Điện nước: chỉ số đầu/cuối, đơn giá, tự tính.
 - Nhắc hạn: nhắc thu tiền và nhắc hết hợp đồng (thông báo trong app; kênh Zalo/SMS để giai đoạn sau).
 - Xuất/in: hoá đơn và hợp đồng PDF.
 
 Not MVP (để sau): marketplace đăng tin, bản đồ, chat thuê nhà, ký số, tích hợp thanh toán đầy đủ, quản lý bảo trì nâng cao.
 
 ## 8) Go-to-market (HP trước, rồi mở rộng)
 ### Kênh bán phù hợp giai đoạn đầu
 - **Bán trực tiếp địa phương**: tiếp cận chủ trọ quanh trường đại học/KCN.
 - **Cộng tác viên**: thợ điện nước, môi giới phòng trọ, quản lý khu trọ.
 - **Nhóm Facebook/Zalo địa phương**: nội dung “mẫu hợp đồng”, “file tính tiền điện nước”, “cách nhắc nợ văn minh” kèm CTA.
 
 ### Thông điệp
 - “Giảm 3–6 giờ/tháng/nhà, hạn chế quên thu tiền, rõ ràng công nợ.”
 - “Import từ Excel trong 3 phút.”
 
 ## 9) Mô hình doanh thu (gợi ý)
 - **Freemium**: miễn phí tới X phòng (vd 5–10 phòng) + giới hạn tính năng.
 - **Subscription theo số phòng**:
   - Basic: X phòng, tính tiền + nhắc trong app.
   - Pro: không giới hạn, phân quyền, xuất PDF nâng cao.
   - Business: đa cơ sở, báo cáo nâng cao, SLA.
 - **Add-on**:
   - Zalo/SMS nhắc nợ (tính theo tin).
   - Tích hợp thanh toán/đối soát.
   - Dịch vụ nhập liệu/triển khai.

 ## 9.1) Pricing chốt (để rẻ nhất ở entry nhưng Pro đi đường dài)
 Value metric: **theo số phòng (unit/room)** + **minimum fee** theo cơ sở.
 - Free: <= 5 phòng.
 - Starter (đánh phủ): **2,000đ/phòng/tháng**, min **20,000đ/tháng**.
 - Pro (core, đi đường dài): **5,000đ/phòng/tháng**, min **99,000đ/tháng**.
 - Business: **8,000đ/phòng/tháng**, min **199,000đ/tháng**.
 - Add-on (tách biến phí): nhắc nợ qua SMS/Zalo tính theo usage/gói tin.

 Nguyên tắc nâng giá về sau:
 - Giữ Starter để luôn “rẻ nhất”.
 - Nâng Pro nhẹ (5k -> 6k hoặc min 99k -> 129k) khi đã có tính năng “đinh” (automation/tenant app/report).
 
 ## 10) Chi phí & vận hành (độ khả thi)
 - Chi phí dev/duy trì: backend + mobile/web, lưu trữ file PDF, thông báo.
 - CAC kỳ vọng thấp nếu bán địa phương tốt; LTV phụ thuộc vào churn (chủ trọ thường dùng lâu nếu dữ liệu đã nằm trong hệ thống).
 - Rào cản: thói quen Excel/Zalo, ngại nhập dữ liệu; cần “import” và “onboarding nhanh”.
 
 ## 11) Rủi ro & lưu ý pháp lý
 - Bảo mật dữ liệu cá nhân (CCCD, thông tin cư trú).
 - Trách nhiệm khi lưu trữ/đồng bộ hợp đồng; cần điều khoản dịch vụ rõ.
 - Nếu làm tính năng hỗ trợ tạm trú/khai báo: phải tuân thủ quy định và tích hợp đúng kênh.
 
 ## 12) Kế hoạch validate trong 2–4 tuần (rất quan trọng)
 ### Tuần 1: Phỏng vấn 15–25 người
 - Mục tiêu: xác nhận pain points, quy trình thu tiền, mức sẵn sàng trả.
 - Câu hỏi chốt:
   - Bạn quản lý phòng/khách/thu tiền bằng gì?
   - Mỗi tháng mất bao lâu để chốt điện nước + thu tiền?
   - Có vấn đề “quên thu/thiếu minh bạch/khó đối soát” không?
   - Nếu có app làm X, bạn trả bao nhiêu/tháng?
 
 ### Tuần 2: Prototype + test quy trình
 - Dựng prototype (Figma hoặc bản web thô) cho:
   - tạo phòng -> nhập khách -> tạo kỳ thu -> chốt điện nước -> xuất hoá đơn.
 - Test 5–8 chủ trọ, đo:
   - thời gian hoàn thành tác vụ,
   - điểm khó hiểu,
   - tính năng “must-have”.
 
 ### Tuần 3–4: Pilot trả phí nhỏ
 - Chọn 3–5 khu trọ (mỗi nơi 10–50 phòng).
 - Offer: miễn phí 1 tháng + hỗ trợ nhập liệu, sau đó thu gói thấp.
 - KPI validate:
   - 60% người pilot dùng hàng tuần,
   - ít nhất 2 người đồng ý trả tiền sau pilot,
   - churn lý do rõ ràng (thiếu tính năng gì).
 
 ## 13) Câu hỏi cần bạn chốt để mình tinh chỉnh kế hoạch
 - Bạn muốn đi hướng **PMS (quản lý vận hành)** hay **marketplace (đăng tin)** ngay từ đầu?
 - Đối tượng ưu tiên ở HP: **chủ trọ KCN**, **sinh viên**, hay **nhà nguyên căn/căn hộ**?
 - Bạn có lợi thế kênh phân phối nào? (quan hệ chủ trọ, môi giới, cộng đồng địa phương)

 ## 13.1) Roadmap theo phase (VN trước, quốc tế sau)
 - Phase 0 (2–4 tuần, pre-prod): MVP PMS thuê dài hạn + pilot trả phí nhỏ.
 - Phase 1 (0–6 tháng): VN Core PMS (Excel killer) + onboarding/import + nhắc hạn in-app + PDF/export.
 - Phase 1.5 (6–12 tháng): automation & add-on (SMS/Zalo), báo cáo nâng cao, gói Business đa cơ sở.
 - Phase 2 (12–18 tháng): serviced apartment/short-stay nhẹ (calendar, check-in/out đơn giản, housekeeping cơ bản).
 - Phase 3 (18–36 tháng): hotel PMS + OTA/channel manager (chỉ làm khi đã có đội support và traction).

 ## 13.2) Programmatic SEO (ưu tiên hiệu quả)
 Mục tiêu: tạo lead chất lượng cho buyer (chủ trọ/chủ nhà), không tạo thin content.
 - Trụ 1: Templates/Downloads (lead magnet)
   - Mẫu hợp đồng/biên bản bàn giao/thông báo tăng giá/biên nhận.
 - Trụ 2: Calculators
   - Tính điện/nước theo chỉ số, tính công nợ, lịch nhắc thu tiền.
 - Trụ 3: Segment landing (không bắn theo địa lý quá nhỏ)
   - Cho chủ trọ 10–50 phòng, 50–200 phòng, căn hộ mini.

 KPI theo dõi:
 - Visit -> lead -> trial -> paid, ưu tiên trang tạo lead.
 - Sau 30–45 ngày: giữ những cluster có lead, loại bài chỉ có view.

 ## 14) Đánh giá độ khả thi (go / no-go)
 ### 14.1) Điểm mạnh của ý tưởng (tăng khả thi)
 - Bài toán lặp lại hàng tháng => dễ tạo thói quen.
 - Dữ liệu tích luỹ (khách, công nợ, lịch sử điện nước) => rào cản chuyển đổi.
 - Bán địa phương được (HP) => không bắt buộc phải “đốt tiền” marketing như marketplace.
 
 ### 14.2) Điểm khó (giảm khả thi nếu không xử lý)
 - Onboarding/nhập dữ liệu ban đầu.
 - Chủ nhà không rành công nghệ; cần UI cực đơn giản và hỗ trợ triển khai.
 - “Nhắc nợ” liên quan trải nghiệm người thuê; phải tinh tế, có tuỳ biến.
 
 ### 14.3) Điều kiện để đi tới product-market fit
 - Bạn phải làm được 3 việc tốt hơn Excel:
   - nhanh hơn (ít thao tác hơn),
   - chắc hơn (không mất dữ liệu, dễ tìm),
   - đỡ quên (nhắc hạn tự động + báo cáo).
 - Có một kênh phân phối có thể lặp (cộng tác viên/giới thiệu/bán địa phương).
 
 ### 14.4) Phán quyết sơ bộ
 - **Khả thi** nếu bạn bắt đầu từ ngách ICP-A (10–200 phòng) ở HP, tập trung PMS, và chứng minh WTP qua pilot.
 - **Không nên** bắt đầu bằng marketplace đăng tin nếu chưa có ngân sách tăng trưởng/đội sale lớn.

 ### 14.5) Unit economics sơ bộ (để ra quyết định go/no-go)
 Mục tiêu: biết “bán có lời không” ngay cả khi chưa có số liệu đẹp.
 - Đặt biến:
   - `ARPA`: doanh thu/tháng/khách (vd 199k)
   - `GrossMargin`: biên gộp (SaaS thường cao; trừ chi phí SMS/Zalo nếu có)
   - `Churn`: tỷ lệ rời/tháng
   - `CAC`: chi phí có được 1 khách trả tiền (quảng cáo + sale + commission)
 - `LTV ≈ ARPA * GrossMargin / Churn`
 - Quy tắc go/no-go đơn giản:
   - `LTV >= 3 * CAC` (tối thiểu)
   - hoàn vốn `CAC` trong <= 3–6 tháng
 
 Gợi ý khung số cho giai đoạn HP (bán địa phương + giới thiệu):
 - Nếu `CAC` chủ yếu là công đi gặp + setup (thời gian), bạn phải tối ưu onboarding để “1 buổi setup xong”.
 - Nếu bạn phải chạy ads mạnh để có lead, PMS sẽ khó hơn marketplace; khi đó cần kênh referral/CTV.

 ### 14.6) Ngưỡng KPI để kết luận “khả thi” sau 30 ngày pilot
 - Có ít nhất **3 cơ sở** dùng thật (nhập kỳ thu + chốt điện nước).
 - Ít nhất **2 cơ sở** đồng ý trả tiền (dù là gói thấp).
 - Tỷ lệ dùng hàng tuần >= **60%** (tạo kỳ thu/ghi nhận thanh toán).
 - Lý do từ chối rõ ràng và giải quyết được bằng sản phẩm (không phải “tôi không muốn số hoá”).
