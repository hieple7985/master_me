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
  - Move (mobile): **tap-to-move**
  - Move (PC/Steam): WASD hoặc click-to-move
  - Cast spell: tap để smart-cast, hold để aim (line/radius), release để cast
- **1–3 hero phụ**: auto attack + đứng theo lane
  - Reposition realtime theo “anchor slots” (kéo portrait hero xuống ô/lane)
  - Reposition có wind-up ngắn để tránh spam và tăng readability

Nguyên tắc targeting:

- Tap spell: auto target theo policy (boss/elite/near-base/lowest HP)
- Hold spell: hiện preview và cho phép override mục tiêu

## Map & nhịp trận (vertical)

- 1 màn = 2–4 phút.
- Map theo kiểu **arena grid** (gợi nhớ Clash Royale): battlefield chia ô để dễ đọc/đặt phép, nhưng unit/hero **di chuyển gần như tự do**.
- Có thể bắt đầu với 3 “luồng” chính (soft lanes) để người chơi đọc nhanh, về sau tăng độ dày wave thay vì tăng số lane.
- UI gợi ý:
  - Nửa trên: lane + telegraph.
  - Nửa dưới: 2–4 hero portraits (tap đổi hero) + 3–4 spell slots (tap cast) + nút craft.

### Grid + free moving (cách hiểu cụ thể)

- Battlefield là lưới theo **template** (không đổi kích thước tùy tiện) để:
  - đặt trap/turret/wall theo ô
  - preview AOE/beam “bám grid” dễ đọc
- Grid size có thể thay theo map/chapter/difficulty nhưng nên nằm trong **vài template cố định** (để người chơi học được và để balance/telegraph ổn định):
  - Small: **6x10** (dễ, nhịp nhanh)
  - Standard: **7x11** (mặc định)
  - Large: **8x12** (late game/challenge)

Lý do không nên “động tuỳ ý” theo từng map:

- Người chơi cần học “khoảng cách” để aim/đặt trap (đặc biệt trên mobile).
- Boss telegraph + counter window phụ thuộc mật độ ô và thời gian di chuyển.
- Vài template cố định vẫn đủ tạo đa dạng nhờ terrain layout, spawn gates, và objective nodes.
- Di chuyển unit/hero theo **navmesh/flow-field**:
  - quái có hướng đi chính về base nhưng có thể “lệch” theo va chạm, push/pull, slow field
  - hero active có thể di chuyển tự do trong vùng cho phép
- “Anchor slots” trở thành **Anchor Zones**:
  - thả portrait hero vào 1 zone/ô -> hero chạy tới đó và giữ vị trí chiến đấu
  - reposition vẫn realtime nhưng có wind-up/cooldown để không thành spam

### Wave & spawn (chốt lựa chọn B: multi-entry horde)

- Quái spawn từ **nhiều cổng** (top/left/right) và chảy về base theo flow-field.
- Mỗi màn có “nhịp áp lực” rõ (để người chơi đọc nhanh như MOBA/auto-battler):
  - Wave thường: 15–25s
  - Wave elite: 25–35s (có 1–2 quái tạo biến số)
  - Boss wave: 45–70s (telegraph rõ + counter-recipe window)
- “Soft lanes” vẫn tồn tại như **luồng giao thông** (choke points tự nhiên), nhưng không khóa cứng.

Role quái (để sản xuất nhanh nhưng đa dạng):

- `Runner`: nhanh, ít máu, ép phản xạ.
- `Tank`: chậm, nhiều giáp, ép dùng Kim/Thổ.
- `Shielder`: tạo shield AOE, ép chọn target policy.
- `Disruptor`: push/pull hoặc silence spell 1–2s.
- `Miner`: chạy tới terrain node để hút tài nguyên (tạo objective phụ).

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

## Địa hình, vật liệu tự nhiên & khai thác (lightweight)

Battlefield có vật liệu như **đá/cây/rãnh/cầu/địa hình** để tăng tactical depth, nhưng không biến thành game mining.

### Terrain features (tác dụng chiến thuật)

- **Đá / vách**: chặn line-of-sight, tạo choke point; beam/chain có thể bị cắt.
- **Cây / bụi**: che tầm nhìn nhẹ hoặc tạo “zone” tăng/giảm accuracy (tuỳ theme).
- **Rãnh / hào**: làm chậm hoặc bắt buộc đi vòng; một số quái bay bỏ qua.
- **Cầu**: choke point rõ; dễ đặt trap/wall.
- **Địa hình cao/thấp**: bonus nhỏ cho tầm bắn hoặc chống push/pull.

### Resource harvesting (gắn với spell craft)

Thay vì “đào vàng”, mỗi terrain node tạo ra **Material Shards** dùng như “gia vị” craft:

- `Stone Shard` (đá): thêm modifier kiểu `Fortify` / `Wall` / `Armor Break`.
- `Wood Resin` (cây): thêm modifier kiểu `Growth` / `Vine` / `Poison duration`.
- `Water Silt` (rãnh): thêm modifier kiểu `Slow field` / `Cleanse`.
- `Bridge Iron` (cầu): thêm modifier kiểu `Pierce` / `Conduct`.

Cách khai thác để không rối:

- Node có trạng thái “đang hoạt động” theo thời gian (spawn shard 1 lần mỗi X giây).
- Hero có thể **đứng gần node** để tự nhặt (passive) hoặc có 1 skill “Harvest” cooldown dài.
- Shard không thay thế token nguyên tố; shard chỉ mở **biến thể** cho recipe (tier-2/3) hoặc giảm trade-off.

Chốt hướng: **A-dominant + B-lite**

- **A (chính)**: shard dùng để augment/biến thể spell (modifier, giảm trade-off, đổi shape nhỏ).
- **B (nhẹ)**: shard cũng tạo ra một “nhịp economy” rất nhỏ trong màn, chỉ để làm vài hành động chiến thuật hiếm.

Ví dụ:

- `Frost Nova` + `Water Silt` -> tạo “slippery field” kéo dài hơn nhưng giảm damage.
- `Vine Trap` + `Wood Resin` -> root mạnh hơn nhưng cooldown dài.

### B-lite: Tactical resource trong màn (không biến thành economy-heavy)

Quy tắc:

- Không có “spam unit” như game deck battler.
- Người chơi chỉ có 2–3 hành động dạng B trong cả màn (tùy perk), chủ yếu để cứu tình huống.

Ví dụ hành động B:

- `Emergency Ward` (tốn shard bất kỳ): đặt 1 công trình tạm trong 8–12s để chặn/taunt.
- `Reroll Quick-Craft` (tốn shard): đổi 3 gợi ý quick-craft.
- `Overcharge Bench` (tốn shard): craft tier-3 bỏ qua hold-confirm 1 lần hoặc giảm overheat 1 lần.

Counterplay:

- Một số quái `Miner` sẽ hút shard từ node (objective phụ), ép người chơi giữ map control.

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

## Adaptive Difficulty (tự hiệu chỉnh khó/dễ)

Mục tiêu: giữ nhịp “căng nhưng công bằng” cho cả người mới và người giỏi, đặc biệt vì game có yếu tố khám phá recipe.

Nguyên tắc:

- Không nerf thẳng damage của người chơi theo kiểu lộ liễu.
- Ưu tiên điều chỉnh bằng **spawn composition**, **telegraph window**, và **tài nguyên cứu nguy**.
- Chỉ điều chỉnh theo “khoảng” (bands), không thay đổi liên tục từng giây.

### Skill signals (đo người chơi giỏi hay chưa)

Tính điểm “Performance Score” theo cửa sổ 30–60s:

- `Base HP lost` trong window.
- `Overkill margin`: còn dư bao nhiêu so với áp lực (clear speed).
- `Craft efficiency`: token bị waste (đầy bar, craft chậm), số lần craft sai/nghẽn.
- `Counter-recipe success`: thành công hay thất bại (boss/elite).
- `Hero downtime`: hero đứng sai vị trí quá lâu (bị push khỏi choke, không cover).

### Knobs (cần gạt để chỉnh khó)

Chỉnh theo 3 tầng: Easy / Normal / Hard trong cùng một stage, dựa trên Performance Score.

- **Wave composition**:
  - tăng/giảm tỷ lệ `Runner` vs `Tank` vs `Disruptor`
  - chèn thêm 1 `Miner` hoặc bỏ `Miner`
- **Telegraph & counter window**:
  - tăng/giảm 0.3–0.6s cho đòn boss quan trọng
  - counter-recipe window có thể dài hơn cho người mới
- **Terrain shard intensity**:
  - người chơi yếu: node spawn shard sớm hơn hoặc gần base hơn
  - người chơi giỏi: node spawn xa hơn (đòi map control)
- **B-lite lifeline**:
  - người chơi yếu: thêm 1 lần miễn phí `Emergency Ward`
  - người chơi giỏi: giảm số lần B-lite trong màn

### Anti-frustration rules

- Không tăng khó ngay sau khi người chơi vừa fail.
- Khi người chơi fail liên tiếp 2–3 lần cùng stage, bật “Mercy Band” trong 1 run kế.
- Người chơi giỏi có thể bật “Challenge Lock” để khóa difficulty (không adaptive).

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

### Opening hook (đưa người chơi vào game)

- Mở đầu: một thành phố tiền tuyến bị vỡ **mạch nguyên tố**, quái tràn ra từ các khe.
- Nhân vật chính (người chơi) được tuyển vào hội **Spellwright** để bảo vệ các “Lò Ổn Định” (stabilizer nodes).
- Tutorial được gắn vào câu chuyện: lần đầu craft thành công là “viết lại” một đoạn mạch nguyên tố.

### Factions

- **Spellwright Guild**: rèn phép, chữa lỗi mạch.
- **The Echo Court**: các “bản sao phép” tự ý thức, muốn chiếm quyền điều khiển mạch.
- **Warden Constructs**: máy cổ đại bảo vệ lò, nhưng giờ hoạt động sai lệch.

### Chapter beats (đủ cho live content)

- Mỗi chapter có:
  - 10–12 stage
  - 1 mini-boss (giữa chương)
  - 1 boss (cuối chương)
  - 1 mechanic mới (terrain, element, hoặc shape)

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

### 7) “Map control” kiểu Warcraft Rumble (nhưng offline)

Mượn tinh thần của các game kiểu `Warcraft Rumble`: map không chỉ là đường đi, mà là **điểm tranh chấp**.

- **Choke point + terrain node** tạo quyết định: giữ vùng nào để dễ craft/tối ưu spell.
- **Objective phụ** (miner quái, elite chiếm node) tạo nhịp trận và lý do reposition.
- Unit role rõ: mỗi hero/quái có “điểm làm việc” riêng (không dẫm chân).

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

## DLC (nếu làm thêm 1 bản)

### Base game vs DLC: nguyên tắc phân rã

- Base game phải có vòng lặp hoàn chỉnh và “đủ no” để review tốt.
- DLC nên thêm **1 mechanic lớn** + **1 chapter theme** + **pool recipe mới**.

### Phase breakdown (khuyến nghị)

- **Phase 0: Prototype (2–4 tuần)**
  - 1 map grid, 1 hero active, 2 hero phụ
  - 10 recipe, 1 boss counter-recipe
- **Phase 1: Vertical Slice (4–8 tuần)**
  - 4 hero, 20 recipe, terrain shards A-dominant + B-lite
  - 1 chapter (10 stage) + 1 boss
- **Phase 2: Base Launch (8–16 tuần)**
  - 3 chapter + meta progression + polish UX
- **Phase 3: DLC 1 (6–10 tuần)**
  - 1 chapter mới + 1 mechanic mới + 2 hero + 12–18 recipe + 1 boss

### DLC 1 gợi ý (mẫu)

- Theme: **Phong/Lôi** (đẩy mạnh reposition, chain, và map control)
- New terrain: `Lightning Rod` node (tạo shard đặc biệt để augment chain/beam)
- New enemies: `Blinker` (teleport), `Grounder` (tắt chain), `Storm Miner`
- New boss: có 2 counter windows liên tiếp (đòi craft nhanh nhưng vẫn one-click)

## Câu hỏi cần bạn chốt để mình refine tiếp

- Grid size: bạn muốn mặc định là **7x11** và dùng template **6x10/8x12** cho map khó/dễ chứ? Lý do chọn template cố định thay vì dynamic sizing là để đảm bảo trải nghiệm chơi ổn định và dễ dự đoán.
- Base position: mặc định **bottom-center**; về sau map variant có thể đổi để tạo thử thách.
- Tap-to-move chốt rồi; bạn muốn thêm tùy chọn `double-tap` để dash/evade không?
- Bạn thích tone truyện: **dark fantasy** hay **sci-fantasy** (cỗ máy nguyên tố)?