# Sun-Blessed / Solar

## Overview

Sun-Blessed Bloons are reported to appear in the Solar Storm mission. an unverified report describes them as Bloons that fire a stunning projectile, move more slowly than their original form, and do not have shields.

The source object is named `Solar_Bloon_Branch`. The wiki treats **Sun-Blessed** and **Solar** as names for this same documented form unless further evidence establishes a distinction.

## Source-confirmed implementation

The Solar Step event:
- Selects an ordinary Bloon sprite according to its layer.
- Uses `image_index = 9` when `tattered = 0`, selecting the tenth sprite frame.
- Uses `image_index = 1` when Tattered.
- Calculates movement with Solar-specific multipliers rather than copying the normal branch's exact values.

The Solar alarm sets a range of 120 and a repeat interval of 150 steps. It searches for a Monkey in range and, if a target exists, creates a `Sun_Stun_Shot` aimed toward that Monkey. Projectile potency is calculated as:

```
round(10 + (3 * bloonlayer))
```

This confirms the source's target search and projectile setup. The exact effect and duration must be read from `Sun_Stun_Shot`.

## Reported behaviour

- Appears in Solar Storm.
- Fires a stunning projectile.
- Has no shield.
- Moves more slowly than the original Bloon.
- Can apply to multiple Bloon layers.

The Solar branch's own speed formulas should be compared against the relevant normal-branch type before making a general "slower" claim for every type.

## Stacking

an unverified report lists no stacking combinations.

## Trivia

The Solar branch selects sprite frame index 9 when the Bloon is not Tattered. Sprite indices are zero-based, so that is the **tenth frame**. This is what identified the previously mysterious tenth recurring sprite state as Solar, rather than the speculative Ditto interpretation.

## Evidence

- **Source-confirmed:** [Solar_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Bloon_Branch/Step_0.gml) and [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Bloon_Branch/Alarm_0.gml).
- **Needs further tracing:** `Sun_Stun_Shot` impact effect, exact duration, and mission spawn rules.
