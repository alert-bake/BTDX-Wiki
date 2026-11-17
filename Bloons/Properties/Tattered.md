# Tattered

## Overview

Tattered is a Bloon property represented by a separate state on ordinary Bloons. The community reference describes Tattered Bloons as moving at twice their normal speed and losing the property after one layer is popped.

## Source-confirmed movement and appearance

The ordinary branch calculates movement using:

```
fast = global.bspeed * type_multiplier * (tattered + 1)
```

When `tattered = 1`, the Tattered multiplier is 2. The normal branch also selects a different sprite frame when `tattered = 1`.

This is directly supported by the source. It is not a universal speed formula for every Bloon branch: Ceramic, Brick, MOAB-class, Static, and Solar forms have their own movement code and must be checked independently.

## Reported behaviour

- Moves at twice the ordinary counterpart's speed.
- Loses the Tattered state after one layer is popped.
- Tattered Purple is described by the community reference as the fastest Bloon.

The first two statements are consistent with the source's ordinary-branch multiplier and sprite state, but the exact point at which the state is cleared should be verified in the relevant damage/transformation path. The "fastest" claim is community-reported and depends on the game mode's global speed and which branches are being compared.

## Stacking

The community reference lists Tattered as compatible with:
- Regrow
- Splitting

Tattered forms also appear in reported MOAB child compositions, including Tattered Camo Lead Brick children.

## Trivia

The code does not apply a 2× multiplier by adding a magic speed bonus. It multiplies by `tattered + 1`. In the ordinary branch, that means the same formula handles both states: 1× when false, 2× when true. Extremely tidy for a variable named `tattered`.

## Evidence

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml), [Research: Bloon variables](../../Research/Finding%20about%20Bloons.md).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for the property description and stacking.
- **Needs in-game verification:** when the flag is removed, and whether every special branch applies the same speed effect.
