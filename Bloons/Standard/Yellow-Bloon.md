# Yellow Bloon

## Overview

The Yellow Bloon is the fourth basic colour in the reported ordinary sequence. Its normal-branch type value is 4. an unverified report reports that it reveals a Green Bloon when popped.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 4`
- **Sprite:** `Yellow_Bloon_Spr`

## Source-confirmed movement

The normal branch selects `Yellow_Bloon_Spr` at `bloonlayer = 4` and calculates:

```
fast = global.bspeed * 4.4 * (tattered + 1)
path_speed = fast
```

The intermediate Amber layer uses `bloonlayer = 4.5` and has a separate multiplier of 5.0×. Both values are relative to `global.bspeed`, before status-effect adjustments.

## Reported pop information

- **RBE:** 4 (unverified report).
- **Pop result:** One Green Bloon (unverified report).
- **HP / hits:** Not established by RBE alone.
- **Leak damage:** Not independently established here.

## Interactions

Yellow uses the normal branch's shared status-effect handling. The presence of an Amber type between Yellow and Pink does not establish that Amber is automatically spawned by an ordinary Yellow pop; the documented three-way Amber-to-Yellow behaviour is specific to Chipper.

## Trivia

Yellow has an intermediate Amber type at layer 4.5. The Chipper's fractional-layer handler can turn an Amber into **three Yellow-layer Bloons** in its base case. That's a special Chipper interaction, not Yellow's normal pop result. The wiki is not allowed to let one attack rewrite the entire family tree.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml) and [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).
