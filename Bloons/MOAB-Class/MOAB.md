# M.O.A.B. (Massive Ornery Air Blimp)

## Overview

The M.O.A.B. is a major blimp enemy with its own shell durability and Brick child-spawn routine. The inspected source branch uses a base shell coefficient of 300 and creates four Brick Bloons when the shell is depleted.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| Unverified hits | 300 |
| Unverified RBE | 1,252 |
| Unverified children | 4 Bricks |
| Unverified speed | 75% of Red |
| Source branch | `Moab_Branch` |
| Shell formula | `ceil(300 * global.bpower)` |
| Source speed formula | `1.5 * global.bspeed` |

The reported hit count and RBE are not guaranteed fixed values: the source scales shell with `global.bpower`.

## Source-confirmed behaviour

The branch initializes `shell` once, clamps it to `maxshell`, and calculates movement from `1.5 * global.bspeed`. Freeze and glue have high thresholds in this branch; distraction and stun also use MOAB-specific handling.

When shell falls below 1, the source creates four Brick-branch children. Above wave 75, it selects `Brick_Lag_Branch`. The usual path initializes each child with layer 48 and armour `30 * global.bpower`. If the current Brick-branch instance count is already 16 or greater, a fallback path creates four children with armour `50 * global.bpower` and derives their layer from the parent's layer minus 300.

## Speed discrepancy to investigate

An unverified value lists the M.O.A.B. at 75% of Red speed. The inspected source uses 1.5× global speed for M.O.A.B. and 1.6× for ordinary Red, which is 93.75% when comparing those two raw branch multipliers. This discrepancy remains unresolved and needs in-game verification.

## Trivia

The M.O.A.B.'s child logic has a population-dependent branch: when enough Brick Bloons already exist, the children are initialized differently. The source is accounting for the current battlefield, not just blindly cloning four identical bricks.

## Evidence

- **Source-confirmed:** [Moab_Branch/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Moab_Branch/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Moab_Branch/Step_0.gml).
- **Needs in-game verification:** hit count, RBE, and the speed discrepancy.