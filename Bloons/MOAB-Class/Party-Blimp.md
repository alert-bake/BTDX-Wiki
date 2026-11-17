# Party Blimp (P.B.)

## Overview

The Party Blimp is a large Nightmare-mode blimp. The community reference describes it as the strongest non-Bounty Bloon. The source branch confirms a 15,000-coefficient shell and a large child release consisting of one Z.O.M.G. and eighteen Rocket Blimps.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| Community-reported hits | 15,000 |
| Community-reported RBE | 55,504 |
| Community-reported children | 18 Rocket Blimps and 1 Z.O.M.G. |
| Community-reported speed | 56.25% of Red |
| Source branch | `The_Party_Blimp_Branch` |
| Shell formula | `ceil(15000 * global.bpower)` |
| Source speed formula | `0.9 * global.bspeed` |

## Source-confirmed behaviour

The source calculates movement at `0.9 * global.bspeed`. When shell falls below 1, it creates one ZOMG branch child with a 4,000-coefficient shell and eighteen Rocket Blimp children with 300-coefficient shells. The children inherit path information and hit bookkeeping.

The branch also has its own handling for freeze, glue, stun, distraction, and corrosion.

## Reported values versus source

The source speed multiplier is 0.9× global speed. Compared with the ordinary Red multiplier of 1.6×, this is 56.25%, matching the community-reported speed figure under this comparison.

## Trivia

The Party Blimp's death routine is a full event: one Z.O.M.G. plus eighteen Rocket Blimps. That's nineteen separate blimp instances from one shell break. The party has a very aggressive guest list.

## Evidence

- **Source-confirmed:** [The_Party_Blimp_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/The_Party_Blimp_Branch/Step_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for the "strongest non-Bounty" description, RBE, and Nightmare restriction.
- **Needs in-game verification:** exact RBE, mode availability, and ranking against all non-Bounty special enemies.
