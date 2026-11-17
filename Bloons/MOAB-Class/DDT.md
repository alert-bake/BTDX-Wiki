# D.D.T. (Dark Dirigible Titan)

## Overview

The D.D.T. is a fast blimp with Camo and Lead properties. Its source branch uses a shell coefficient of 303 and releases six Tattered Camo Lead Brick children.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| Community-reported hits | 303 |
| Community-reported RBE | 1,731 |
| Community-reported children | 6 Tattered Camo Lead Bricks |
| Community-reported speed | 250% of Red |
| Source branch | `DDT_Branch` |
| Shell formula | `ceil(303 * global.bpower)` |
| Source speed formula | `4.0 * global.bspeed` |

## Source-confirmed behaviour

When shell falls below 1, the DDT branch creates six Brick-branch children. Each is assigned:
- `camo = 1`
- `lead = 1`
- `tattered = 1`
- Armour of `30 * global.bpower`

The children inherit the parent's path and hit bookkeeping. The DDT movement formula is `4.0 * global.bspeed`; compared with the ordinary Red multiplier of 1.6×, that is 250%.

The branch also has its own handling for freeze, glue, stun, distraction, and corrosion. Do not copy ordinary Bloon status thresholds into this page.

## Trivia

The DDT's six children are not generic Bricks with a label slapped on. The source explicitly sets all three properties on each child: Camo, Lead, and Tattered.

## Evidence

- **Source-confirmed:** [DDT_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/DDT_Branch/Step_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for RBE and the descriptive speed.
- **Needs in-game verification:** exact RBE and platform/mode availability.
