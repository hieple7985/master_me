# 09. Game Monkey

## Giá
- 38tr

## Estimate (solo)
- Tổng: 8-12 ngày làm việc
- Breakdown (ước lượng):
  - 1) FX coin success: 0.5-1 ngày
  - 2) Character model khi đoán trúng: 1-2 ngày
  - 3) FX xuất hiện coin trên cột: 0.5-1 ngày
  - 4) Text nhảy về (UI text vs Text 3D): 0.5-1.5 ngày
  - 5) Win screen + sequence (FX + coin nổ/rơi): 2-4 ngày
  - 6) Rung + particle scaling theo streak: 1-2 ngày
  - Integrate API + tune + bugfix: 2-3 ngày

## Stack
- Phaser 3: gameplay/render/anim/tween/audio/masking
- React + Vite: shell UI + routing
- TypeScript: toàn dự án
- REST (NestJS backend): balance, win/lose, multiplier, cashout, limit mode
- Assets (PNG frames): coin flip, fire win/lose, slot doors, buttons, HUD

## Tasks
1. FX khi quay coin thành công
2. Gọi model nhân vật khi đoán trúng
3. Đổi FX xuất hiện xu đoán trúng trên cột
4. Text “nhảy về” khi đoán đúng (UI text hay Text 3D?)
5. Màn hình win (nhân vật + FX trên + coin nổ rơi)
6. Rung điện thoại + particle tăng dần theo số coin lật được