# Shielded

## Overview

Shielded Bloons have a shield durability pool that must be depleted before the underlying Bloon can be damaged. an unverified report also reports that shields protect the Bloon from status effects until the shield is removed.

BTDX implements Shielded Bloons through a dedicated `Shielded_Bloon_Branch`. The shield is separate from Ceramic/Brick armour and MOAB shell durability.

## Source-confirmed shield calculation

The Shielded branch calculates `maxshield` from the Bloon's `bloonlayer` and `global.bpower`. Selected source coefficients include:

| Shielded type | `bloonlayer` | Maximum shield formula |
|---|---:|---|
| Red | 1 | `ceil(1 × global.bpower)` |
| Blue | 2 | `ceil(2 × global.bpower)` |
| Green | 3 | `ceil(3 × global.bpower)` |
| Yellow | 4 | `ceil(4 × global.bpower)` |
| Pink | 5 | `ceil(5 × global.bpower)` |
| Black / White | 6 / 6.1 | `ceil(8 × global.bpower)` |
| Zebra | 7 | `ceil(11 × global.bpower)` |
| Rainbow | 8 | `ceil(15 × global.bpower)` |
| Prismatic | 8.5 | `ceil(30 × global.bpower)` |
| Ceramic | 18 | `ceil(25 × global.bpower)` |
| Brick | 48 | `ceil(55 × global.bpower)` |
| Mini MOAB | 93 | `ceil(100 × global.bpower)` |
| MOAB | 348 | `ceil(355 × global.bpower)` |
| BFB | 1248 | `ceil(1255 × global.bpower)` |
| ZOMG | 5248 | `ceil(5255 × global.bpower)` |

The branch also has explicit coefficients for fractional types such as Orange, Cyan, Lime, Amber, and Purple. The exact final value is rounded upward after scaling.

When shield reaches zero, the branch creates the corresponding underlying Bloon branch for the recognised type. For example, layer 18 becomes Ceramic, layer 48 becomes Brick, and the larger values transform into their corresponding blimp branches.

## unverified report interactions

an unverified report reports that Shielded Bloons:
- Resist low-damage explosions.
- Cannot be frozen or glued while the shield remains.
- Are not bypassed by M.I.B. immunities.
- Take an additional 0.25 damage from all sources against the shield.

These are unverified report combat rules; the shield calculation and transformation paths above are directly visible in source.

## Stacking

an unverified report lists Shielded as compatible with:
- Splitting
- Static

Shielded Splitting forms are reported to have twice the shield value of the Bloon they split into. Treat this as a separate reported rule, not as a universal multiplier for every Shielded Bloon.

## Trivia

The Shielded branch has explicit values for fractional types too. Amber's shield coefficient is 8, even though its normal-branch type value is only 4.5. The shield formula is a lookup by type, not a direct copy of `bloonlayer`.

## Evidence

- **Source-confirmed:** [Shielded_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Shielded_Bloon_Branch/Step_0.gml).
- **Needs in-game verification:** exact shield damage rules, status immunity, and behaviour across all game modes.
