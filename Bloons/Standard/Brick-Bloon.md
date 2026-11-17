# Brick Bloon

## Overview

The Brick Bloon is a durable Bloon with its own `Brick_Bloon_Branch`. It is not simply another colour in the ordinary Red-to-Prismatic ladder. Its durability is armour-based, and shielded handling uses a separate large type value.

## Classification

- **Family:** Durable standard-related Bloon
- **Source branch:** `Brick_Bloon_Branch`
- **Shielded type value:** `bloonlayer = 48`
- **Sprite:** `Brick_Bloon_Spr`

## Source-confirmed durability

The Brick Step event calculates:

```
maxarmour = ceil(30 * global.bpower)
```

When `spawned = 0`, the branch initializes `armour` to `maxarmour`. It also clamps armour to the maximum. This is three times the base armour coefficient used by the Ceramic branch (30 versus 10), although actual values depend on `global.bpower`.

In the Shielded Bloon branch, layer 48 receives a maximum shield of `ceil(55 * global.bpower)`. When that shield is depleted, the source creates a Brick Bloon with armour initialized to `30 * global.bpower`.

## Source-confirmed movement

The Brick branch calculates:

```
fast = 2.5 * (tattered + 1) * global.bspeed
path_speed = fast
```

This is a separate formula from the ordinary and Ceramic branches. The Brick Step event also selects appearance frames based on Tattered, Lead, Camo, Regrow, and armour condition.

## Reported information

- **RBE:** 238 (community-reported; unverified).
- **Children:** Not established by the source files checked for this article.
- **Leak damage:** Not independently established.
- **Armour:** Source formula above; actual value scales with `global.bpower`.

## Interactions

The branch has its own status-effect movement calculations. For example, its glue, stun, and distraction formulas differ from the ordinary branch. Do not copy the ordinary Bloon formula into Brick's entry.

The shielded branch treats layer 48 as a Brick-tier form and transforms it into the Brick branch when its shield reaches zero.

## Trivia

Brick is not a normal colour tier. It has its own branch, its own armour coefficient, and a shielded type value of 48. It is less “the next colour after Ceramic” and more “the game has decided this balloon is now masonry.”

## Evidence and sources

- **Source-confirmed:** [Brick_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Brick_Bloon_Branch/Step_0.gml) and [Shielded_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Shielded_Bloon_Branch/Step_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for the RBE.
