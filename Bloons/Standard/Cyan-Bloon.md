# Cyan Bloon

## Overview

Cyan is an intermediate colour-layer type in the ordinary Bloon branch. It sits between Blue and Green and has its own source-selected sprite and movement multiplier.

## Classification

- **Family:** Intermediate ordinary-branch type
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 2.5`
- **Sprite:** `Cyan_Bloon_Spr`

## Source-confirmed movement

At layer 2.5, the normal branch calculates:

```
fast = global.bspeed * 2.6 * (tattered + 1)
path_speed = fast
```

The result is subject to later status-effect adjustments.

## Pop and Chipper behaviour

The Chipper branch has a fractional-layer rule. With the base `pophit = 0` case, a half-step layer is reduced by 0.5 and represented by three instances at the lower layer: the original and two additional Bloons.

For Cyan, the source-backed Chipper result is **three Blue-layer Bloons**. This is specific to Chipper's interaction and must not be written as the universal result of popping Cyan.

## Durability and properties

Cyan uses the ordinary branch's shared property and movement handling. Its type value does not itself mean that it has Camo, Lead, Regrow, or another modifier.

## Trivia

Cyan is layer 2.5, but its normal-branch movement multiplier is 2.6×. Blue is 2.0× and Green is 2.4×. The half-step is faster than both of its neighbouring integer types in the checked script.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml) and [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).
- **Unconfirmed:** RBE, ordinary pop result, leak damage, and round availability.
