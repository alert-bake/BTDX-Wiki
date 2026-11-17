# B.R.C. (Big Rubbery Carrier)

## Overview

The B.R.C. is a carrier blimp whose source branch releases eight Mini M.O.A.B.s when its shell is depleted.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| Community-reported hits | 500 |
| Community-reported RBE | 4,428 |
| Community-reported children | 8 Mini M.O.A.B.s |
| Community-reported speed | 62.5% of Red |
| Source branch | `BRC_Branch` |
| Shell formula | `ceil(500 * global.bpower)` |
| Source speed formula | `1.0 * global.bspeed` |

## Source-confirmed behaviour

The source initializes shell using `500 * global.bpower` and sets movement to `1.0 * global.bspeed`. When shell falls below 1, it creates eight Mini M.O.A.B. branch instances. Each child receives shell and maximum shell of `75 * global.bpower`, inherits path information and hit bookkeeping, and receives a small path-position offset.

## Reported values versus source

The source multiplier is 1.0× global speed. Compared with the normal Red multiplier of 1.6×, this is 62.5%, matching the community-reported speed figure under that comparison. The shell coefficient also matches the reported 500 hits when `global.bpower = 1`.

## Trivia

The B.R.C. is a literal carrier in the source: its death routine creates eight Mini M.O.A.B. instances, each with the Mini M.O.A.B.'s own 75-coefficient shell.

## Evidence

- **Source-confirmed:** [BRC_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/BRC_Branch/Step_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for RBE and descriptive stats.
- **Needs in-game verification:** exact RBE and mode availability.
