# Red Bloon

## Overview

The Red Bloon is the base ordinary Bloon type in BTDX's normal Bloon branch. It is the lowest value in the ordinary branch's `bloonlayer` mapping and is the reference point used by unverified RBE tables.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 1`
- **Sprite:** `Red_Bloon_Spr`

## Source-confirmed behaviour

The normal branch selects `Red_Bloon_Spr` when `bloonlayer = 1`. Its calculated movement value is:

```
fast = global.bspeed * 1.6 * (tattered + 1)
path_speed = fast
```

This is the value before the later glue, freeze, stun, and distraction adjustments in the same Step event. It is not an absolute speed: `global.bspeed` changes with game settings and modes.

The Create event initializes the ordinary branch's common fields, including glue, freeze, shielded, bigbloon, electric, camo, lead, regrow, tattered, stun, distraction, corrosion, and radiation. It initializes `bloonlayer` and `bloonmaxlayer` to zero; a spawner or transformation assigns the actual type value.

## Reported pop information

- **RBE:** 1 (unverified report).
- **Children:** None; it is the base entry of the reported ordinary hierarchy.
- **HP / hits:** Do not treat the RBE value as a universal number of hits. Actual damage depends on the attack and the active game rules.
- **Leak damage:** Not independently established in this article.

## Interactions

- **Tattered:** the normal branch multiplies the calculated speed by `tattered + 1`. With `tattered = 1`, that multiplier is 2. This is a code observation, not a judgement about intended balance.
- **Status effects:** glue, freeze, stun, and distraction modify movement later in the same Step event.
- **Other properties:** Camo, Lead, and Regrow are represented by flags and/or separate branches. Their exact targeting and damage rules belong in [Bloon properties](../Properties.md).

## Trivia

The Red Bloon is the only basic colour whose sprite metadata has an extra twelfth frame in the current sprite inventory. The first eleven frame labels are shared with the recurring low-tier lineup; the extra frame's identity is still unconfirmed. A suspicious extra frame is not enough evidence to name a secret Bloon.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Create_0.gml) and [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml).
- **Not independently verified here:** exact hit count, leak damage, and platform-specific differences.
