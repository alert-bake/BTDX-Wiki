# Blooming Bloon

## Overview

The Blooming Bloon Bounty takes place on **Autumn Acres** and has four reported stages. The boss resembles a flower, relocates around the map, and emits groups of Bloons. The community reference says its movement accelerates over time.

## Encounter and stage progression

1. **Blooming Bloon:** appears from the ground, fires Bloon clusters, relocates, and repeats. Its health pool is substantial.
2. **Gardening Bloon:** weaker versions appear on selected rounds before the main Blooming Bloon. They have less HP and release fewer Bloons per appearance.
3. **Blossom Bloon:** a Venus-flytrap form that can consume the newest tower. The community source says defeating this form is sufficient to clear the stage.
4. **Earth Spirit:** a larger Blooming form with colourful petals. It reportedly releases very large clusters ranging from Tattered Yellows to Splitting Rainbows.

The exact stage health and cluster compositions are not fully established by the source excerpt.

## Source cross-check

The base `Blooming_Bloon` Create event sets its HP according to `global.flowerenable`: 3,900, 5,200, 6,500, or 6,500 multiplied by `global.bpower`. It starts with `fast = 3`, then uses alarms to control its actions.

The alarm code creates groups of `Bloom_Branch` instances. Depending on a randomly selected pattern, it creates:
- 15 Bloon branches with a fractional layer based on the boss's remaining HP.
- 18 Tattered Green-layer branches.
- 4 Pink-layer branches.

A separate alarm relocates the boss to a new random position and increases its `fast` value by 0.075. The source confirms relocation and increasing speed, while the exact cluster patterns are more specific than the community summary.

## Community-suggested counters

TreeM, TackR, DartlingS, WizardS, AceL, BoomerL, BombM, and MortarM are community suggestions, not guaranteed solutions.

## Trivia

The Blooming Bloon's source does not choose one fixed flower-bullet pattern. Its alarm randomly selects among three cluster recipes, and the recipes use different child counts and layer values.

## Evidence and open questions

- **Source-confirmed:** [Blooming_Bloon/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Blooming_Bloon/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Blooming_Bloon/Step_0.gml), [Alarm_1.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Blooming_Bloon/Alarm_1.gml), and [Alarm_2.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Blooming_Bloon/Alarm_2.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for stage descriptions and counter suggestions.
- **Needs verification:** tower-consumption trigger, full stage progression, and exact child-layer interpretation for each pattern.
