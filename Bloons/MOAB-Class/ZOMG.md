# Z.O.M.G. (Zeppelin of Mighty Gargantuaness)

## Overview

The Z.O.M.G. is a high-durability blimp with a source-defined shell coefficient of 4,000. When its shell is depleted, it creates three B.F.B. children.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| unverified report hits | 4,000 |
| unverified report RBE | 17,968 |
| unverified report children | 3 B.F.B.s |
| unverified report speed | About 59.38% of Red |
| Source branch | `ZOMG_Branch` |
| Shell formula | `ceil(4000 * global.bpower)` |
| Source speed formula | `0.95 * global.bspeed` |

The community source notes a mode restriction in one context. Do not assume the Z.O.M.G. appears in every round set or game mode.

## Source-confirmed behaviour

The branch initializes shell once and creates three `BFB_Branch` instances when shell falls below 1. Each child receives a shell coefficient of 900 multiplied by `global.bpower`, inherits path information and hit bookkeeping, and is offset slightly along the path.

The source movement formula is `0.95 * global.bspeed`. Compared with the ordinary Red multiplier of 1.6×, this is 59.375%, matching the unverified report 59.38% under that comparison.

## Trivia

The Z.O.M.G. has a clean three-stage source chain: its shell is 4,000× the global power factor, and its three children each receive the B.F.B.'s 900× coefficient. The child chain is explicit in the Step event.

## Evidence

- **Source-confirmed:** [ZOMG_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/ZOMG_Branch/Step_0.gml).
- **Needs in-game verification:** RBE, exact mode restrictions, and platform differences.
