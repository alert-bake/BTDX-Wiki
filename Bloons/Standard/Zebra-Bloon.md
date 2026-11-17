# Zebra Bloon

## Overview

The Zebra Bloon is an ordinary-branch type with its own sprite and movement multiplier. The source assigns it `bloonlayer = 7`. The community RBE breakdown reports an RBE of 23, but that value has not been independently confirmed here.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 7`
- **Sprite:** `Zebra_Bloon_Spr`

## Source-confirmed movement

At layer 7, the normal branch selects the Zebra sprite and calculates:

```
fast = global.bspeed * 2.8 * (tattered + 1)
path_speed = fast
```

The later status-effect code can change the final movement value.

## Reported information

- **RBE:** 23 (unverified report; unverified).
- **Children:** Not established by the source files checked for this article.
- **HP / hits:** Not established by RBE alone.
- **Leak damage:** Not independently established.

## Interactions

Zebra is a distinct type value, not a combination of the Black and White flags in the ordinary branch. The exact immunities and property combinations need a separate damage/targeting trace.

The Challenge Drones routine has a special case for `bloonlayer = 7` that creates three Bloon-branch instances. That is behaviour of the Challenge Drones routine, not evidence that every Zebra pop creates three children.

## Trivia

Zebra's source multiplier is 2.8×, exactly the same as White's in the ordinary branch. The two Bloons still have different layer values, sprites, and potentially different damage interactions. Speed equality does not make them twins.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml) and [Challenge_Drones/Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Challenge_Drones/Alarm_0.gml).
