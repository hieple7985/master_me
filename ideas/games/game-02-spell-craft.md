# game-02-spell-craft.md

## Tóm tắt

Game mobile **màn hình dọc** dạng **PvE lane / tower defense lai hero-control**.

Mỗi màn người chơi điều khiển **2–4 hero** (sống sót tới hết wave / hạ boss wave). Quái chết rơi **nguyên tố** (Hỏa, Thủy, Mộc, Kim, Thổ… + Light/Dark về sau). Hero **nhặt nguyên tố** để **craft spell ngay trong trận** theo “công thức” (người chơi tự khám phá hoặc suy luận).

Mỗi hero giữ tối đa **3–4 spell** (loadout trong màn), nâng cấp hero tối đa **level 10 trong trận**. Qua màn sẽ **reset level + spell**, nhưng giữ **meta progression** (mở hero, mở rune/công thức, nâng bench, sổ tay tri thức…).

Trọng tâm: cảm giác “tự sáng chế” build, nhưng vẫn có **logic rõ** để học dần và khoe build.

## Player fantasy

- Vừa là chỉ huy (đặt hero đúng lane, dùng skill đúng nhịp), vừa là “phù thủy” (ghép nguyên tố ra phép).
- Thấy mình **giỏi dần**: hiểu công thức nhanh hơn, tối ưu drop, chọn trade-off tốt hơn.

## Pillars

- **Craft trong combat, tốc độ cao**: nhặt 1–3 nguyên tố là ra phép/biến thể ngay.
- **Sáng tạo có giới hạn**: công thức đủ nhiều để khám phá, nhưng có “grammar” để người chơi đoán được.
- **2–4 hero, phối hợp rõ vai**: mỗi hero có cơ chế riêng để tạo/nhặt/nhân nguyên tố.
- **Vertical-first readability**: lane rõ, telegraph rõ, một tay vẫn chơi ổn.

## Vòng lặp (Core loop)

1. Chọn 2–4 hero + chọn “Rune Loadout” (meta) cho màn.
2. Vào trận: quái đi theo lane -> hero auto attack + người chơi can thiệp bằng reposition/ultimate.
3. Quái chết rơi nguyên tố -> hero nhặt -> mở “Craft Wheel” để ghép -> tạo spell.
4. Gắn spell vào slot (tối đa 3–4) -> dùng spell để clear wave/boss.
5. Trong trận lên level (tới 10) -> chọn 1 trong 3 perk (trade-off).
6. Kết thúc màn: reset level+spell; nhận meta currency + unlock/cập nhật sổ tay.

## Control (chốt hướng hybrid kiểu MOBA)

Mục tiêu: “đã tay” như MOBA nhưng không quá tải thao tác.

Chốt hướng: **Hybrid H1**

- **1 hero active**: người chơi điều khiển trực tiếp (giống MOBA)
  - Move: joystick/tap-to-move (tuỳ platform)
  - Cast spell: tap để smart-cast, hold để aim (line/radius), release để cast
- **1–3 hero phụ**: auto attack + đứng theo lane
  - Reposition realtime theo “anchor slots” (kéo portrait hero xuống ô/lane)
  - Reposition có wind-up ngắn để tránh spam và tăng readability

Nguyên tắc targeting:

- Tap spell: auto target theo policy (boss/elite/near-base/lowest HP)
- Hold spell: hiện preview và cho phép override mục tiêu

## Map & nhịp trận (vertical)

- 1 màn = 2–4 phút.
- 3 lane (mặc định), về sau mở 4 lane (để tăng độ sâu).
- UI gợi ý:
  - Nửa trên: lane + telegraph.
  - Nửa dưới: 2–4 hero portraits (tap đổi hero) + 3–4 spell slots (tap cast) + nút craft.

## PC/Steam (chốt lựa chọn B: PC-native)

- Vẫn giữ core gameplay theo trục dọc (đọc lane rõ), nhưng cho thêm **landscape expanded HUD**:
  - Battlefield nằm giữa (giữ tỉ lệ đọc tốt)
  - Hai bên là panel: spellbook/recipes, perk log, wave preview, hero management
- Input gợi ý:
  - Move (hero active): WASD hoặc click-to-move
  - Cast: `QWER` (tap) + giữ chuột để aim
  - Quick-craft: `1/2/3` cho 3 gợi ý
  - Switch hero active: `Tab` hoặc `F1–F4`

## Hệ nguyên tố (Element drops)

### Bộ nguyên tố

- Cơ bản: **Hỏa / Thủy / Mộc / Kim / Thổ**.
- Midgame: **Phong / Lôi** (để tăng biến hóa theo “tốc độ/CC”).
- Endgame (tuỳ): **Quang / Ảnh** (để mở mechanic phản-chiêu, curse, clone).

### Drop logic

- Mỗi loại quái có “bản chất” nên drop nghiêng về 1–2 nguyên tố.
- Elite/boss rơi “Core” (nguyên tố đậm đặc) dùng để craft tier cao.

## Spell Crafting System (điểm ăn tiền)

### Grammar: spell = Base + Shape + Modifiers

- **Base** (nguyên tố chính): quyết định type damage/interaction (burn, freeze, poison, bleed, armor break…)
- **Shape** (khuôn): bolt / beam / nova / trap / turret / aura / chain
- **Modifier** (gia vị): pierce, split, echo, siphon, overheat, bounce, delay, detonate…

Trong trận, craft theo “đơn vị nguyên tố” (token). Ví dụ:

- 2 token: spell tier-1 (nhanh, rẻ)
- 3 token: tier-2 (mạnh, có modifier)
- 4 token: tier-3 (rất mạnh, có nhược điểm/rủi ro)

### Công thức (ví dụ để hình dung)

- **Hỏa + Hỏa** -> `Ember Bolt` (single target, burn)
- **Thủy + Thủy** -> `Frost Nova` (AOE, slow)
- **Kim + Kim** -> `Piercing Lance` (xuyên giáp, xuyên hàng)
- **Mộc + Thổ** -> `Vine Trap` (root theo ô/lane)
- **Hỏa + Thủy** -> `Steam Beam` (beam lane, tick nhanh, giảm accuracy quái)
- **Phong + Lôi** -> `Chain Spark` (nhảy mục tiêu, tăng charge khi kill)

### Trade-off bắt buộc (để tránh “công thức tối ưu duy nhất”)

Mỗi spell tier-2/3 phải có 1 nhược điểm rõ:

- Overheat: cast liên tục sẽ lock spell 2–3s
- Self-drain: ăn mana/focus chung của team
- Fragile: mạnh nhưng chỉ có N charges
- Backfire: cast sai timing sẽ tạo debuff nhỏ

### “Sổ tay tri thức” để hỗ trợ khám phá

- Người chơi có thể chơi “mù” để tự khám phá.
- Nhưng game vẫn **dẫn dắt** bằng:
  - Quest gợi ý: “Craft 1 spell có Shape = Trap”
  - Log sau màn: “Bạn đã dùng 70% Hỏa; thử phối Thủy để mở Steam”
  - Hint theo boss: boss có tooltip “weak to Kim/Thổ”

### UI craft (gợi ý + 1-click)

- Hero nhặt token và đưa vào **Craft Bar** (tối đa 4 token).
- UI luôn có **3 nút Quick-Craft** (gợi ý recipe tốt nhất theo ngữ cảnh).
- Bấm 1 lần: craft ngay.
- Nếu slot hero đang đầy: đẩy vào “Queue” (1 ô) hoặc gợi ý thay spell yếu nhất.
- Tier-3 có confirm ngắn (hold) để giảm bấm nhầm.

## Hero design (2–4 hero mỗi màn)

Mỗi hero có 3 phần: **Vai trò lane**, **cơ chế nguyên tố**, **ultimate**.

### Archetype gợi ý

- **Collector**: hút/nam châm nguyên tố, giúp craft nhanh (support)
- **Catalyst**: nhân đôi token (nhưng tạo curse) để đẩy tier-3 (risk-reward)
- **Smith**: chuyển token (Kim<->Thổ…) theo cooldown để sửa sai craft (control)
- **Invoker**: cast spell mạnh hơn, nhưng spell decay nhanh (burst)

### Giới hạn spell slot

- Mỗi hero giữ 3 spell (cứng) + 1 slot “flex” của team (mở bằng meta).
- Mục tiêu: người chơi phải chọn “bộ bài phép” thay vì ôm hết.

## Progression (trong trận và meta)

### Trong trận (reset mỗi màn)

- Hero level 1 -> 10
- Mỗi level: chọn 1 trong 3 perk
- Perk có thể ảnh hưởng trực tiếp craft:
  - “Giảm cost token cho Shape Trap”
  - “Spell Beam có thêm 1 tick nhưng tăng overheat”

### Meta (giữ sau màn)

- Mở hero mới.
- Mở “Rune Board”: vài ô rune ảnh hưởng grammar (ví dụ thêm Shape mới).
- Nâng “Craft Bench”: tăng tốc craft, mở tier, mở slot team.
- Sổ tay tri thức: lưu discovered recipes + mastery.
- Cosmetic: VFX spell theo trường phái.

## Tuyến truyện (đủ dẫn dắt, không nặng cutscene)

Thế giới bị xé rách bởi **Lò Luyện Nguyên Tố** (một cỗ máy cổ đại). Quái vật là “tàn dư” của các mạch nguyên tố bị lỗi, tràn ra các khe nứt.

Bạn là nhóm **Spellwright** (thợ rèn phép) – những người hiếm hoi có thể “viết lại” phép bằng cách ghép nguyên tố ngay trong chiến trường.

Mỗi chương truyện tương ứng một vùng bị nhiễm:

- Chương 1: Hỏa mạch (quái nhanh, burn)
- Chương 2: Thủy mạch (slow, shield)
- Chương 3: Kim mạch (armor, reflect)
- Chương 4: Mộc mạch (summon, poison)
- Chương 5: Thổ mạch (tank, quake)

Twist cuối chương: kẻ địch không chỉ là quái, mà là “bản sao phép” (spell echoes) – học cách phản-craft.

## Yếu tố độc nhất để “cuốn” 2026

### 1) Boss có cơ chế “Counter-Recipe”

- Boss sẽ phát tín hiệu chuẩn bị skill.
- Người chơi có thể craft **đúng recipe phản** trong 3–5 giây để phá chiêu.
- Nếu craft sai: boss mạnh hơn (tạo drama).

### 2) “Spell Mutation” theo ngữ cảnh

- Cùng recipe nhưng tùy tình huống (lane đông/ít, hero nào cầm, thời tiết màn) sẽ biến thể.
- Ví dụ `Steam Beam`:
  - Lane đông -> beam rộng hơn nhưng yếu hơn
  - Lane ít -> beam mỏng nhưng xuyên mạnh

### 3) “Proof-of-Mastery” (thay vì pay-to-win)

- Mỗi spell có mastery challenge (dạng logic): “kill 30 quái bằng detonate đúng nhịp”.
- Mastery mở VFX/biến thể (không phá balance).

### 4) Async social: “Recipe Seeds”

- Người chơi share “seed” của một màn (pattern wave + bias drop).
- Bạn bè thử beat seed bằng build khác.
- Tạo nội dung UGC nhẹ, hợp 2026 (share short-form).

### 5) One-hand UX

- Tap/hold craft wheel.
- Swipe giữa hero.
- “Smart equip”: nếu slot trống, craft xong auto gợi ý gắn vào hero phù hợp.

### 6) “MOBA-readability” trong tower defense

- Mọi đòn nguy hiểm của elite/boss đều có telegraph rõ.
- Spell/skill có preview giống MOBA (line, cone, circle).
- Có “danger ping” tự động trên lane sắp vỡ.

## Trên thị trường có game nào giống chưa?

Có **một vài họ hàng gần** nhưng hướng của bạn vẫn có chỗ khác biệt:

- `GemCraft` (PC/Flash): **craft & combine gems** để gắn vào tower (rất gần về “combine”, nhưng không phải 2–4 hero và không có nhặt nguyên tố kiểu action).
- `Element TD` (Warcraft 3 map / mobile): **chọn element để mở tower** (rất gần về “element combination”, nhưng thiên về build tower trước/giữa wave, không có hero-carry spell loadout 3–4 slot và không tập trung discovery recipe trong combat).
- `Magicka` (PC/console): **combine elements để cast spell** (rất gần về “spell grammar”, nhưng không phải tower defense/lane defense).

Kết luận: ý tưởng “tower defense + Magicka-like craft-in-combat + 2–4 hero loadout giới hạn” là một mix tương đối mới, đặc biệt nếu bạn nhấn mạnh **counter-recipe boss** + **vertical one-hand**.

## Scope MVP (solo-friendly)

- 6 hero (mỗi run chọn 2–4).
- 20–30 recipe (tier 1–2) + 6 recipe tier-3.
- 3 chương, mỗi chương 10 màn + 1 boss.
- 1 mode endless (tuỳ).

## Rủi ro & cách giảm

- **Rủi ro quá nhiều công thức**: grammar rõ + tier unlock dần + sổ tay hint.
- **Rủi ro UI craft rối**: craft wheel tối đa 4 token, thao tác 1 tay.
- **Rủi ro “build tối ưu” thống trị**: mỗi spell có trade-off + boss buộc counter khác nhau.

## Save & Offline (Steam Cloud / mobile)

- Offline-first: chơi full offline.
- Trên Steam: hỗ trợ **Steam Cloud** để sync save (meta progression, sổ tay recipe, settings).
- Trên mobile: cloud save tuỳ chọn (không bắt buộc) để giữ tinh thần offline.

## Steam Early Access (marketing)

- Mục tiêu: build wishlist sớm bằng 1 demo có “wow moment” rõ.
- Demo tối thiểu nên có:
  - 4 hero
  - 15–20 recipe
  - 1 boss có cơ chế counter-recipe
- Dùng Steam Playtest để test control/craft UI.

## Câu hỏi cần bạn chốt để mình refine tiếp

- Bạn muốn map theo kiểu **lane cố định** (giống Arknights) hay **đường cong** (maze-lite)?
- Bạn thích tone truyện: **dark fantasy** hay **sci-fantasy** (cỗ máy nguyên tố)?