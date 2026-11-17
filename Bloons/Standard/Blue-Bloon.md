# Blue Bloon

## Overview

The Blue Bloon is the second basic colour in the community-documented ordinary sequence. Its normal-branch type value is 2, and the community source reports that popping it reveals a Red Bloon.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 2`
- **Sprite:** `Blue_Bloon_Spr`

## Source-confirmed movement

When the normal branch has `bloonlayer = 2`, it selects `Blue_Bloon_Spr` and calculates:

```
fast = global.bspeed * 2.0 * (tattered + 1)
path_speed = fast
```

The speed calculation is subsequently affected by status effects in the same Step event. It is not a fixed absolute speed.

## Reported pop information

- **RBE:** 2 (community-reported).
- **Pop result:** One Red Bloon (community-reported).
- **HP / hits:** Not established by RBE alone.
- **Leak damage:** Not independently established here.

## Interactions

The ordinary branch uses the same shared status-effect movement handling for Blue as for Red. The exact effects of Camo, Regrow, Lead, shielding, and damage types are documented separately in [Bloon properties](../Properties.md).

## Trivia

Blue has the cleanest possible nested relationship in the basic sequence: one step down, to Red. The fractional Cyan type sits between Blue and Green in the source's type map, but that does not change the community-reported basic pop relationship.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for RBE and child result.
- **Not independently verified here:** exact hit count, leak damage, and platform-specific differences.
