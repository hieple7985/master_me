# Opp 05 – TON “New Crypto Staking”

Tên gợi ý (≤3 từ): **Launchpool Carry**

Kết luận hiện tại: **bỏ qua nếu chỉ chơi ngắn hạn**; chỉ revisit khi có điều kiện hedge rẻ + pool ổn định.

## 1) Kèo đang nói tới là gì? (theo screenshot)

Đúng format của **Gate Launchpool**:

- **Snapshot theo giờ** (platform chụp nhiều lần mỗi giờ và lấy trung bình).
- **Trả thưởng theo giờ** vào spot.
- APR hiển thị là **ước tính** dựa trên reward/hour và giá (tham chiếu FAQ).

Tham chiếu:
- Launchpool FAQ (cách snapshot/tính reward/APR): https://www.gate.com/help/guide/startup/37021/gate.io-launchpool-faq
- Launchpool page: https://www.gate.com/launchpool

## 2) Ví dụ cụ thể từ screenshot

- Reward token: **WET**
- Tổng reward hiển thị: **375,000 WET**
- Có 2 kiểu “Per …” (pool theo tài sản stake): **Per GUSD** và **Per WET**
  - “Per GUSD” nghĩa là stake GUSD để nhận WET.
  - “Per WET” nghĩa là stake WET để nhận WET.

Lưu ý: APR cực cao kiểu 400%+ thường là do:
- Total staked ở pool còn nhỏ trong một vài giờ đầu, hoặc
- Giá reward token biến động mạnh, hoặc
- APR là annualize từ 1h gần nhất (noise rất lớn).

## 3) Dự trù “delta-neutral hedging + stake” (khung triển khai)

### 3.1. Biến thể A (đơn giản, thường hợp với Launchpool)

- Vốn chính: **stablecoin stake** (ví dụ GUSD) để farm airdrop token mới.
- Delta-neutral phần “reward token” (nếu muốn):
  - Chỉ thực sự hedge được khi token có **perp/futures** và đủ thanh khoản.
  - Khi đã có perp: có thể **short** reward token theo lượng reward dự kiến/nhận được để khoá biến động giá.

Điểm mạnh:
- Principal gần như stable (trừ rủi ro sàn/custody).

Điểm yếu:
- Thường không hedge được “từ phút 0” (chưa có perp).

### 3.2. Biến thể B (classic delta-neutral carry)

- Long spot (hoặc hold tài sản stake) + short perp cùng tài sản để neutral giá.
- Thu lợi từ:
  - staking/earn APR,
  - funding rate (nếu funding dương theo hướng có lợi),
  - airdrop/points (nếu chương trình tính theo spot balance).

Điểm choke:
- Nếu staking yêu cầu lock spot nhưng short perp cần margin, sẽ bị “kẹt vốn” và rủi ro liquidation.

## 4) Cách tính & thứ cần theo dõi (để biết còn “alpha” hay không)

- **Reward/hour** (Gate phân phối theo giờ; công thức tính theo share của bạn).
- **Total staked** trong pool (tăng nhanh thì APR thường tụt).
- **Hard cap** theo giờ cho cá nhân (nếu có) → stake thêm không tăng reward.
- **Điều kiện eligibility**: một số launchpool có yêu cầu trading volume/KYC; không đạt có thể không nhận reward.
- **Chi phí hedge** (funding + fee + slippage) nếu bạn short để neutral.

## 5) Rủi ro chính (đừng bỏ qua)

- **Custody/CEX risk**: stake trên sàn = rủi ro đối tác.
- **Rule risk**: điều kiện volume/KYC/cap có thể thay đổi theo từng pool.
- **APR illusion**: annualize từ 1h/day gần nhất nên rất nhiễu.
- **Reward token dump**: token unlock ngay, nhận reward xong nhiều người bán.
