# app-01-listen-to-earn.md

## Me-App-01: Listen-to-Earn (2026)

### 1) Mục tiêu
Xây một marketplace cho attention (audio listening) nơi user được thưởng, nhưng emission bị neo theo doanh thu để hệ sinh thái bền vững và có khả năng chống gian lận.

### 2) Phạm vi
- Listen: podcast + micro-learning audio (MVP), mở rộng dần sang music/audiobook.
- Global-first.
- Reward: token (convertible về sau theo quota).

### 3) Lựa chọn thiết kế (chốt)
- Cashflow chính: advertiser/brand trả tiền cho Audio Missions / Promotions (fiat/stable).
- Convertible target: stablecoin (USDC/USDT) theo tier + quota + delayed settlement.
- Wedge MVP: podcast + micro-learning audio (có quiz để proof-of-listen).

### 4) Mô hình doanh thu
- Brand mua campaign theo:
  - CPListen (verified listen), hoặc
  - CPA (install/signup/purchase) với listen là bước đầu, hoặc
  - Hybrid (listen + quiz + click).
- Platform take-rate trên gross margin.
- Rewards pool chỉ tăng khi doanh thu tăng.

### 5) Token & Treasury (convertible về sau)
- GĐ0 (MVP): points/credits (off-chain ledger) vận hành như token.
- GĐ1: convert hạn chế sang stablecoin theo quota và KYC tier.
- GĐ2: mở token public/liquidity khi brand spend ổn định và fraud control đạt.

Emission policy:
- Daily/weekly cap theo % gross profit.
- Không trả theo “mọi phút nghe”; chỉ trả theo missions có budget + daily cap.

Token sinks tối thiểu:
- Premium: offline, transcript, AI summary.
- Boost: creator/brand boost episode/missions.
- Staking: mở hạn mức withdraw / tăng rate / ưu tiên missions payout cao.

### 6) Anti-fraud (phải làm từ ngày 1)
- Device integrity:
  - iOS DeviceCheck, Android Play Integrity.
  - Chặn/giảm quyền lợi emulator/root/jailbreak.
- Proof-of-listen:
  - Heartbeat + completion gate.
  - Random challenges tần suất thấp: tap confirm.
  - Quiz 1 câu cho micro-learning / brand story.
- Risk scoring:
  - Pattern 24/7, IP/VPN, replay, multi-account correlation.
- Settlement:
  - Rewards pending 24–72h trước khi vested.
  - Withdraw limit theo tier + reputation; high-risk bị giảm rate/blocked convert.

### 7) Roadmap 90 ngày (MVP)
- Listener app:
  - Player + feed + missions + quiz.
  - Wallet points + pending/vested.
- Brand mini-console:
  - Tạo mission + upload audio + set budget + set targeting cohort cơ bản.
  - Dashboard: verified listens, completion, quiz pass, CTR.
- Fraud v1:
  - Attestation + basic risk scoring + delayed settlement.

### 8) KPIs phải theo dõi
- Gross profit per verified hour.
- Fraud rate (farm detection + invalid rate).
- Cost per verified listen.
- D7/D30 retention (tách cohort high-risk).
- Conversion rate: listen -> quiz pass -> CTA.

### 9) Cấu hình mặc định để bền vững
Payout policy:
- Reward budget = % gross profit (đề xuất 20–40%), cập nhật theo tuần.
- Không có “APR cố định” hay “trả theo phút nghe vô hạn”.
- Daily cap theo user + cap theo mission budget.

Conversion policy (token -> stablecoin):
- Tier 0: không convert.
- Tier 1: convert nhỏ theo quota + delay 24–72h.
- Tier 2: KYC + quota cao hơn + kiểm soát rủi ro.

Geo rollout:
- GĐ MVP: mở earning toàn cầu, nhưng convert theo whitelist quốc gia.
- Ưu tiên geo có CPM/CPA cao để có gross profit tốt trước (thường US/EU), sau đó mở dần.

Rule sống còn:
- Emission chỉ tăng khi revenue tăng.
- Nếu gross profit/verified hour giảm dưới ngưỡng: giảm emission, tăng difficulty verification, giảm convert quota.

### 10) Mốc bền vững A (team gọn 3–5 người)
Target tài chính:
- Gross profit: $50k–$100k / tháng.
- Với gross margin 40%: revenue cần $125k–$250k / tháng.

Quy đổi volume (min để đạt revenue):
- Nếu price/verified mission = $0.05: cần ~2.5M–5.0M missions/tháng (~83k–167k/ngày).
- Nếu price/verified mission = $0.03: cần ~4.2M–8.3M missions/tháng (~139k–278k/ngày).

Quy đổi MAU (ví dụ):
- MAU 500k, trung bình 0.3 missions/user/day, verified completion 60% => ~2.7M missions/tháng.
- MAU 1.0M, trung bình 0.2 missions/user/day, verified completion 60% => ~3.6M missions/tháng.