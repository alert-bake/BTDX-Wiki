# Purple Bloon

## Overview

Purple is an intermediate colour-layer type between Pink and Black in the ordinary Bloon branch. The source gives it a dedicated sprite and the highest normal-branch movement multiplier in the listed ordinary colour sequence.

## Classification

- **Family:** Intermediate ordinary-branch type
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 5.5`
- **Sprite:** `Purple_Bloon_Spr`

## Source-confirmed movement

The normal branch selects Purple at layer 5.5 and calculates:

```
fast = global.bspeed * 5.4 * (tattered + 1)
path_speed = fast
```

The script also contains a nearby clamp that changes values greater than 5 and less than 5.5 to 5. The exact value 5.5 selects Purple.

## Pop and Chipper behaviour

The Chipper's fractional-layer handler reduces a half-step layer by 0.5 in its base case and creates two additional instances alongside the original.

For Purple, the resulting three instances use the Pink layer. This is a Chipper-specific result, not a universal ordinary pop rule.

## Durability and properties

Purple uses the ordinary branch. Its colour/type value does not by itself establish any property such as Camo, Lead, or Regrow. The ordinary branch's status-effect movement logic is applied after its base multiplier.

## Trivia

Purple has the highest movement multiplier in the ordinary branch's documented colour map: 5.4×. It is a half-step between Pink and Black, and it outruns both in the raw multiplier table. The hierarchy is not a speed chart.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml) and [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).
- **Unconfirmed:** RBE, ordinary pop result, leak damage, and round availability.
