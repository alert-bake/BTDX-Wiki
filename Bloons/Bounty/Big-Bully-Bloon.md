# Big Bully Bloon

## Overview

The Big Bully family is a five-stage Bounty encounter on **Monkey Meadows**. The community reference describes five colour-coded Bully Bloons, with leak penalties based on colour and an increasing penalty after repeated leaks. It also reports that taking hits accelerates the family.

## Encounter and stage progression

1. **Big Bully Bloon:** one Pink BBB, reported at 3,000 HP.
2. **Big Bully Family:** one of each colour: Red 500 HP, Blue 1,000, Green 1,500, Yellow 2,000, Pink 2,500.
3. **Big Rage Bloon:** one of each colour. The Pink form glows red, has 5,000 HP, and fires a rapid stunning projectile.
4. **Big Bully Rage:** one of each colour plus a second Pink. Both Pinks fire rapid stun projectiles. One has a devil aura, 8,000 HP, an area stun triggered by each hit, and an initial 10-life leak penalty.
5. **Rage God:** the aura Bloon grows to a reported 20,000 HP and fires stunning fingers that pierce towers. Its speed boost reportedly accelerates other Bloons, up to 3×. It initially removes 20 lives and gains another 10-life penalty on each later leak.

All stage values and mechanics above are unverified report.

## Source cross-check

The base `Big_Bully_Bloon` Create event initializes `hitpoints` and `maxpoints` to `3000 * global.bpower`, sets `dmgpower = 4`, and starts with `fast = 1 * global.bspeed`. Its Step event assigns `path_speed = fast` and includes a gradual speed adjustment.

This supports the 3,000 base HP figure when `global.bpower = 1`, but the colour variants and later Rage forms require their own source paths. Do not assume the base object's values apply to every stage.

## Community-suggested counters

TreeM, EngineerS, AceM, MortarL, TreeM/TreeR, and ChipperL are listed by the community as suggestions. These are not guaranteed solutions or the only viable towers.

## Trivia

The base object has a type identifier `bigbloon = 10001`, not an ordinary Bloon layer value. This is a Bounty boss object, not a Pink Bloon with a comically large health bar.

## Evidence and open questions

- **Source-confirmed:** [Big_Bully_Bloon/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Big_Bully_Bloon/Create_0.gml) and [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Big_Bully_Bloon/Step_0.gml).
- **Needs verification:** every colour variant's HP, Rage God attack behaviour, acceleration formula, and repeat-leak penalties.
