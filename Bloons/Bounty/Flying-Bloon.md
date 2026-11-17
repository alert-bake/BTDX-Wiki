# Flying Bloon

## Overview

The Flying Bloon Bounty takes place on **Sky Battles** and has four reported stages. The boss circles the central cloud, emits gusts that affect Bloon movement, and releases airborne allies.

## Encounter and stage progression

1. **Flying Bloon:** circles the middle cloud and fires gust projectiles that accelerate Bloons they touch. When popped, it releases Phoenix and Angel Bloons, each reported as 30 RBE.
2. **Higher Bloon:** increases the boss and ally health, spawns allies more quickly, and makes gusts push Bloons farther.
3. **Ascended Bloon:** follows a Higher Bloon. It reportedly has more HP, stronger Phoenix Bloons, and more powerful gusts.
4. **Almighty Bloon:** has more HP and creates a rain of gusts that push Bloons forward and block projectiles. It spawns after a Higher Bloon.

Stage descriptions and RBE values are unverified report.

## Source cross-check

The base `Flying_Bloon` Create event initializes 5,500 HP multiplied by `global.bpower`, a base speed of `2 * global.bspeed`, and a custom path. When `global.flyingenable > 1`, the same Create event instead sets its HP to 4,000 multiplied by `global.bpower`; this differs from the reported description of later stages having more HP and needs investigation.

Its spawn alarm creates an Undying Bloon with 60 armour and a Winged Bloon with 60 shield. The spawn rate increases over time. A second alarm creates six Wind Gust projectiles in a spread and also increases the spawn rate.

## Unverified suggested counters

PlasmaM, IceM, VillageM, BuccS, BuccM, WizardR, and SpacM are unverified suggestions, not guaranteed solutions.

## Trivia

The Flying Bloon's source creates two different ally types per spawn cycle: an Undying Bloon with armour and a Winged Bloon with a shield. They are not simply two copies of the same airborne enemy.

## Evidence and open questions

- **Source-confirmed:** [Flying_Bloon/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Flying_Bloon/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Flying_Bloon/Step_0.gml), [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Flying_Bloon/Alarm_0.gml), and [Alarm_1.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Flying_Bloon/Alarm_1.gml).
- **Needs verification:** why later `flyingenable` values reduce the base object's HP, and exact Phoenix/Angel spawn rules.
