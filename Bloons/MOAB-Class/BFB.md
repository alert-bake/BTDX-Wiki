# B.F.B. (Brutal Floating Behemoth)

## Overview

The B.F.B. is a large blimp with a source-defined shell coefficient of 900. When its shell is depleted, it releases three M.O.A.B.s.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| unverified report hits | 900 |
| unverified report RBE | 4,656 |
| unverified report children | 3 M.O.A.B.s |
| unverified report speed | About 71.88% of Red |
| Source branch | `BFB_Branch` |
| Shell formula | `ceil(900 * global.bpower)` |
| Source speed formula | `1.15 * global.bspeed` |

## Source-confirmed behaviour

The branch initializes shell once, clamps it to its maximum, and sets movement to `1.15 * global.bspeed`. Its code applies its own freeze and glue thresholds, plus stun and distraction handling.

When shell falls below 1, the B.F.B. creates three `Moab_Branch` instances. Each child receives shell and maximum shell of `300 * global.bpower`, and inherits the parent's path and hit bookkeeping.

## Reported values versus source

The source speed multiplier is 1.15× global speed. Compared with the normal Red multiplier of 1.6×, that is 71.875%, matching the unverified report 71.88% figure under this comparison. The 900 shell coefficient also matches the unverified report 900 hits when `global.bpower = 1`.

## Trivia

A B.F.B. does not produce a random pile of lower Bloons in the inspected Step event. It creates exactly three MOAB branch instances, each with its own 300-coefficient shell.

## Evidence

- **Source-confirmed:** [BFB_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/BFB_Branch/Step_0.gml).
- **Needs in-game verification:** exact RBE and mode-specific modifiers.
