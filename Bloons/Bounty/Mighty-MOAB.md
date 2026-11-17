# Mighty MOAB

## Overview

The Mighty MOAB Bounty takes place on **Monkey Fort** and has four reported stages. The community reference describes it as the slowest and toughest Bounty Bloon and says it periodically launches Mini M.O.A.B.s.

## Encounter and stage progression

1. **Mighty MOAB:** one Mighty MOAB, reported at 40,000 HP.
2. **Mighty MOAB MK II:** reported 60,000 HP; launches M.O.A.B.s and Shielded Mini M.O.A.B.s alongside ordinary Mini M.O.A.B.s.
3. **Mighty FIST:** reported 80,000 HP; gains a slowly moving fist projectile that stuns towers on contact.
4. **Mightiest MOAB:** a red-tinted 160,000-HP form that also launches Super Shielded Mini M.O.A.B.s.

These values and later-stage mechanics are community-reported.

## Source cross-check

The base `Mighty_Moab` Create event sets `hitpoints = 27000 * global.bpower`, `dmgpower = 40000`, and `fast = 0.06 * global.bspeed`. Its spawn alarm creates a Mini M.O.A.B. with shell 75 and increments `spawnspeed` by 0.01; the next alarm is scheduled from `360 / spawnspeed`.

This creates a discrepancy with the community-reported 40,000 HP for the first stage. The source value is 27,000 when `global.bpower = 1`; do not overwrite one with the other until the stage-specific setup is traced.

## Community-suggested counters

TreeM, HeliM, DartlingL, and DartlingS are community suggestions, not guaranteed solutions.

## Trivia

The source schedules Mini M.O.A.B. spawns using `360 / spawnspeed`, and the spawn speed rises by 0.01 each cycle. That means the interval shrinks as the encounter continues.

## Evidence and open questions

- **Source-confirmed:** [Mighty_Moab/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Mighty_Moab/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Mighty_Moab/Step_0.gml), and [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Mighty_Moab/Alarm_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for stage HP and later variants.
- **Needs verification:** 27,000 vs 40,000 base HP, later-stage HP, child spawn composition, and fist projectile behaviour.
