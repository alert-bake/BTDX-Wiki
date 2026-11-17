# Lime Bloon

## Overview

Lime is an intermediate colour-layer type between Green and Yellow in the ordinary Bloon branch. Its identity is established by the source's sprite-selection and movement code.

## Classification

- **Family:** Intermediate ordinary-branch type
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 3.5`
- **Sprite:** `Lime_Bloon_Spr`

## Source-confirmed movement

At layer 3.5, the normal branch calculates:

```
fast = global.bspeed * 3.0 * (tattered + 1)
path_speed = fast
```

This is before the later status-effect adjustments.

## Pop and Chipper behaviour

In the Chipper's base fractional-layer case (`pophit = 0`), the source subtracts 0.5 from the half-step layer and produces three instances at the resulting lower layer.

For Lime, that means **three Green-layer Bloons** in the Chipper interaction. This is not a general pop rule for Lime.

## Durability and properties

Lime is handled by the ordinary branch, not by the separate Ceramic or Brick armour systems. Shared status-effect handling includes glue, freeze, stun, and distraction; property flags such as Camo, Lead, and Regrow are tracked separately.

## Trivia

Lime's multiplier is 3.0×, while Green is 2.4× and Yellow is 4.4×. The intermediate layer is not merely decorative: it has its own type value, sprite, and movement calculation.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml) and [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).
- **Unconfirmed:** RBE, ordinary pop result, leak damage, and round availability.
