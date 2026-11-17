# H.T.A. (Hard Titanium Aircraft)

## Overview

The H.T.A. is a titanium blimp with a source-defined shell coefficient of 60. The community reference reports a high pierce requirement and four Shielded Prismatic children.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| Community-reported hits | 60 |
| Community-reported RBE | 628 |
| Community-reported children | 4 Shielded Prismatics |
| Community-reported speed | Blue-Bloon speed |
| Source branch | `HTA_Branch` |
| Shell formula | `ceil(60 * global.bpower)` |
| Source speed formula | `1.8 * global.bspeed` |

## Source-confirmed behaviour

The source initializes shell using `60 * global.bpower`. When shell falls below 1, it creates four `Shielded_Bloon_Branch` instances. Each child receives a layer derived from the parent's layer minus 60 and a shield value of `30 * global.bpower`.

The branch's raw movement formula is `1.8 * global.bspeed`. This is a source multiplier, not a fixed percentage of Red speed.

## Reported combat behaviour

The community reference reports:
- Attacks with fewer than 10 pierce cannot damage the H.T.A.
- Attacks that connect suffer a nine-pierce penalty.

These special pierce rules have not been independently traced in the source files used for this article. They should remain attributed to the community reference until verified.

## Trivia

The H.T.A. is not a normal shielded Bloon: it is a blimp with its own shell pool, and its death routine creates four Shielded-branch children. The child layer is calculated from the parent's layer rather than hard-coded to a visible colour in this Step event.

## Evidence

- **Source-confirmed:** [HTA_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/HTA_Branch/Step_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for RBE, pierce rules, child naming, and speed description.
- **Needs further tracing:** exact child type, pierce threshold/penalty, and mode availability.
