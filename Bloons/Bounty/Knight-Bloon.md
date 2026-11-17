# Knight Bloon

## Overview

The Knight Bloon Bounty takes place on **Bloon Light Throwback** and has four reported stages. The community reference describes a slow, durable boss surrounded by projectile-blocking shields and accompanied by Sword Bloons.

## Encounter and stage progression

1. **Knight Bloon:** approximately 100,000 HP according to the community source. Sends Sword Bloons toward the exit, each reported as 30 RBE, and can surround itself with Shield Bloons that behave like projectile-blocking rocks.
2. **White Knight:** reportedly sends Sword Bloons twice as quickly, with increased damage and HP, and doubles the number and HP of Shield Bloons.
3. **Paladin Bloon:** gains more HP, faster anti-projectile shields, stronger Sword Bloons, and stronger Shield Bloons. It also spawns a Giant Baby Bloon associated with Monster Mom.
4. **Birthday Delivery:** listed by the source, but no mechanics are supplied.

## Source cross-check

The base `Knight_Bloon` Create event sets HP to `13500 * global.bpower`, base movement to `0.12 * global.bspeed`, and schedules three alarms. Its Step event continuously creates two `Light_Ball` objects travelling in opposite directions around the boss. During the first 20% of its path, its path speed is tripled.

The inspected base-object HP (13,500 before the global multiplier) does not match the community's approximate 100,000 HP. This may reflect stage scaling or a different form; it remains unresolved.

## Community-suggested counters

HeliM, PlasmaL, PlasmaM, IceM, AceR (GZ), and BombL (MA) are community suggestions, not guaranteed solutions.

## Trivia

The Knight's source creates two orbiting Light Balls every Step event, with their directions separated by 180 degrees. The orbit is actively updated rather than being a single static shield sprite.

## Evidence and open questions

- **Source-confirmed:** [Knight_Bloon/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Knight_Bloon/Create_0.gml) and [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Knight_Bloon/Step_0.gml).
- **Needs verification:** 13,500-vs-100,000 HP discrepancy, Light Ball collision rules, shield count, and Stage 4 mechanics.
