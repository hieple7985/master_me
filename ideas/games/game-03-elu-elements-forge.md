# game-03: Element Forge
 
 ## Direction (confirmed)
 - **Genre**: Casual mobile puzzle
 - **Core**: Match-3 to build/craft elemental pieces, then clear **level objectives**
 - **Combat/Boss**: Boss appears as an **objective set-piece** (not full RPG)
 - **Monetization**: Ads + IAP
 - **Release**: Global (English-first)
 - **Art direction**: Cute/bright
 
 ## One-line hook
 Match-3 to auto-craft elemental orbs with fixed recipes, then use them to beat objectives and boss mechanics.
 
 ## Pillars
 1. **Familiar match-3** (swap + gravity + cascades)
 2. **Element crafting** (fixed recipes, discovery/collection feel)
 3. **Objective variety** + occasional boss set-pieces
 
 ## Core loop
 - Enter level with 1-2 clear objectives
 - Swap tiles to match and generate resources
 - Auto-craft elemental orbs via fixed recipes
 - Spend orbs / trigger effects to progress objectives
 - Win on completing objectives before move limit (MVP)
 
 ## Match-3 rules (MVP)
 - Board: rectangular grid, gravity, cascades
 - Input: swap 2 adjacent tiles
 - Valid move required (optional: hint if no move)
 - Special matches:
   - Match-4 creates a **Line Clear** tile
   - Match-5 creates a **Color Clear** tile
 
 ## Objectives (templates)
 - **Clear**: remove X blockers
 - **Collect**: collect X items that drop from top and must reach bottom
 - **Score/Progress**: reach a target progress bar (for early tutorials)
 - **Boss**: break X weakpoints / shields (see below)
 
 ## Element system
 ### Design constraints
 - Long-term: up to ~27 combined elements
 - MVP: ship a smaller set, but keep the architecture consistent
 - Effects should map to a small number of **archetypes** to keep balance manageable
 
 ### Raw elements (MVP proposal)
 - **Fire**
 - **Water**
 - **Earth**
 - **Air**
 - **Light**
 - **Shadow**
 
 ### Crafted orbs (MVP proposal: 9 recipes)
 - Fire + Air -> **Explosion Orb** (AoE clear)
 - Water + Air -> **Storm Orb** (random zaps / line clear)
 - Earth + Air -> **Quake Orb** (crack nearby blockers)
 - Fire + Water -> **Steam Orb** (fog/soften blockers)
 - Water + Earth -> **Vine Orb** (grow/convert tiles or trap enemies)
 - Fire + Earth -> **Magma Orb** (persistent hazard / multi-hit)
 - Light + Shadow -> **Eclipse Orb** (convert + burst)
 - Light + Air -> **Radiance Orb** (extra moves/time-like relief via progress)
 - Shadow + Earth -> **Curse Orb** (weaken boss shield / reduce blocker strength)
 
 ### How crafting works (fixed recipe, auto-craft)
 - Matching raw tiles charges their **element meter**
 - When a recipe condition is met, the orb is auto-crafted onto the board
 - Orbs appear on board as a special tile and trigger when matched/activated
 
 ## Boss set-piece (objective-based)
 ### Boss goals
 - Keep it puzzle-first: boss is a **board modifier**, not a full RPG system
 
 ### Boss template (3-phase)
 - **Phase 1**: Boss shield element rotates every N moves
 - **Phase 2**: Summons blockers on a pattern; player must craft the counter-orb
 - **Phase 3**: Exposes weakpoints; break weakpoints using specific crafted orbs
 
 ### Failure / pressure
 - MVP: **moves-based** (clear objectives before move limit)
 - Later: add timed event levels (non-core progression)
 
 ## Progression (casual)
 - World map chapters
 - Gradual unlock of raw elements and recipes
 - Lightweight collection: recipe book + orb upgrades (late game)
 
 ## Monetization (Ads + IAP)
 - **Rewarded ads**:
   - +5 moves on fail
   - Start-level booster
   - Daily bonus multiplier
 - **IAP**:
   - Starter pack (boosters + remove ads)
   - Booster bundles
   - Optional: recipe cosmetic skins (late)
 - Avoid gacha/hero systems in MVP (scope + balance risk)
 
 ## MVP scope (to ship fast)
 - 1 board type, 6 raw elements, 9 crafted orbs
 - 6-8 objective templates
 - 1 boss template reused with parameter variations
 - 50-100 levels for first release iteration
 
 ## Success metrics (targets to validate)
 - D1 retention: >= 30%
 - D7 retention: >= 8-12%
 - Session length: 5-10 minutes
 - Rewarded ad opt-in: healthy but not required to progress
 
 ## Main risks
 - Balance explosion from too many unique effects (mitigation: archetype mapping)
 - Content production (mitigation: objective templates + boss template)
 - Tutorial complexity (mitigation: unlock elements/recipes slowly)