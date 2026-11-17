# Amber Bloon

## Overview

Amber is an intermediate colour-layer type between Yellow and Pink in the ordinary Bloon branch. The source explicitly selects `Amber_Bloon_Spr` at `bloonlayer = 4.5`.

## Classification

- **Family:** Intermediate ordinary-branch type
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 4.5`
- **Sprite:** `Amber_Bloon_Spr`

## Source-confirmed movement

At layer 4.5, the normal branch calculates:

```
fast = global.bspeed * 5.0 * (tattered + 1)
path_speed = fast
```

This is a pre-status-effect value. Amber's 5.0× multiplier is higher than both Yellow's 4.4× and Pink's 4.8× in the same script.

## Pop and Chipper behaviour

The Chipper's fractional-layer handler reduces a half-step layer by 0.5 in its base case and produces three instances at the lower layer.

For Amber, this produces **three Yellow-layer Bloons** in that Chipper-specific interaction. It does not establish that Amber normally appears as a child of Yellow or that ordinary popping uses the same three-way split.

## Durability and properties

Amber uses the ordinary branch. It is not a separate armour branch like Ceramic or Brick. Shared status-effect movement adjustments and the ordinary property flags apply through the branch's common handling.

## Trivia

Amber is the half-step that sits between Yellow and Pink, and it is actually faster than both according to the normal-branch multipliers: 5.0× versus 4.4× and 4.8×. Yellow's little in-between cousin is not messing around.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml) and [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).
- **Unconfirmed:** RBE, ordinary pop result, leak damage, and round availability.
