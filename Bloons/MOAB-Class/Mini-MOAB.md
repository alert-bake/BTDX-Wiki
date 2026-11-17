# Mini M.O.A.B. (Miniature Massive Ornery Air Blimp)

## Overview

The Mini M.O.A.B. is the smallest documented member of BTDX's blimp family. Its source branch tracks a shell durability pool and releases four Ceramic Bloons when the shell is depleted.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| Community-reported hits | 75 |
| Community-reported RBE | 491 |
| Community-reported children | 4 Ceramics |
| Community-reported speed | Red-Bloon speed |
| Source branch | `Mini_Moab_Branch` |
| Shell formula | `ceil(75 * global.bpower)` |
| Source speed formula | `2.1 * global.bspeed` |

The hit count and RBE are community-reported. The source formula scales with `global.bpower`, so the shell value can change with game modifiers.

## Source-confirmed behaviour

The Step event initializes shell once using `spawned`, clamps it to `maxshell`, and assigns a movement value of `2.1 * global.bspeed`. Distraction and stun can change the speed; sufficiently strong freeze or glue can stop movement.

When shell reaches zero, the branch creates four Ceramic Bloons. Their armour is initialized to `10 * global.bpower`. Above wave 75, the child object changes to `Ceramic_Lag_Branch`. The parent is then destroyed.

## Speed discrepancy to investigate

The community page calls the Mini M.O.A.B. Red-Bloon speed. In the inspected source, the Mini M.O.A.B. multiplier is 2.1 while the ordinary Red multiplier is 1.6. Those raw multipliers do not match. The wiki preserves both claims rather than pretending the discrepancy is resolved.

## Trivia

The Mini M.O.A.B. is not just a bigger Bloon with a health bar: its source uses `shell`, and its children are created as separate Ceramic-branch instances. The shell is the blimp's own durability pool.

## Evidence

- **Source-confirmed:** [Mini_Moab_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Mini_Moab_Branch/Step_0.gml), [Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Mini_Moab_Branch/Create_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for 75 hits, RBE, and reported speed.
- **Needs in-game verification:** platform-specific hit count, RBE, and the speed discrepancy.
