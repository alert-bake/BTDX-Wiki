# Clown Bloon

## Overview

The Clown Bloon Bounty takes place on **Omega River** and has five reported stages. The boss moves across the screen and uses random abilities to disrupt towers and Bloon movement. an unverified report says each ability makes it faster and increases ability frequency.

## Encounter and stage progression

1. **Clown Bloon:** reported 5,000 HP. It can spawn six poppable 40-HP Star Balls that block projectiles, or teleport Bloons forward by 10% of their remaining path. Initial ability interval is about 12.63 seconds.
2. **Joker Bloon:** an 8,000-HP Joker joins a 2,500-HP Clown. The Joker can spawn six 70-HP bombs that remove 10 lives if not popped within 13 seconds, and redirect Bloons onto a random Beginner or Intermediate map path. Star Balls rise to eight and 60 HP. Initial cooldown is about 11.16 seconds.
3. **Demon Clown:** replaces the Joker with a 12,300-HP form and adds another random ability. Path redirection can select any map. The Clown has 4,000 HP.
4. **Rubber Terror:** a faster, bulkier Demon Clown with 15,300 HP. Star Balls become 80-HP Demon Balls that stun nearby towers; bombs have 90 HP. Initial cooldown is about 10.62 seconds.
5. **Trickster God:** follows two normal 3,000-HP Clowns. It has 27,300 HP and adds Hungry Hungry Bloons (999 HP) and Monkey Terrors (400 HP), both of which stun towers and block most projectiles. Demon Balls reach 150 HP; bombs reach 200 HP and stun on contact. Initial cooldown is about 17.14 seconds.

The stage details are unverified report.

## Source cross-check

The base `Clown_Bloon` Create event sets HP according to `global.clownenable`: 5,000, 2,500, 4,000, 5,000, or 3,000 multiplied by `global.bpower`. Its base movement value is `3.8 * global.bspeed`.

The movement alarm changes direction, chooses a random vertical position, sets movement speed from `fast`, and increases `fast` by 0.06. The ability alarm can create six `Star_Ball` objects with 40 shield, or create `Joker_Effect` projectiles and redirect the global track selection. The source confirms the random ability structure, but later-stage variants have their own implementation and must be checked separately.

## Unverified suggested counters

TreeM, WizardS, HeliM, BuccM, SubS, and AceL are unverified suggestions, not guaranteed solutions.

## Trivia

The source's base Clown has a `fast` multiplier of 3.8× global speed. Its movement alarm then increments that value by 0.06, so the Clown's speed is not a single immutable constant.

## Evidence and open questions

- **Source-confirmed:** [Clown_Bloon/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Clown_Bloon/Create_0.gml), [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Clown_Bloon/Alarm_0.gml), [Alarm_1.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Clown_Bloon/Alarm_1.gml), and [Alarm_2.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Clown_Bloon/Alarm_2.gml).
- **Needs verification:** later-stage HP, bombs' exact leak conditions, and all ability cooldowns.
