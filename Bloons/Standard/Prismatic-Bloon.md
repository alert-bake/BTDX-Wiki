# Prismatic Bloon

## Overview

Prismatic is the fractional type immediately above Rainbow in the ordinary Bloon branch. It has a dedicated sprite and a separate movement multiplier. The source uses `bloonlayer = 8.5`.

## Classification

- **Family:** Intermediate ordinary-branch type
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 8.5`
- **Sprite:** `Prismatic_Bloon_Spr`

## Source-confirmed movement

The normal branch calculates:

```
fast = global.bspeed * 4.4 * (tattered + 1)
path_speed = fast
```

This is before the later status-effect adjustments.

## Pop and Chipper behaviour

The Chipper branch's fractional-layer handler treats a half-step layer by reducing it by 0.5 and producing three instances at the lower layer in the base `pophit = 0` case.

For Prismatic, the source-backed result is **three Rainbow-layer Bloons** in that Chipper interaction. It is not evidence of the ordinary pop result for Prismatic.

## Durability and properties

Prismatic uses the ordinary branch's layer/sprite selection. It is not the same branch as Ceramic or Brick, which use armour-based durability.

## Trivia

Prismatic is the only half-step above Rainbow in the ordinary branch's listed type map. Its 4.4× speed multiplier is lower than Rainbow's 3.8×? No: it is higher. It is also lower than Purple's 5.4×, so the top of the ladder is colourful but not strictly getting faster.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml) and [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).
- **Unconfirmed:** RBE, ordinary pop result, leak damage, and round availability.
