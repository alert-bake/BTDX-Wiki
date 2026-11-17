# Horror Bloon

## Overview

The Horror Bloon Bounty takes place on **The Depths** and has four reported stages. The encounter begins with stationary enemies in the centre of the map; if they are not dealt with quickly enough, the community reference says they can reduce the player's lives to one.

## Encounter and stage progression

1. **Horror Bloon:** two Horror Bloons stand in the centre from round 1. After a time threshold, the player's lives reportedly fall to a permanent one.
2. **Darkness Bloon:** four Horror Bloons occupy the middle. After a certain round, the two outer Bloons spawn onto the tracks with their remaining HP. A spotlight effect similar to Necropolis also activates after a time threshold.
3. **Demonic Bloon:** the two inner Horror Bloons gain a single-target projectile that stuns a tower.
4. **True Horror:** adds another Horror Bloon that blocks the central rock and has substantially more HP than the others.

The stage effects and one-life penalty are unverified report.

## Source cross-check

The source contains a `Horror_Bloon_X` object with:
- 12,666 HP and 12,666 maximum HP.
- `dmgpower = 6666`.
- `fast = 0.045 * global.bspeed`.
- A long initial alarm and a separate short alarm.

Its Step event clamps one alarm when the Bloon falls below half health. Another alarm starts `Prison_Break_Path`, positions the Bloon based on its remaining health, marks it as unchained, and schedules another delayed event. This supports a stationary-to-moving encounter phase, but it does not by itself confirm the community's permanent one-life effect.

## Community-suggested counters

TreeM, DartlingM, DartlingS, HeliM, and WizardS are community suggestions, not guaranteed solutions.

## Trivia

The Horror object uses its remaining-health ratio to calculate its new path position when it becomes unchained. Its transition is tied to its health state, not just a fixed "walk after timer" instruction.

## Evidence and open questions

- **Source-confirmed:** [Horror_Bloon_X/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Horror_Bloon_X/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Horror_Bloon_X/Step_0.gml), and [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Horror_Bloon_X/Alarm_0.gml).
- **Needs verification:** exact stage-to-object mapping, timer thresholds, spotlight effect, and whether the one-life effect is reversible.
