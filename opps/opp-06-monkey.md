#!/usr/bin/env python3

# Opp 06 – Flip 2 Earn Monkeys (Telegram Mini App)

## 1. Links & Tham chiếu

- **Telegram channel (client/product):** https://t.me/MonkeyPlayOfficial
- **Phaser news/examples (game engine):** https://phaser.io/news/category/game
- **Rive (animation tool):** https://rive.app/
- **Game juice spec (WHAT/WHY):**
  - Document: *Flip 2 Earn Monkeys - Game Juice Requirements v2.0 (WHAT/WHY)*
  - Editor video: `Monkeys_edited_compressed.mp4`
  - Phân tích chi tiết: `edited_analysis.md`, `analysis.json`, `game-juice-improvement-plan.md`

## 2. Tổng quan sản phẩm & mục tiêu

- **Game type:** Coin-Flip mechanic, Telegram Mini App.
- **Hiện tại:** Game đã chạy, nhưng "flat", win không phê, không có cảm giác progression, thiếu juice.
- **Target:** Nâng cảm giác từ ~4/10 lên ~8/10 về "juice/polish".
- **Triết lý:**
  - Khách **own WHAT/WHY** (feature nào, vì sao quan trọng, trải nghiệm mong muốn).
  - Bên mình **own HOW** (giải pháp kỹ thuật, implement trên stack TMA).

Các cảm xúc cần đạt:

- Anticipation trước mỗi lần lật coin.
- Satisfaction khi coin match.
- Excitement build up theo streak.
- Euphoria khi total win / cashout.
- Loss phải cảm thấy fair, không bị punish.

## 3. Scope chính bên mình (juice, không đụng core rules)

- Không thay đổi core mechanic / toán học thắng thua.
- Tập trung **FEEL**:
  - Screen shake, particle, flash, burst.
  - Animation coin flip (anticipation, reveal pop).
  - Win celebration over-the-top.
  - Progressive escalation theo streak & multiplier.
  - Haptics + layered audio + button feedback.
- Tối ưu để chạy mượt trong **Telegram Mini App** với giới hạn asset & performance.

## 4. Tech stack đề xuất

- **Nền tảng:** Telegram Mini App (Web, chạy trong Telegram).

- **Game/Render:**
  - **Phaser 3** (web game engine) – phù hợp mini-game TMA:
    - Hỗ trợ sprite, tween, particle, camera shake.
    - Nhẹ, quen thuộc, nhiều ví dụ gambling-style.

- **Animation nhân vật / motion phức tạp:**
  - **Rive** (optional, nếu khách invest asset):
    - Monkey character: idle, victory pose, reaction khi big win.
    - Một số motion mượt (pose chuyển trạng thái, biểu cảm).
  - Nếu cần tối giản size: có thể dùng sprite sheet + tween thay cho Rive.

- **Âm thanh:**
  - Web Audio API (hoặc Phaser sound) cho layered audio, pitch theo streak.
  - Tổng dung lượng SFX < **500KB** (theo constraint TMA).

- **Haptics:**
  - Telegram WebApp HapticFeedback API:
    - `impactOccurred('light' | 'medium' | 'heavy')`.
    - `notificationOccurred('success' | 'error')`.
  - Wrap thành `HapticsManager` để map event → pattern.

- **Cấu trúc code:**
  - `GameState` (streak, multiplier, balance, trạng thái coin).
  - `EventBus` (emit các event game → FX, audio, haptics).
  - `FXManager` (particle, radial burst, flash overlay, connection lines).
  - `ScreenShakeManager` (camera / container shake theo intensity).
  - `HapticsManager` (wrapper TMA): tap, reveal, multiplierUp, bigWin, loss.
  - `AudioManager` (preload, layered SFX, pitch scaling theo streak).
  - `EscalationManager` (map streak → level 1–5 → scale intensity).
  - `SettingsManager` (on/off sound, haptics, FX; đọc từ config).
  - `gameJuiceConfig` (JSON/TS): toàn bộ timing, intensity, particle count.

## 5. Các nhóm feature (theo Priority của khách)

### 5.1 Priority 1 – MUST HAVE (khoảng 70% impact)

1. **Physical Impact Feedback (Haptics)**
   - Mọi moment quan trọng đều có rung:
     - Coin selection → light tap.
     - Coin reveal → quick pulse.
     - Multiplier increase → mạnh hơn.
     - Big win → pattern dài, cảm giác win lớn.
     - Loss → single error buzz.
   - Implement qua `HapticsManager` map từ event → TMA haptics.

2. **Screen Shake**
   - Shake cả game board, intensity theo event:
     - Coin reveal match: subtle, 150ms.
     - Multiplier up: medium, 200ms.
     - Streak continue: strong, 250ms.
     - Total win: intense, ~600ms "earthquake".
   - Không shake khi **loss** để reinforce: gold = good (impact), red = bad (contained).

3. **Coin Flip Anticipation**
   - Flow:
     - Tap coin → bắt đầu spin.
     - Spin ~300ms.
     - Pause ~100ms ở peak tension.
     - Reveal instant + pop (scale, sparkle, haptic, sound, shake nếu win).

4. **Explosive Win Celebration**
   - Trigger khi total win / cashout.
   - Sequence ~2s:
     - Pause ngắn sau final coin.
     - Gold flash full-screen.
     - Monkey/character victory pose.
     - Coin burst khắp màn hình.
     - Win amount count-up nhanh.
     - Strong shake + triumphant sound.
   - Có thể cho **tap to skip** để không làm người chơi khó chịu.

### 5.2 Priority 2 – SHOULD HAVE (khoảng 25% impact)

5. **Progressive Escalation System**
   - Streak càng dài → mọi thứ càng mạnh:
     - Shake amplitude tăng.
     - Particle nhiều hơn.
     - Audio pitch cao dần.
     - Visual flash xuất hiện ở streak cao.
   - `EscalationManager` map streak → level 1–5, scale toàn bộ effect qua config.

6. **Radial Burst (Big moments)**
   - Sunburst particle từ center khi multiplier tăng / streak continue.
   - 360°, 40+ particles, 500ms, màu gold/yellow.

7. **Multiplier Emphasis**
   - Multiplier là trung tâm: khi tăng thì lớn lên, glow, micro-shake, haptic.
   - Intensity tăng dần khi multiplier càng cao.

8. **Layered Audio Feedback**
   - Base + layers + pitch shift theo state:
     - Flip: whoosh.
     - Match: pop.
     - Multiplier up: pop + chime (+10% pitch).
     - Streak 2–3+: thêm ding, pitch +20–30%.
     - Total win: fanfare + tất cả layers.
   - Dùng Web Audio / Phaser sound, đảm bảo tổng SFX < 500KB.

### 5.3 Priority 3 – NICE TO HAVE (khoảng 5% impact)

9. **Visual Connection Lines**
   - Đường line vàng nối các coin match, pulse ~300ms rồi fade.

10. **Loss State Clarity**
    - Loss: reveal nhanh, particle đỏ/tối, error haptic.
    - Không shake, không flash lớn, clear sớm → cảm giác fair, không punish.

11. **Button Press Feedback**
    - Tất cả button (coin, flip, cashout, menu):
      - Scale down nhẹ khi press.
      - Glow/brighten + light haptic.
      - Spring back nhanh (<100ms).

## 6. Constraints & yêu cầu performance (TMA)

- FPS: **45+** trên Android mid-tier.
- Load time: < **2s**.
- Touch latency: < **16ms**.
- Asset:
  - Audio tổng < **500KB**.
  - Hình ảnh < **1MB**.
- Không dùng lib nặng.
- Ưu tiên API native của Telegram (haptics, WebApp integration).

## 7. Ước lượng effort & timeline

Giả định:

- Core game logic (flip, thắng/thua, multiplier, balance) **đã hoạt động**.
- Mình tập trung implement juice + polish layer, không viết lại core.

### Phase 1 – Core Juice (Week 1)

- Xây hệ thống:
  - EventBus, FXManager, ScreenShakeManager, HapticsManager, AudioManager.
  - `gameJuiceConfig` cho timing/intensity.
- Implement:
  - Coin flip anticipation (spin + pause + reveal pop).
  - Screen shake các mức theo event.
  - Particle cơ bản: sparkles, radial burst.
  - Win celebration sequence ~2s (flash, coin burst, shake, count-up).
- 1–2 vòng tuning cảm giác.

**Ước lượng:** ~ **4–6 ngày dev** (mid level, full-time).

### Phase 2 – Enhancement (Week 2)

- Implement:
  - Progressive escalation theo streak.
  - Multiplier emphasis (scale, glow, micro-shake).
  - Layered audio (preload, pitch theo streak).
  - Full haptics mapping theo event.
  - Loss treatment, button feedback.
- Tối ưu perf, test multi-device, setting on/off.

**Ước lượng:** ~ **3–5 ngày dev** + **2–3 ngày design/anim** (asset, Rive, polish).

### Tổng quan thời gian

- Dev: **~7–11 man-day**.
- Design/anim: **~2–3 man-day**.
- Calendar realistic: **1–2 tuần** (tùy feedback vòng lặp với khách).

## 8. Ước lượng cost & giá đề xuất (VN)

> Lưu ý: đây là khung ước lượng để bàn nội bộ, không phải báo giá final.

Giả sử cost nội bộ (ví dụ):

- Dev mid: **1.5–2.5M VND/ngày**.
- Designer/anim part-time: **0.8–1.5M VND/ngày**.

Cost thô (không overhead/margin):

- Dev: 8–10 ngày × 1.5–2.5M ≈ **12–25M**.
- Design: 2–3 ngày × 0.8–1.5M ≈ **1.6–4.5M**.
- Tổng cost nội bộ khoảng **14–30M**.

Thêm overhead (PM, QA, vòng feedback, thuế) + margin tối thiểu **30–50%**:

- **Floor (rất rẻ, khách thân, lấy case):** ~ **30–40M VND**.
  - Rủi ro: ít buffer cho vòng chỉnh nhiều.
- **Mức hợp lý (khuyến nghị):** ~ **40–50/60M VND**.
  - Cho phép thêm 2–3 vòng tune effect, A/B small, test đa thiết bị.
- **Nếu khách brand / cần A/B, analytics sâu:** có thể **>60M**.

**Khuyến nghị:**

- Không nên xuống dưới **~30M** cho full scope juice như spec v2.0.
- Sweet spot hiện tại: **~40–50M VND cho 1–2 tuần**, deliver cảm giác premium trong giới hạn TMA.

## 9. Acceptance Criteria tóm tắt

- **Screen Shake:**
  - Intensity khác nhau theo event, config được, không drop FPS.
  - Off được trong settings.

- **Coin Flip Animation:**
  - Có anticipation pause rõ, reveal pop satisfying.
  - Chạy mượt với rapid flips, không lag consecutive.

- **Win Celebration:**
  - Sequence ~2s, cảm giác "overwhelming" positive.
  - Đủ rõ trên màn hình nhỏ, có thể skip.

- **Progressive Escalation:**
  - Người chơi cảm nhận rõ khác biệt flip 1 → flip 5.
  - Reset khi loss, không gây khó chịu ở max.

- **Haptic Feedback:**
  - Chạy được trong Telegram app.
  - Intensity match visual/audio, respect system setting.

## 10. Next steps nội bộ

- Confirm với khách:
  - Stack (Phaser + optional Rive) có OK không.
  - Phạm vi: Priority 1 + 2 là must trong batch này, Priority 3 nếu còn budget/time.
  - Budget range đề xuất.
- Sau khi chốt:
  - Viết technical plan chi tiết cho dev (module breakdown, interface).
  - Chuẩn bị skeleton project TMA + Phaser.
  - Thực hiện Phase 1 → review với khách → Phase 2.

