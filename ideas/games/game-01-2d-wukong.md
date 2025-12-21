# game-01-2d-wukong.md

## Tóm tắt

Game mobile dạng **2.5D action platformer**: bạn điều khiển Ngộ Không vượt “ải ngắn” theo kiểu run-based, học pattern và **đánh boss**. Mỗi run tương ứng một chuỗi “kiếp nạn” (trial) trong tinh thần **81 kiếp nạn** (không cần bám 1-1 theo nguyên tác ngay từ đầu). Người chơi chết sẽ mất run nhưng giữ **meta progression** (mở kỹ năng/đồ/ngọc/phép) để đi sâu hơn.

Điểm khác biệt: “Soulslike boss pattern” + “Roguelite build” trong format platformer 2.5D, gắn với khung **kiếp nạn** (trial rules) thay vì chỉ là map ngẫu nhiên.

Chốt hướng: **skill-based soulslike** (đòi hỏi điều khiển tốt) + **art ink brush/thuỷ mặc** + mô hình **premium mua 1 lần** (DLC là expansion trả phí).

## Mục tiêu (solo indie)

- **MVP fun**: 1 nhân vật, 1 vũ khí chính, 6-10 boss nhỏ/mini-boss, 2 boss lớn, 1 biome.
- **Chơi được ngắn**: 8-15 phút/run.
- **Skill-based**: thắng vì đọc pattern và ra quyết định build, không vì “cày số”.

## Pillars

- **Boss học pattern**: boss có 3-5 move set core, telegraph rõ, punish rõ.
- **Build có cá tính**: mỗi run người chơi chọn “pháp”/“ngọc” thay đổi nhịp combat.
- **Kiếp nạn là luật chơi**: mỗi trial thêm 1 constraint hoặc modifier (mưa lửa, trọng lực lạ, cấm hồi máu, quái phản đòn…).
- **Controls mobile-first**: ưu tiên 2-3 nút chính + context (dodge, attack, skill), tránh input phức tạp.

## Vòng lặp (Core loop)

1. Chọn loadout ban đầu (ít lựa chọn, rõ ràng).
2. Vào run: vượt 2-4 room platforming/combat ngắn.
3. Nhặt “phúc/hoạ”: chọn 1 trong 3 upgrade (trade-off).
4. Gặp boss: học pattern, quản lý stamina/chiêu.
5. Thắng: nhận currency meta + mở trial tiếp.
6. Thua: mất run, giữ meta currency, mở upgrade vĩnh viễn.

## Combat (soulslike nhưng tối giản)

- **Tài nguyên**: `stamina` (tấn công/né/skill tiêu hao) + `focus` (tích để dùng phép).
- **Khung tránh (i-frames)**: né có i-frame ngắn, cooldown nhỏ.
- **Stance/poise**: đánh đúng timing phá thế (break) để mở “window” gây sát thương lớn.
- **Heal**: giới hạn theo run (2-3 lần), có animation/commitment.

Định hướng “skill control ngon mới qua cửa”:

- Window né/đỡ **ngắn**, đòn boss có “delayed hit” để phạt panic dodge.
- Ưu tiên **readability** (telegraph rõ) thay vì spam số lượng đòn.
- Camera/độ zoom cố định, hitbox rõ để người chơi cảm thấy công bằng.

Chốt combat model: **hybrid dodge + parry (A + B)**

- **Dodge** là phòng thủ mặc định (an toàn hơn, ít reward hơn).
- **Parry** là kỹ năng rủi ro cao - thưởng cao:
  - Parry đúng timing: hồi `stamina`/tăng `focus` + tăng poise damage (dễ break boss).
  - Parry sai: ăn full damage hoặc bị stagger nhẹ (đủ để “đáng sợ” nhưng không quá ức chế).
- Boss design để hỗ trợ cả hai:
  - Mỗi phase có 1-2 đòn “parryable rõ” (spark/ink flash) và 1-2 đòn “dodge-only” (AOE/throw/grab).
  - Có 1-2 chuỗi hit với nhịp “trễ” để người chơi học thay vì spam.

Mobile input gợi ý (tối giản):

- **Attack** (tap/hold tuỳ stance)
- **Dodge** (tap)
- **Guard + Parry (đã chốt: B)**: giữ để guard, **release đúng timing** để parry
- **Skill** (tap, dùng `focus`)

Tuning gợi ý (để feel “soulslike” nhưng vẫn hợp mobile):

- Guard **giảm damage ít**, chủ yếu là “setup” cho parry; vẫn tốn `stamina` khi bị đánh.
- Parry window (release timing) rất ngắn; có thể tăng nhẹ theo meta/talent.
- Fail parry: mất `stamina` + stagger nhẹ (đủ phạt, không one-shot người mới).

## Hệ thống build (roguelite)

### Loại upgrade trong run

- **Pháp** (active): ví dụ “Hỏa Nhãn” (reveal weakpoint), “Cân Đẩu Vân” (dash dài), “Định Thân” (root ngắn).
- **Ngọc** (passive): tăng i-frame nhưng giảm damage; hồi stamina khi parry; đánh trên không mạnh hơn.
- **Di vật** (relic): thay đổi rules nhỏ nhưng mạnh (ví dụ “Gậy Như Ý” mở moveset nặng).

### Meta progression (giữ sau khi chết)

- Mở khóa pool upgrade (làm đa dạng run).
- Mở “đường tu” (talent tree nhỏ): thiên về né, parry, phép, hoặc sát thương.
- Cosmetic/collection: bestiary boss, lore fragments theo trial.

## “81 kiếp nạn” thành cấu trúc nội dung

Không cần làm 81 boss. “81” dùng làm:

- **81 trial nodes** (nhỏ) chia thành các chương.
- Mỗi chương kết thúc bằng **1 boss lớn**.
- Trong chương có: room thường, elite, mini-boss, “trial đặc biệt” (luật chơi lạ).

Đề xuất mapping nội dung:

- **Base game**: 12-18 trial nodes (1 chương) + 2 boss lớn.
- **Mỗi DLC**: thêm 1 chương (12-18 nodes) + 2 boss lớn + 3-5 mini-boss.
- Tổng dần dần tiệm cận “81” theo roadmap, không gánh từ đầu.

### Chia “81” theo tuần tự hay modular để làm DLC?

Khuyến nghị cho solo indie: **tuần tự theo “chương” (mainline) + xen kẽ “side trials” (modular)**.

- **Mainline tuần tự**: Base phát hành “Chương 1” (một lát cắt của hành trình). DLC tiếp tục “Chương 2/3/4…”.
  - Ưu điểm: cảm giác tiến trình rõ, dễ marketing (Chapter-based), dễ giữ nhịp khó tăng dần.
  - Nhược: người chơi mới vào sau có thể muốn skip.
- **Side trials modular**: trong mỗi DLC thêm một cụm “kiếp nạn ngoại truyện” (3-6 nodes) không bắt buộc theo cốt truyện.
  - Ưu điểm: bạn có chỗ để thử mechanics mới mà không phá mainline.
  - Dùng để “đổi món” mà không cần thêm nhiều cutscene/lore.

Gợi ý mapping số thứ tự (để bạn giữ cảm giác “81” mà không bị trói):

- Base: mở mốc **1–18**.
- DLC 1: mở **19–36**.
- DLC 2: mở **37–54**.
- DLC 3: mở **55–72**.
- Phần còn lại **73–81** để dành cho expansion cuối hoặc free update nhỏ tuỳ sức.

## Thiết kế boss (khung chuẩn để sản xuất nhanh)

Mỗi boss nên có:

- **Phase 1**: 3 moves cơ bản (telegraph dài).
- **Phase 2**: thêm 2 moves + 1 punish nếu người chơi spam né.
- **Enrage** (tùy chọn): tăng nhịp, không thêm mechanics mới.

Quy tắc solo-friendly:

- Ưu tiên **ít animation nhưng rõ**.
- Reuse skeleton/rig giữa boss cùng “họ”.
- Boss khác nhau bằng “modifier” (AOE, summon, delayed hit) thay vì asset hoàn toàn mới.

## Cấu trúc màn (room-based)

- 1 run = 6-10 room.
- 1 room = 20-60 giây.
- Xen kẽ: platforming nhẹ (timing) + combat nhỏ.
- “Shrine” giữa run: heal ít + chọn upgrade.

## Định vị & tham chiếu

- Gameplay gần: `Dead Cells` (roguelite platformer), `Grimvalor` (action platformer), `Ronin: The Last Samurai` (pattern/parry).
- Điểm khác: gắn hệ thống “trial rules/kiếp nạn” và boss-centric.

## Art direction

- **Ink brush/thuỷ mặc**: ưu tiên silhouette, stroke rõ, ít màu, tương phản mạnh.
- UI nên tối giản, dùng texture giấy/mực để đồng bộ.
- Boss/đòn đánh nên có “ink splash” rõ để telegraph tốt (hỗ trợ gameplay skill-based).

## Monetization

- **Premium mua 1 lần**: Base game là sản phẩm hoàn chỉnh.
- DLC là **expansion trả phí** theo chương (mỗi chương thêm biome + boss + upgrades + 1 mechanic).

## Scope breakdown (Base + DLC)

### Base Game (MVP)

- 1 biome (1 tileset, 6-10 room types).
- 1 nhân vật chơi (Ngộ Không) + 1 weapon core + 1 alternate stance.
- 2 boss lớn + 3 mini-boss.
- 15-25 upgrades trong run (pháp/ngọc/di vật).
- 1 talent tree meta (10-15 nodes).
- 1 mode chính: Run-based.

### DLC 1: “Chương 2 – Họa phong hỏa”

- 1 biome mới (modifier thiên về môi trường).
- +2 boss lớn, +3 mini-boss.
- +15 upgrades, thêm 1 phép mới.
- Thêm 1 loại trial đặc biệt (ví dụ “cấm hồi máu”, “double damage”).

### DLC 2: “Chương 3 – Tâm ma”

- Biome thiên về debuff/ảo giác (UI minimal, fake telegraph).
- +2 boss lớn, +3-5 mini-boss.
- Hệ “curse” (được mạnh hơn nhưng mang nhược điểm dài hơi trong run).

### DLC 3: “Chương 4 – Thiên đình”

- Biome thiên về aerial/combat trên không.
- +2 boss lớn, +3 mini-boss.
- Thêm 1 kiểu vũ khí phụ (staff mode khác) hoặc 1 companion ngắn hạn.

## Rủi ro & cách giảm

- **Rủi ro input mobile**: giữ control set nhỏ, ưu tiên readability hơn combo.
- **Rủi ro scope boss**: dùng boss template + reuse rig + khác nhau bằng modifiers.
- **Rủi ro roguelite “không đủ build”**: bắt đầu ít nhưng “đậm” (upgrade có trade-off), mở pool dần qua DLC.

## Câu hỏi cần chốt (để mình refine tiếp)

Đã chốt:

- Art direction: **ink brush/thuỷ mặc**.
- Monetization: **premium mua 1 lần**.
- Combat: **hybrid dodge + parry**.

- Input parry: **B** (giữ guard, release đúng timing).

- Guard: **B** (không giảm damage nhiều, chủ yếu là “setup” cho parry).