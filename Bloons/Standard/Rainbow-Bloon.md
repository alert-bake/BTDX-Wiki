# Rainbow Bloon

## Overview

The Rainbow Bloon is a higher ordinary-branch type with `bloonlayer = 8`. The normal branch selects a dedicated Rainbow sprite and applies a 3.8× movement multiplier. The unverified RBE breakdown reports 47.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 8`
- **Sprite:** `Rainbow_Bloon_Spr`

## Source-confirmed movement

```
fast = global.bspeed * 3.8 * (tattered + 1)
path_speed = fast
```

The value is calculated before the later status-effect adjustments. The source clamps values above 9 back to 8 in this branch, which is an implementation detail and not a general rule for other branches.

## Reported information

- **RBE:** 47 (unverified report; unverified).
- **Children:** Not established by the source files checked for this article.
- **HP / hits:** Not established by RBE alone.
- **Leak damage:** Not independently established.

## Interactions

The Chipper branch handles the fractional Prismatic type (8.5) as a three-way reduction to layer 8 in its base case. That makes Prismatic → three Rainbow-layer instances a Chipper-specific result; it does not establish Rainbow's ordinary pop result.

The Challenge Drones routine also has a special case for layer 8 that creates seven Bloon-branch instances. This is specific to that routine and must not be confused with Rainbow's general pop behaviour.

## Trivia

Rainbow has a source-defined half-step above it: Prismatic at 8.5. And, in a separate Challenge Drones routine, the code uses seven spawned instances for a Rainbow-layer case. Two different special systems, two different counts. Bloon documentation: where context matters.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml), [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml), and [Challenge_Drones/Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Challenge_Drones/Alarm_0.gml).
