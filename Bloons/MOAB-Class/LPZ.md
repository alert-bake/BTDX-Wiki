# L.P.Z. (Lightning Powered Zeppelin)

## Overview

The L.P.Z. is a shielded lightning blimp. Its source branch tracks both shell and shield, fires a stun projectile at nearby towers, changes speed when its shield is gone, and releases ten Static Ceramic-tier Bloons when its shell is depleted.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| unverified report shell/RBE | 1,340 |
| unverified report shield | 500 |
| unverified report children | 10 Static Ceramics |
| unverified report shielded speed | About 93.88% of Red |
| unverified report unshielded speed | About 187.5% of Red |
| Source branch | `LPZ_Branch` |
| Shell formula | `ceil(300 * global.bpower)` |
| Shield formula | `ceil(500 * global.bpower)` |

## Source-confirmed durability and movement

The Step event initializes shell and shield once. When shield is positive, the source selects the shielded sprite and calculates `1.5 * global.bspeed`. When shield is depleted, it selects the unshielded LPZ sprite and calculates `3 * global.bspeed`.

Shell depletion is a separate condition. When shell reaches zero, the branch creates ten Static Bloon instances. Their layer is derived from the parent's layer minus 300; the child shield is set to `35 * global.bpower`. For the LPZ's layer-318 form, this yields layer 18, the Ceramic tier.

## Source-confirmed tower attack

The LPZ alarm repeats after `180 + random(30)` steps. It searches for a Monkey within a 240-unit circle and, if it finds one, creates a `Stun_Shot` aimed at that target. Projectile potency is set to `other.maxshield * 5`.

The source confirms the attack setup and potency calculation. The projectile's full impact effect must be read from `Stun_Shot`.

## Trivia

The LPZ has two independent durability pools and two distinct speed states. Losing the shield does not itself trigger the shell-depletion child routine; the source checks those conditions separately.

## Evidence

- **Source-confirmed:** [LPZ_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/LPZ_Branch/Step_0.gml) and [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/LPZ_Branch/Alarm_0.gml).
- **Needs further tracing:** Stun_Shot impact effect, exact in-game timing, and all mode variants.
