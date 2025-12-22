# game-04
 
## High concept
Isometric/top-down lap-based arcade combat racing set in a cyberpunk city, starring feline couriers (hài + ngầu). Core loop keeps SNES/arcade readability and aggression, but uses original world, UI, vehicles, weapons, tracks, and audio identity.

## Target platform
iOS/Android (mobile-first).

## Business model
Premium, low price.

## Pillars
- Readability-first on small screens (vehicles, projectiles, pickups, hazards).
- Lap rhythm (combat windows placed intentionally per sector/lap).
- Aggressive arcade handling (drift, bumping, line control).
- Comedy + cool (cat gadgets are funny, presentation stays stylish).
- Anti-reskin identity (distinct UI, track language, weapon set, vehicle fantasy, audio).

## Core loop
- Choose rider + cyber ride.
- Race 3–5 laps on an isometric track.
- Collect pickups (weapon/boost/defense).
- Use light combat to gain position (no heavy destruction focus).
- Finish → reward → upgrade/unlock → next event.

## Vehicles ("cyber rides")
Avoid motorbike silhouettes; use original vehicle fantasy.
- Mono-wheel courier
- Hover-scooter
- Tri-ride drifter
- Magnet-board

Stats axes:
- TopSpeed
- Accel
- Handling (Grip/Drift)
- Armor/Weight

## Weapons (light combat)
Design goal: readable, short effects, position play (slow/knock/deny line), not long disable chains.
- Yarn Snare Drone: short snare line that reduces handling.
- Laser Pointer Decoy: misdirect soft-lock for a moment.
- EMP Meow Burst: small radius, brief boost-disable.
- Scratch Blades: close-range shove/knock.
- Tuna Can Mine: small splash slow.

Loadout: 1 main weapon slot + 1 defense slot (shield/dash).

## Track language (cyberpunk city)
Each track has:
- 3 sectors with distinct palettes and signage.
- 1 signature hazard (beat-gates, conveyor mall floor, ventilation gust, holo-billboard occlusion).
- 1 risk shortcut (tight service tunnel, rooftop cut, maintenance ramp).
- 1 combat choke (narrow lane or hazard zone where timing matters).

## Controls (mobile)
- Scheme A: left thumb steer, right thumb buttons (drift/boost/weapon/defense).
- Scheme B: drag-steer + auto-accel (casual).
- Soft-lock cone assist for weapons to reduce touch aiming burden.

## Progression
- District-based career (Neon Harbor / Old Metro / Cloud Mall / Server Alley...).
- Series events unlock:
  - New rides
  - Weapon modules
  - Cosmetic trails/plates
- Boss race per district with a signature build.

## Roster (riders)
Each rider has a passive perk to support build variety without turning combat into a shooter.
- Kumo: +handling while drifting.
- Pixel: +pickup magnet radius.
- Nori: +boost regen on clean laps.
- Sable: +armor, lower knockback.
- Miso: +weapon cooldown slightly reduced.
- Taffy: +higher top speed, weaker armor.

## Districts / tracks (v1 content list)
Each track includes 1 signature hazard + 1 risk shortcut + 1 combat choke.
- Neon Harbor Circuit: beat-gates at docks; shortcut via container lane; choke at crane turn.
- Old Metro Loop: train pass hazards; shortcut through maintenance tunnel; choke at platform S-curve.
- Cloud Mall Ring: conveyor floors; shortcut through service escalator ramp; choke at food-court narrow.
- Server Alley Sprint: holo-billboard occlusion; shortcut via data-center vent; choke at firewall gate.
- Rain District Overpass: gust vents on bridges; shortcut via rooftop ramp; choke at toll booths.
- Holo Theater Circuit: strobe lights affect readability windows; shortcut behind stage props; choke at backstage corridor.
- Junkyard Neon Yard: magnet pulses tug rides; shortcut across scrap bridge; choke at crusher lane.
- Skyline Helix: wind shear; shortcut through maintenance spiral; choke at helix apex.

## Scope guardrails (solo)
- v1 focuses on strong handling, readability, and a polished PvE career.
- No real-time PvP at launch.
- No user-generated tracks at launch.

## Solo production estimate (global, 2026)
Assuming you work solo with a reusable engine stack and store-ready pipelines.

- Prototype (4–6 weeks)
  - Core handling + isometric camera
  - 1 ride + 1 weapon + 1 track graybox
  - Basic UI + lap timing
- Vertical slice (8–12 weeks)
  - 2 rides, 3 weapons, 2 tracks
  - Core meta (rewards, upgrade loops)
  - Art direction locked (shaders, UI kit, VFX style)
- Beta content (12–16 weeks)
  - 6 riders, 4 rides, 5 weapons
  - 6 tracks + boss templates
  - Difficulty tuning + accessibility controls
- Release candidate (6–10 weeks)
  - 8 tracks, final UI polish, device performance pass
  - Store assets, achievements, analytics minimal
  - QA sweep + crash fixing

Total: ~7–11 months (realistic solo), depending on art production speed.

## Sales and revenue (premium, low price, global)
These are directional assumptions for planning, not guarantees.

Assumptions:
- Price: USD $1.99–$3.99
- Platform fee: 30%
- Refunds/chargebacks allowance: 2–5%
- Net per unit (very rough):
  - $1.99 price → ~$1.30 net
  - $2.99 price → ~$1.95 net
  - $3.99 price → ~$2.60 net

Distribution scenarios (units sold in 12 months):
- Low: 10k–30k
- Base: 50k–150k
- High: 300k–800k

Net revenue ranges (12 months):
- Low: ~$13k–$78k
- Base: ~$65k–$390k
- High: ~$390k–$2.08M

What moves the needle most (for premium):
- Trailer + first 10 seconds gameplay readability
- Launch featuring / press pickup
- Strong keyword positioning ("top-down combat racer", "isometric arcade racing")
- 2–3 standout tracks that look unique in screenshots

## Art direction (2.5D HD)
- Isometric camera ~30–35° tilt, slight dynamic zoom on boost.
- Stylized PBR with strong rim neon lighting for silhouette readability.
- UI is holographic + playful (cat humor) but not toy-like.
- VFX chunky and readable (sparks, skid decals, short-lived projectiles).

## PvE vs PvP (2026 recommendation)
For a low-price premium mobile game, the safest path is:
- Primary: PvE career + time trials.
- Competitive: asynchronous PvP (leaderboards, ghosts, weekly challenges).

Reasons:
- Premium games struggle to sustain real-time PvP concurrency on mobile unless you already have a big funnel.
- Real-time PvP adds large scope: netcode, matchmaking, anti-cheat, balance, live-ops cadence.
- Asynchronous PvP still delivers competitiveness with much lower risk and clearer offline value.

Optional later (only if metrics justify): real-time PvP rooms (2–4 players) as a post-launch update.