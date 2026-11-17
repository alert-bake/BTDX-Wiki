# Ceramic Bloon

## Overview

The Ceramic Bloon is a durable Bloon handled by its own `Ceramic_Bloon_Branch`, rather than by the ordinary colour branch. The source uses armour to track its durability and a separate type value of 18 in shielded-Bloon handling.

## Classification

- **Family:** Durable standard-related Bloon
- **Source branch:** `Ceramic_Bloon_Branch`
- **Shielded type value:** `bloonlayer = 18`
- **Sprite:** `Ceramic_Bloon_Spr`

## Source-confirmed durability

The Ceramic Step event calculates:

```
maxarmour = ceil(10 * global.bpower)
```

When `spawned = 0`, it initializes `armour` to `maxarmour` and sets the initialization flag. Armour is clamped so it does not exceed the maximum.

The Shielded Bloon branch assigns a maximum shield of `ceil(25 * global.bpower)` to the layer-18 form. When that shield is depleted, the source creates a Ceramic Bloon and initializes its armour to `10 * global.bpower`.

Armour and shield are separate durability pools. A shielded Ceramic-tier Bloon therefore must not be documented as having one combined HP value.

## Source-confirmed movement

The Ceramic branch calculates:

```
fast = 3.8 * (tattered + 1) * global.bspeed
path_speed = fast
```

Glue, freeze, stun, and distraction have branch-specific effects after this calculation. Ceramic's stun and distraction handling is not identical to the ordinary branch.

## Reported information

- **RBE:** 104 (unverified report; unverified).
- **Children:** Not established by the source files checked for this article.
- **Leak damage:** Not independently established.
- **Armour:** Source formula above; actual value scales with `global.bpower`.

## Interactions

The source selects Ceramic damage-state frames from the ratio of current armour to maximum armour. This gives Ceramic a visible armour-damage progression.

Camo, Lead, Regrow, and Tattered can affect the sprite frame selected by the branch. The precise attack-type interactions still need a separate collision/damage audit.

## Trivia

Ceramic does **not** sit in the ordinary branch's fractional colour ladder. It uses its own branch and an armour pool. Yellow has Amber at layer 4.5; Ceramic is layer 18 in shielded handling. No, Ceramic does not secretly owe us three Yellow Bloons. That three-way fractional split belongs to Chipper's handling of intermediate types.

## Evidence and sources

- **Source-confirmed:** [Ceramic_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Ceramic_Bloon_Branch/Step_0.gml) and [Shielded_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Shielded_Bloon_Branch/Step_0.gml).
