# H.T.A. (Hard Titanium Aircraft)

## Overview

The H.T.A. is a titanium blimp with a source-defined shell coefficient of 60. Unverified details include a high pierce requirement and four Shielded Prismatic children.

## Classification and reported statistics

| Field | Value |
|---|---|
| Class | MOAB-class |
| Unverified hits | 60 |
| Unverified RBE | 628 |
| Unverified children | 4 Shielded Prismatics |
| Unverified speed | Blue-Bloon speed |
| Source branch | `HTA_Branch` |
| Shell formula | `ceil(60 * global.bpower)` |
| Source speed formula | `1.8 * global.bspeed` |

## Source-confirmed behaviour

The source initializes shell using `60 * global.bpower`. When shell falls below 1, it creates four `Shielded_Bloon_Branch` instances. Each child receives a layer derived from the parent's layer minus 60 and a shield value of `30 * global.bpower`.

The branch's raw movement formula is `1.8 * global.bspeed`. This is a source multiplier, not a fixed percentage of Red speed.

## Unverified combat behaviour

The following reported mechanics have not been independently traced in the source files used for this article:
- Attacks with fewer than 10 pierce cannot damage the H.T.A.
- Attacks that connect suffer a nine-pierce penalty.

Keep these mechanics unverified until they can be reproduced in-game or located in the implementation.

## Trivia

The H.T.A. is not a normal shielded Bloon: it is a blimp with its own shell pool, and its death routine creates four Shielded-branch children. The child layer is calculated from the parent's layer rather than hard-coded to a visible colour in this Step event.

## Evidence

- **Source-confirmed:** [HTA_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/HTA_Branch/Step_0.gml).
- **Needs further tracing:** exact child type, pierce threshold/penalty, and mode availability.