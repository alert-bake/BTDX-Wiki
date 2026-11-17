# White Bloon

## Overview

The White Bloon is a distinct ordinary Bloon type in BTDX. It is not an alternate sprite for Black: the normal branch assigns it the separate value `bloonlayer = 6.1` and selects `White_Bloon_Spr`.

## Classification

- **Family:** Standard / ordinary Bloon
- **Source branch:** `Normal_Bloon_Branch`
- **Source type value:** `bloonlayer = 6.1`
- **Sprite:** `White_Bloon_Spr`

## Source-confirmed movement

The normal branch calculates:

```
fast = global.bspeed * 2.8 * (tattered + 1)
path_speed = fast
```

This is the pre-status-effect movement value. White's multiplier is 2.8×, compared with Black's 2.4×.

## Reported pop information

- **RBE:** 11 (unverified report).
- **Pop result:** Not established by the sources checked for this article.
- **HP / hits:** Do not infer from the reported RBE.
- **Leak damage:** Not independently established here.

## Interactions

The exact damage immunities and child behaviour should be confirmed in BTDX itself. A White Bloon sharing a reported RBE and broad tier with Black does not mean that it shares Black's reported two-Pink split.

## Trivia

Black and White are almost neighbours in the source's type map: 6 and 6.1. That tiny decimal is enough for the normal branch to select a different sprite and a different speed multiplier. Tiny number, entirely different Bloon identity.

## Evidence and sources

- **Source-confirmed:** [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml).
- **Not independently verified here:** child composition, damage immunities, hit count, and leak damage.
