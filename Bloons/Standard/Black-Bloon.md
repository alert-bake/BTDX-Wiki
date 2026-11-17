# Black Bloon

## Overview

The Black Bloon is a standard Bloon type in BTDX. The ordinary branch assigns it `bloonlayer = 6`. The community source places it at the same broad tier as White and reports an RBE of 11.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 6`
- **Sprite:** `Black_Bloon_Spr`

## Source-confirmed movement

The normal branch selects `Black_Bloon_Spr` at layer 6 and calculates:

```
fast = global.bspeed * 2.4 * (tattered + 1)
path_speed = fast
```

The speed is modified later by applicable status effects. Black's multiplier is lower than Pink's 4.8× and Purple's 5.4×; colour tier does not imply monotonically increasing speed.

## Reported pop information

- **RBE:** 11 (unverified report).
- **Pop result:** Two Pink Bloons (unverified report).
- **HP / hits:** RBE is not a universal hit count.
- **Leak damage:** Not independently established here.

## Interactions

Black and White are distinct normal-branch type values: Black is 6 and White is 6.1. Their shared reported tier does not prove identical child composition, immunities, or damage interactions. Those details should be documented separately.

## Trivia

Black is one of the rare cases where the unverified report RBE is much larger than the layer value might make a reader expect. The source's `bloonlayer = 6` is a type selector, not a hidden "six hits" label.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml).
- **Not independently verified here:** exact damage immunities, hit count, and leak damage.
