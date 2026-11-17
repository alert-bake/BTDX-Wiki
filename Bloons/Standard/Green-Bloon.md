# Green Bloon

## Overview

The Green Bloon is the third basic colour in the community-documented ordinary sequence. Its normal-branch type value is 3. The community source reports that it reveals a Blue Bloon when popped.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 3`
- **Sprite:** `Green_Bloon_Spr`

## Source-confirmed movement

The normal branch selects `Green_Bloon_Spr` at `bloonlayer = 3` and calculates:

```
fast = global.bspeed * 2.4 * (tattered + 1)
path_speed = fast
```

Status effects can alter the calculated movement value later in the same Step event.

## Reported pop information

- **RBE:** 3 (unverified report).
- **Pop result:** One Blue Bloon (unverified report).
- **HP / hits:** Not established by RBE alone.
- **Leak damage:** Not independently established here.

## Interactions

Green uses the ordinary branch's shared movement/status handling. Its Camo, Regrow, Lead, and shield interactions should be read as property interactions rather than assumed from its colour.

## Trivia

Green's source speed multiplier is 2.4×, while the intermediate Lime layer between Green and Yellow is 3.0×. The fractional layer is a real source-defined type, not just a colour someone made up for a chart.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml).
- **Not independently verified here:** exact hit count, leak damage, and platform-specific differences.
