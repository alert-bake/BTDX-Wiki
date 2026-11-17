# Splitting

## Overview

Splitting is a property described by an unverified report as causing a Bloon to produce three Bloons of its counterpart type when popped. The reference also reports that Splitting forms move faster than their ordinary counterparts.

The term needs careful handling because the source contains more than one three-child routine. A Chipper interaction, a Challenge Drones attack, and a Splitting property are not automatically the same mechanic.

## Source-backed fractional-layer behaviour

The Chipper branch examines the fractional part of `bloonlayer`. For half-step types, its base case (`pophit = 0`) reduces the type value by 0.5 and creates two additional instances while retaining the original.

| Input | Lower type | Chipper base-case result |
|---|---|---|
| Orange (1.5) | Red (1) | 3 Reds |
| Cyan (2.5) | Blue (2) | 3 Blues |
| Lime (3.5) | Green (3) | 3 Greens |
| Amber (4.5) | Yellow (4) | 3 Yellows |
| Purple (5.5) | Pink (5) | 3 Pinks |
| Prismatic (8.5) | Rainbow (8) | 3 Rainbows |

This is source-confirmed Chipper behaviour. A non-zero `pophit` changes the amount subtracted. It is not proof that every Splitting property uses the same trigger or exact speed.

## unverified report speed and RBE

An unverified report reports the following values:

| Form | Speed relative to Red | Children | Reported RBE |
|---|---:|---|---:|
| Orange | 137.5% | 3 Red | 4 |
| Cyan | 162.5% | 3 Blue | 7 |
| Lime | 187.5% | 3 Green | 10 |
| Amber | 312.5% | 3 Yellow | 13 |
| Purple | 337.5% | 3 Pink | 16 |
| Prismatic | 275% | 3 Rainbow | 142 |

These figures are unverified report, not derived from the normal-branch speed multipliers. Do not substitute one table for the other: the normal branch's `global.bspeed` multipliers describe its own movement calculation.

## Stacking

an unverified report lists Splitting as compatible with:
- Camo
- Lead
- Regrow
- Tattered
- Shielded
- Static

It also notes that not all combinations can occur simultaneously.

## Trivia

The Chipper's base fractional split is literally "keep the original, then make two more." It is a three-Bloon result without needing to destroy the original and respawn all three. This distinction matters when reading the source.

## Evidence

- **Source-confirmed:** [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).
- **Needs in-game verification:** exact trigger, speed, and property combinations for each Splitting form.
