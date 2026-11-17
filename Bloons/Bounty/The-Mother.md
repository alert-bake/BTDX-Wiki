# The Mother

## Overview

The Mother Bounty takes place on **Minecarts** and has four reported stages. The boss flies around the map, spawns alien Bloons, and periodically stuns towers.

## Encounter and stage progression

1. **The Mother:** one Mother Bloon with approximately 12,000 HP. It spawns alien Bloons that remove 10 lives if they leak.
2. **The Queen:** grows larger and gains more HP. It spawns Cyclops Bloons near its position; they slowly gravitate toward the exit.
3. **Monster Mom:** returns to its original size, becomes darker, and reportedly rearranges the player's towers about every two minutes. It also creates a Giant Baby Bloon with infinite HP that follows the mouse and blocks projectiles until Monster Mom is popped.
4. **Monster Queen:** combines Stage 3 behaviour with the Queen form.

The stage names and most values are unverified report.

## Source cross-check

The base `The_Mother` Create event initializes 18,000 HP multiplied by `global.bpower`, `strength = 10`, and `fast = 2 * global.bspeed`. Its first alarm adjusts direction slightly and moves the boss. Its second alarm:
- Creates a Creep Bloon with layer and HP derived from the current `strength`.
- Adds stun to nearby Monkey and Necromancer instances, scaling with `strength`.
- Increases `strength` by 1.5.
- Repeats after 900 steps.

The inspected third alarm begins with an immediate `exit;`, so the tower-rearrangement code beneath that statement is unreachable in the current file. the reported claim about tower rearrangement is therefore not confirmed by this event and may describe an older build or another implementation.

The source's base HP of 18,000 × `global.bpower` also differs from the reported approximate 12,000 HP.

## Unverified suggested counters

TreeM, HeliM, and DartlingS are unverified suggestions, not guaranteed solutions.

## Trivia

The tower-rearrangement code exists textually in the third alarm, but the event exits before reaching it. This is exactly why source research needs to inspect control flow, not just search for a function name.

## Evidence and open questions

- **Source-confirmed:** [The_Mother/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/The_Mother/Create_0.gml), [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/The_Mother/Alarm_0.gml), [Alarm_1.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/The_Mother/Alarm_1.gml), and [Alarm_2.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/The_Mother/Alarm_2.gml).
- **Needs verification:** 12,000-vs-18,000 HP discrepancy, Giant Baby behaviour, and whether tower rearrangement is active in another build.
