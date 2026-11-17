# Track Crawler

## Overview

The Track Crawler Bounty takes place on **Bloon Circles X** and has four reported stages. The Track Crawler is a spider-like enemy that moves toward the exit rather than following the ordinary Bloon path. It fires webs that stun towers and can leave persistent hazards.

## Encounter and stage progression

1. **Track Crawler:** spits webs at towers, stunning them, and leaves additional webs behind.
2. **Track Nest:** begins with three Spider Bloons. Each has a passive nest phase that creates web areas, followed by a moving phase in which it heads toward the exit and spits webs. A Track Crawler then appears, followed by two more entering from the upper and lower left edges.
3. **Track Spire:** increases the number of Spider Bloons to five. After them, two corner Track Crawlers appear, followed by a Track Spire with more HP and longer-lasting webs.
4. **Track Swarm:** adds four Spider Bloons. These are initially invulnerable and lose that protection one at a time later. The three earlier Track Crawlers are upgraded to Track Spires.

The stage composition is unverified report.

## Source cross-check

The base `Track_Crawler` Create event initializes 14,400 HP multiplied by `global.bpower`, sets `fast = 0.0475 * global.bspeed`, and schedules its first alarm.

The Step event moves directly toward the `End` object using `move_towards_point`, then derives `path_position` from the distance to that endpoint. This confirms that the base crawler does not use the ordinary Bloon path movement formula.

Its alarm searches for a Monkey within a 300-unit circle. If a target is found, it creates a `Web_Shot` aimed at the target with potency 100, then schedules the next alarm after 90 steps. The exact impact and persistence rules belong to the Web_Shot and web objects.

## Community-suggested counters

TreeM, DartlingM, DartlingR, DartlingS, Dart0 (blocking webs), and PlasmaL are community suggestions, not guaranteed solutions.

## Trivia

The Track Crawler calculates progress from its distance to the End object: `(2000 - distance_to_object(End)) / 2000`. It is using a direct-to-exit movement model, not the ordinary path-position progression.

## Evidence and open questions

- **Source-confirmed:** [Track_Crawler/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Track_Crawler/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Track_Crawler/Step_0.gml), and [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Track_Crawler/Alarm_0.gml).
- **Needs verification:** web persistence, stun duration, Spider Bloon spawn timing, and Track Spire differences.
