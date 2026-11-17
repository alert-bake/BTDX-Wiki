# Pink Bloon

## Overview

The Pink Bloon is the fifth basic colour in the ordinary reported ordinary sequence. Its normal-branch type value is 5. an unverified report reports that it reveals a Yellow Bloon when popped.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 5`
- **Sprite:** `Pink_Bloon_Spr`

## Source-confirmed movement

The normal branch selects `Pink_Bloon_Spr` at `bloonlayer = 5` and calculates:

```
fast = global.bspeed * 4.8 * (tattered + 1)
path_speed = fast
```

The script also contains a special clamp for values between 5 and 5.5, assigning them to 5. This is an implementation detail worth preserving when documenting fractional types.

## Reported pop information

- **RBE:** 5 (unverified report).
- **Pop result:** One Yellow Bloon (unverified report).
- **HP / hits:** Not established by RBE alone.
- **Leak damage:** Not independently established here.

## Interactions

Pink uses the normal branch's shared movement and status-effect code. Purple at layer 5.5 is a distinct intermediate type and should not be treated as a Pink property.

## Trivia

Pink's normal-branch speed multiplier is 4.8×, but the intermediate Purple at 5.5 is 5.4×. The source is perfectly happy to put a faster half-step between two colours; the colour order is not a speed ranking.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml).
