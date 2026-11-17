# Orange Bloon

## Overview

Orange is an intermediate colour-layer type in BTDX's ordinary Bloon branch. It sits between Red and Blue in the source's numeric type map. Its existence is source-confirmed by the branch's sprite selection; its ordinary-round availability and standalone pop behaviour are not established here.

## Classification

- **Family:** Intermediate ordinary-branch type
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 1.5`
- **Sprite:** `Orange_Bloon_Spr`

## Source-confirmed movement

At layer 1.5, the normal branch selects the Orange sprite and calculates:

```
fast = global.bspeed * 2.2 * (tattered + 1)
path_speed = fast
```

Status effects can modify the result later in the same Step event.

## Pop and Chipper behaviour

The source-backed Chipper routine treats half-step layers specially. In its base case (`pophit = 0`), it reduces the fractional layer by 0.5 and leaves the original plus creates two additional instances at the lower layer.

For Orange, this means **three Red-layer Bloons** in that specific Chipper interaction. It is not evidence that an ordinary Orange pop always creates three Reds.

## Durability and properties

Orange uses the ordinary branch rather than the separate Ceramic or Brick armour branches. The ordinary branch has shared handling for Camo, Lead, Regrow, Tattered, glue, freeze, stun, and distraction. The precise combat interactions should be read from the corresponding property articles.

## Trivia

Orange is the first fractional step in the normal branch: 1.5, between Red's 1 and Blue's 2. It is also one of the Chipper's three-for-one conversions. A Bloon can apparently be a half-step and still have a full-time job.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml) and [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).
- **Unconfirmed:** RBE, ordinary pop result, leak damage, and round availability.
