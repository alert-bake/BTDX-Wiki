# Super Bloon

## Overview

The Super Bloon Bounty takes place on **Swamp Spirals** and has four reported stages. The boss moves erratically across the screen and fires projectiles that stun towers. an unverified report says it removes lives on each screen pass.

## Encounter and stage progression

1. **Super Bloon:** one 5,000-HP Bloon that fires stunning darts forward.
2. **Super Duper Bloon:** fires two lasers that reportedly double stun time. an unverified report lists 6,500 HP with uncertainty and says the leak penalty becomes four lives.
3. **Super Villain Bloon:** reported 9,000 HP and fires plasma balls with longer stun.
4. **Super Bloon 2:** reported 12,500 HP and uses a Ray of Doom-like stunning beam. It removes more lives the longer it remains on-screen. After it is popped, another Bloon follows the track and uses a similar beam; its reported 4,000 HP and leak penalty are uncertain.

## Source cross-check

The base `Super_Bloon` Create event sets `hitpoints = 5000 * global.bpower`, `dmgpower = 4`, and `fast = 3 * global.bspeed`. It also initializes its route and movement alarms. This supports the reported 5,000 base HP figure when `global.bpower = 1`.

The later Super Bloon forms are separate objects. The inspected `Super_Bloon_2` Destroy event creates a `Super_Bloon_3` instance, confirming a chained follow-up form. Its full attack and HP values still need separate event inspection.

## Unverified suggested counters

TreeM, HeliR, HeliM, WizardS, and BombL are unverified suggestions, not guaranteed solutions.

## Trivia

The Super Bloon family has a chained destruction event: popping one variant can create the next variant. That means "boss defeated" and "encounter finished" are not necessarily the same moment.

## Evidence and open questions

- **Source-confirmed:** [Super_Bloon/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Super_Bloon/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Super_Bloon/Step_0.gml), and [Super_Bloon_2/Destroy_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Super_Bloon_2/Destroy_0.gml).
- **Needs verification:** later variants' HP, projectile stun values, and leak penalties.
