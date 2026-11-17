# Static / Energized

## Overview

Static Bloons are electrical Bloons with a shield and a periodic attack against towers. an unverified report also calls this form Energized; **Static** is the name used by the source object, `Static_Bloon_Branch`.

This is more than a visual modifier: the branch has its own shield calculation, movement code, and attack alarm.

## Source-confirmed implementation

The Static Create event initializes:
- `electric = 1`
- `normal = 0`
- `camo = 0`, `lead = 0`, and `regrow = 0`
- `shield = 0` and `maxshield = 0`
- A periodic alarm with a random initial delay

The Static Step event calculates shield strength using twice the corresponding Shielded coefficient. Examples include:

| Type | Normal Shield coefficient | Static coefficient |
|---|---:|---:|
| Red | 1 | 2 |
| Blue | 2 | 4 |
| Black / White | 8 | 16 |
| Zebra | 11 | 22 |
| Rainbow | 15 | 30 |
| Ceramic | 25 | 50 |
| Brick | 55 | 110 |
| MOAB | 355 | 710 |

The exact maximum is rounded up after multiplication by `global.bpower`.

The Static alarm searches for a Monkey within a range based on `100 + maxshield`. If it finds a target, it creates a `Stun_Shot` and sets projectile potency to `maxshield * 2`. This confirms the projectile creation and potency calculation; the full stun effect belongs to the projectile's own implementation.

## Reported behaviour

an unverified report describes Static Bloons as:
- Shielded electrical forms.
- Periodically firing a projectile at towers.
- Stuning/disabling a tower hit by the projectile.
- Moving more slowly than their unmodified counterparts.

The source confirms the electrical state, doubled shield coefficients, target search, and projectile creation. The exact stun duration and full movement comparison need further tracing.

## Stacking

an unverified report lists no stacking combinations for Static. It does list Static as a possible combination with Splitting.

## Trivia

Static's shield is not merely the ordinary shield with a cosmetic lightning overlay. Its Step event doubles the shield coefficients, and its alarm creates a dedicated projectile. The electricity has paperwork.

## Evidence

- **Source-confirmed:** [Static_Bloon_Branch/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Static_Bloon_Branch/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Static_Bloon_Branch/Step_0.gml), and [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Static_Bloon_Branch/Alarm_0.gml).
- **Needs further tracing:** `Stun_Shot` effect duration and all mode-specific spawn rules.
