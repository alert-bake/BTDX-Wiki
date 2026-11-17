# Rocket Blimp (R.B.)

## Overview

The Rocket Blimp is a fast Nightmare-mode blimp. The source branch gives it a high movement multiplier and releases four Tattered Brick children when its shell is depleted.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| unverified report hits | 300 |
| unverified report RBE | 1,252 |
| unverified report children | 4 Tattered Bricks |
| unverified report speed | 406.25% of Red |
| Source branch | `Rocket_Blimp_Branch` |
| Shell formula | `ceil(300 * global.bpower)` |
| Source speed formula | `6.5 * global.bspeed` |

## Source-confirmed behaviour

The Step event creates a `Rocket_Show_off` visual effect and calculates movement at `6.5 * global.bspeed`. When shell falls below 1, it creates four Brick-branch children and sets `tattered = 1` on each. Above wave 50, the child object can be `Brick_Lag_Branch`.

The branch also applies its own freeze, glue, stun, distraction, and corrosion handling. The ordinary Bloon movement formula does not apply here.

## Reported values versus source

The source multiplier is 6.5× global speed. Compared with the ordinary Red multiplier of 1.6×, that is 406.25%, matching the unverified report speed figure under this comparison.

## Trivia

The Rocket Blimp's "rocket" identity is not just the speed stat: its Step event repeatedly creates a `Rocket_Show_off` effect that follows its current sprite frame and angle. Even its presentation gets its own object.

## Evidence

- **Source-confirmed:** [Rocket_Blimp_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Rocket_Blimp_Branch/Step_0.gml).
- **Needs in-game verification:** exact hit count, RBE, and mode availability.
