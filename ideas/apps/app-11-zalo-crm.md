# Zalo CRM

## Định vị
- “Zendesk/Intercom-lite cho Zalo OA” dành cho SME: shared inbox + ticket + SLA + CRM nhẹ.
- Mục tiêu: biến Zalo từ kênh chat cá nhân → kênh vận hành có quy trình (phân công, SLA, đo lường, bàn giao ca).

## Ngành/vertical dễ ra tiền nhất (khuyến nghị)
### 1) Điện máy / bảo hành / sửa chữa / lắp đặt (dễ nhất để chốt)
- Volume cao, nhiều tình huống follow-up (hẹn kỹ thuật, đổi trả, bảo hành).
- “Chi phí lỗi” cao: bỏ sót inbox = mất đơn + bùng khiếu nại.
- ROI đo được ngay: giảm trễ phản hồi, giảm missed appointment, giảm ticket tồn.
- Dễ bán qua: đại lý/chuỗi nhỏ + đội kỹ thuật + agency chạy Zalo Ads.

### 2) Trung tâm giáo dục (tư vấn tuyển sinh + chăm sóc học viên)
- Lead vào Zalo nhiều, cần pipeline + nhắc lịch + đo chất lượng tư vấn.
- Pain rõ: nhiều tư vấn viên, dễ thất thoát lead, không có chuẩn kịch bản.

## ICP (khách hàng mục tiêu)
- SME bán lẻ/điện máy/giáo dục/du lịch; inbound qua Zalo; đội sales/CSKH 3–50 người.
- Có 1 Zalo OA đang chạy ads hoặc có lượng inbox tự nhiên cao.
- Trigger mua: inbox tăng, quản lý không kiểm được chất lượng, khách phàn nàn chậm.

## Buyer / Champion
- Buyer: chủ doanh nghiệp/COO/Head of CSKH/Sales Manager.
- Champion: team lead CSKH (đau vì không kiểm được nhân sự & không bàn giao được).

## Pain (vấn đề hiện tại)
- Chat phân mảnh, nhân viên dùng Zalo cá nhân/thiết bị chung.
- Mất lịch sử, không audit được ai xử lý.
- Không đo được SLA (first response / resolution), backlog “mù”.
- Không có pipeline/nhắc việc, follow-up rơi rớt.

## Wedge (MVP bán được bằng demo)
- Shared inbox Zalo OA.
- Ticket từ hội thoại.
- Phân công + tag + SLA.
- Báo cáo realtime + export.

## Use-cases ưu tiên
- CSKH sau bán: bảo hành/đổi trả/sửa chữa/đặt lịch.
- Tư vấn trước bán: hỏi giá/kiểm tồn/đặt cọc.
- Khiếu nại/đòi bồi hoàn cần theo SLA.

## Core modules
### Inbox & routing
- Shared inbox theo OA.
- Assignment: manual + round-robin + theo tag.
- Trạng thái: open/pending/closed.
- Tag, priority.

### Ticketing
- Ticket từ hội thoại + form/webhook.
- SLA policy: first response, next response, resolution (theo tag/team/giờ làm việc).
- Internal note, @mention, file.

### Mini-CRM
- Contact profile (tên/điện thoại/Zalo ID), custom fields.
- Timeline hội thoại + ticket.
- Pipeline đơn giản (lead → won/lost) hoặc lifecycle.

### Automation (gói Pro)
- Auto-tag/auto-assign theo keyword, menu, nguồn campaign, giờ làm việc.
- SLA breach alert.
- Macro/canned reply.

### Reporting
- SLA attainment, backlog, agent performance, tag volume, peak hours.
- Export CSV.

## Workflow chuẩn
### As-is
- Inbound → nhân viên tự nhảy vào trả lời → không phân công, không bàn giao, không SLA.

### To-be
- Inbound Zalo OA → auto-tag/assign → agent xử lý → tạo ticket nếu cần follow-up.
- Escalate → close → CSAT (tuỳ) → broadcast/bán lại.

## Tích hợp
- Zalo OA API (bắt buộc): nhận/gửi tin nhắn, menu.
- ZNS (tuỳ giai đoạn): thông báo trạng thái ticket/đặt lịch.
- Webhook/Google Sheet/CRM: đồng bộ contact + ticket.
- Call center (add-on): click-to-call + log call.
- POS/ERP (sau wedge): tra đơn hàng/bảo hành/tồn.

## Data model tối thiểu
- Tenant
- Channel (Zalo OA)
- User/Agent, Team, Role
- Contact, ContactAttribute
- Conversation, Message
- Ticket, TicketStatusHistory, SLAPolicy
- Tag
- AutomationRule
- Macro
- EventLog

## MVP 4–6 tuần (scope chặt)
- Shared inbox + phân công + tag + search.
- Ticket create/assign/close.
- SLA 1 cấp + cảnh báo quá hạn.
- Contact profile + timeline.
- 6 report lõi: volume theo tag, backlog, SLA attainment, first response time, resolution time, agent leaderboard.
- Import/export CSV + phân quyền cơ bản.

## Pricing gợi ý
- Starter: gói cố định 3–5 agents.
- Pro: theo agent + SLA nâng cao + automation.
- Add-on: ZNS, call center, multi-OA, integration pack, onboarding.

## Metrics
- % ticket đúng SLA.
- First response time (P50/P90).
- Resolution time.
- Backlog theo ngày.
- Reopen rate.
- CSAT (tuỳ).

## GTM (thử nghiệm 14 ngày)
- 10 interview (điện máy/bảo hành + giáo dục + 1 ngành phụ) để chốt workflow.
- 3 pilot trả phí nhẹ (2–5 triệu/tháng) kèm cam kết KPI: giảm first response 30–50%.
- Kênh:
  - Agency chạy Zalo Ads.
  - Đơn vị triển khai CRM.
  - Cộng đồng chủ shop/chuỗi điện máy nhỏ, đội kỹ thuật.

## Roadmap 6–12 tháng
- Q1: Zalo-first inbox + ticket + SLA + report.
- Q2: automation nâng cao + multi-OA + survey.
- Q3: call center integration + knowledge base/macro library theo ngành.
- Q4: omnichannel (nếu cần) + benchmark theo ngành.

## Rủi ro
- Phụ thuộc policy/API của Zalo.
- Cạnh tranh mạnh từ CRM/inbox tools.
- Khách đòi tích hợp sớm.

## Moat
- Template workflow + macro + automation theo ngành.
- Benchmark SLA/CSAT theo ngành (ẩn danh) để upsell.