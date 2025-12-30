#!/usr/bin/env python3

# Opp 04 – TON “GPU Mining” (Cocoon / Confidential Compute on TON)

## 1. Links & tham chiếu

- **Cocoon (official):** https://cocoon.org/
- **GPU Owners (yêu cầu phần cứng + quick start worker):** https://cocoon.org/gpu-owners
- **Developers (lộ trình client/SDK):** https://cocoon.org/developers
- **Smart contracts (payment flow, stake, close delay):** https://cocoon.org/docs/smart-contracts
- **Thông báo network live (Pavel Durov):** https://x.com/durov/status/1995208789600182391

## 2. Tóm tắt nhanh (tính đến hiện tại)

- “GPU mining TON” trong bối cảnh Cocoon thực chất là **cung cấp GPU để chạy AI inference** (tác vụ có ích), và **được trả bằng TON** theo lượng request/token đã xử lý.
- Cocoon nhấn mạnh **confidential computing**: workload chạy trong môi trường được attest, nhà cung cấp GPU **không đọc được** input/output và model theo thiết kế.
- Network đã **live** và đã có “first AI requests”, “GPU owners already earning TON” theo thông báo công khai của Pavel Durov.

## 3. Cơ hội: đáng để làm không?

### 3.1. “Thắng” ở đâu

- **Nếu bạn đã có hạ tầng datacenter phù hợp** (Intel TDX + GPU đời mới hỗ trợ confidential computing), Cocoon là một kênh monetize thêm cho GPU khi nhàn rỗi.
- **Demand engine từ Telegram** (kỳ vọng): nếu Telegram đưa các AI feature vào hệ sinh thái (Mini Apps / client), nhu cầu inference có thể tăng nhanh.

### 3.2. “Thua” ở đâu (điểm chặn lớn nhất)

- Rào cản vào mạng **cực cao về phần cứng**: docs hiện nêu NVIDIA GPU cần CC support **H100+** + Intel **TDX-capable CPU** + kernel/QEMU đủ mới.
- Đây là kiểu bài “ai đã có H100/colo sẵn thì thử được”; còn bài “lấy 1–2 GPU consumer (3090/4090) cắm máy nhà” thì **không fit** theo yêu cầu hiện tại.

## 4. Cần gì để tham gia làm GPU owner (theo docs hiện tại)

### 4.1. Phần cứng / hệ điều hành

- **Linux server** (docs nêu kernel **6.16+** để hỗ trợ TDX đầy đủ).
- **CPU Intel hỗ trợ TDX** (bật TDX trong BIOS/firmware).
- **NVIDIA GPU có Confidential Computing support** (docs nêu **H100+**); có thể cần **update VBIOS** để attestation hoạt động đúng.
- **QEMU có TDX support** (docs nêu **10.1+**).

### 4.2. Thành phần vận hành worker

- Tải “worker distribution” từ CI và chạy worker bằng script `cocoon-launch`.
- Chạy **seal-server** (được mô tả là required cho production) trước khi start worker.
- Chuẩn bị `worker.conf` (INI) với các trường tối thiểu:
  - `model` (model để serve)
  - `owner_address` (địa chỉ ví TON nhận tiền)
  - `gpu` (PCI address GPU)
  - `node_wallet_key` (private key revenue wallet, base64)
  - `hf_token` (Hugging Face token để pull model)
  - `ton_config` (TON liteserver config)
  - `root_contract_address` (địa chỉ root contract Cocoon trên TON)

## 5. Tiền về như nào (hiểu cơ bản)

- Cocoon dùng smart contracts trên TON để:
  - **Client trả tiền** vào proxy contract
  - **Proxy trả worker** vào worker contract
  - Worker/owner **withdraw earnings** về owner wallet
- Có khái niệm **stake** và **close delay** khi proxy down (đọc kỹ để hiểu rủi ro vốn bị “đóng băng” theo thời gian chờ).

## 6. Nên “xài” ngay hay chờ?

### 6.1. Khi nào nên làm ngay

- Bạn đã có (hoặc thuê được) **server TDX + H100+** với chi phí hợp lý.
- Bạn chịu được:
  - Setup hạ tầng phức tạp (TDX, VFIO passthrough, attestation)
  - Biến động doanh thu theo demand
  - Rủi ro vận hành (downtime ảnh hưởng uy tín/payout)

### 6.2. Khi nào nên chờ

- Bạn chỉ có **GPU consumer** hoặc server không có **TDX**.
- Bạn muốn “plug-and-play” (ít ops) → hiện dev docs còn nói “sắp có Docker-based client” và “lightweight client library” (tức onboarding phía demand và tooling vẫn đang hoàn thiện).

## 7. Chờ gì (những mốc đáng theo dõi)

- **Nới phần cứng hỗ trợ**: nếu Cocoon mở rộng ra các GPU phổ biến hơn (không chỉ H100+), cơ hội retail sẽ tốt hơn rất nhiều.
- **Maturity của tooling**:
  - Docker-based deployment cho client/dev (để tăng demand).
  - Library nhẹ cho mobile/desktop integration.
- **Số liệu utilization thực** (GPU-hours / request volume / payout stability) và cơ chế pricing đủ “market-driven” để ước lượng ROI.
- **Governance / rủi ro protocol**: hiện docs smart contracts có nói governance đang centralized; cần theo dõi lộ trình phi tập trung hoá.

## 8. Checklist hành động (nếu muốn thử trong 1–2 tuần)

- Chốt bài toán: mục tiêu là **validate utilization + payout** (không phải “mining hash”).
- Thuê/chuẩn bị server đúng chuẩn (TDX + H100+), set monitoring (GPU util, errors, network).
- Start ở test mode trước, rồi chuyển production (seal-server).
- Ghi nhận: TON/day, uptime, cost/day (server + điện + bandwidth + ops) → ra quyết định scale.

## 9. Rủi ro & mô hình ROI (ước lượng theo kịch bản)

### 9.1. Rủi ro chính (ảnh hưởng trực tiếp ROI)

- **Rủi ro demand/utilization:** doanh thu phụ thuộc số job thật sự chạy; util thấp là chết ROI.
- **Rủi ro pricing:** giá market có thể bị kéo xuống nhanh nếu nguồn cung H100+ tăng.
- **Rủi ro phần cứng/khấu hao:** H100+ capex lớn, tốc độ mất giá cao; downtime = mất doanh thu.
- **Rủi ro vận hành/attestation:** TDX/VFIO/driver/VBIOS là mảng dễ “đau” (mất nhiều giờ ops).
- **Rủi ro governance/protocol:** governance hiện mang tính centralized; thay đổi config/allowed images/models có thể ảnh hưởng người chạy node.
- **Rủi ro khóa/ví:** `node_wallet_key` là private key; rò rỉ là mất tiền.

### 9.2. Khung tính (để bạn tự plug số thực tế)

- **Doanh thu/ngày (USD):** `R = rate_usd_per_gpu_hr * 24 * utilization`
- **Chi phí/ngày (USD):** `C = power_cost + colocation + bandwidth + ops_reserve`
- **Lợi nhuận/ngày:** `P = R - C`
- **Payback (ngày):** `payback_days = capex / P` (chỉ có ý nghĩa khi `P > 0`)

Gợi ý lấy `rate_usd_per_gpu_hr` để tham chiếu:

- Thị trường cloud rental H100 80GB on-demand cuối 2025 dao động rất rộng, có nơi ~`$1.9–$7+/GPU-hr` tuỳ provider (marketplace thường rẻ hơn hyperscaler).
- Giá mua H100 80GB thường được nhắc ở mức `~$30k–$40k+`/GPU tuỳ biến thể và nguồn cung.

### 9.3. 3 kịch bản minh hoạ (1× H100)

Assumption minh hoạ (đổi theo thực tế của bạn):

- `capex = $45,000` (GPU + server + linh kiện)
- `C ≈ $12/day` (điện + colo + misc; tùy location)

Kịch bản:

- **Bear:** `rate=$1.5/h`, `util=20%` → `R=$7.2/day`, `P≈ -$4.8/day` → không hoàn vốn
- **Base:** `rate=$3.0/h`, `util=40%` → `R=$28.8/day`, `P≈ $16.8/day` → payback ~`2,679 ngày` (~7.3 năm)
- **Bull:** `rate=$5.0/h`, `util=70%` → `R=$84/day`, `P≈ $72/day` → payback ~`625 ngày` (~1.7 năm)

Điểm mấu chốt:

- ROI nhạy nhất với **utilization** và **rate**.
- Nếu bạn đã có sẵn H100 (sunk cost), bài toán chuyển thành “P > 0 không?” và “P đủ bù rủi ro ops không?”.
- Nếu bạn phải mua mới chỉ để chạy Cocoon thì cần đo **TON/day thực tế** trước khi scale.

## 10. Kaggle “free GPU” có tận dụng để kiếm TON được không?

- Để làm **GPU owner** cho Cocoon thì hiện yêu cầu **Intel TDX + NVIDIA H100+** và setup TDX/VFIO/attestation. GPU Kaggle thường là GPU phổ thông (ví dụ P100/T4 tùy thời điểm) và môi trường notebook không cho bạn quyền hạ tầng để chạy TDX guest + passthrough theo kiểu đó, nên **không dùng Kaggle để chạy worker kiếm TON** được.
- Kaggle cũng chống lạm dụng tài nguyên cho “cryptocurrency mining”; nền tảng này hướng tới học tập/ML notebook chứ không phải chạy worker kiếm coin.
- Kaggle có thể hữu ích ở hướng khác: **viết và test code client/app** (phía người dùng/developer) khi Cocoon cung cấp thư viện/SDK phù hợp, nhưng đây là phía **tiêu TON để gọi inference**, không phải phía “đào”.

## 11. Khi nào có “thông tin tiếp theo” (dự trù)

- Hiện **không thấy công bố một ngày cố định** cho đợt thông tin tiếp theo trên các kênh chính thức.
- Thông điệp chính thức đang ở dạng “rolling update”:
  - Pavel Durov nói “over the next few weeks” sẽ onboard thêm GPU supply và developer demand.
  - Kênh Telegram của Cocoon cũng kêu gọi dev/GPU owners nhắn DM để onboard.
- Vì vậy, kỳ vọng hợp lý là **update theo tuần** (worker release mới, mở rộng model/hardware, thay đổi pricing/contract params), chứ không phải 1 mốc ngày cụ thể.

Gợi ý tracking nội bộ (đỡ miss):

- Check mỗi **thứ 2**:
  - Post mới trên kênh Cocoon Telegram: https://t.me/s/cocoon?before=13
  - Update/release/commit trên GitHub: https://github.com/TelegramMessenger/cocoon
  - Update docs chính thức: https://cocoon.org/

## 12. Nội bộ – đoạn tóm tắt gửi team (copy/paste)

Cocoon (TON) đã live và trả TON cho GPU owners, nhưng hiện “GPU mining” thực chất là chạy AI inference trong confidential computing. Rào cản lớn nhất là phần cứng: yêu cầu Intel TDX + NVIDIA H100+ (consumer GPU không fit). ROI nhạy cực mạnh với utilization và rate; nếu mua mới chỉ để chạy Cocoon thì cần pilot đo TON/day trước khi scale. Hiện chưa có lịch “ngày X” cho update tiếp theo; kênh chính thức nói sẽ scale “trong vài tuần tới”, nên tracking theo tuần qua Telegram channel Cocoon + GitHub + cocoon.org.
