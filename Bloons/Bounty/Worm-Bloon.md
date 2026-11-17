# Worm Bloon

## Overview

The Worm Bloon Bounty takes place on **Rubber Rug** and has four reported stages. The family uses a dedicated worm path and is described by the community reference as rapidly zigzagging across the screen.

## Encounter and stage progression

1. **Worm Bloon:** one Worm Bloon.
2. **Mega Worm:** higher HP, faster movement, and a stun effect on tower contact.
3. **Iron Rubber Worm:** replaces the ordinary Worm Bloon. It gains Lead but reportedly has less HP while moving faster.
4. **Titanium Terror:** follows an Iron Rubber Worm and gains the H.T.A. property.

Exact stage HP and contact-stun values are not provided by the community excerpt.

## Source cross-check

The base `Worm_Bloon` Create event initializes 5,500 HP multiplied by `global.bpower`, assigns `Worm_Bloon_Path`, and sets `fast = 12 * global.bspeed`. It also starts with a custom path movement state.

Its spawn alarm creates two different allies:
- An Undying Bloon with 60 armour.
- A Winged Bloon with 60 shield.

The alarm increases `spawnspeed` by 0.01 and schedules the next spawn using `900 / spawnspeed`. The source confirms the dedicated path and ally spawning; the precise zigzag geometry is in the path asset and needs separate inspection.

## Community-suggested counters

HeliS, TreeM, and BoomerL are community suggestions, not guaranteed solutions.

## Trivia

The Worm's base movement value is 12× `global.bspeed`, which is unusually high for an enemy with a custom path. The path itself, not a low speed multiplier, gives the movement its distinctive shape.

## Evidence and open questions

- **Source-confirmed:** [Worm_Bloon/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Worm_Bloon/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Worm_Bloon/Step_0.gml), and [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Worm_Bloon/Alarm_0.gml).
- **Needs verification:** path geometry, contact-stun logic, Lead/Titanium forms, and stage-specific health.
