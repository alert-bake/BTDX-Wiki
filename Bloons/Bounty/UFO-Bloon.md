# UFO Bloon

## Overview

The UFO Bounty takes place on **Bloon Oasis** and has four reported stages. UFOs move erratically and drain the player's money while active. The community reference says that once money reaches zero, the drain switches to lives.

## Encounter and stage progression

1. **UFO Bloon:** one green UFO with a reported 2,000 HP.
2. **UFO Squad:** five UFOs; one has a blue aura, 2,250 HP, and absorbs projectiles.
3. **UFO Cluster:** eight UFOs spawn in a flower formation. Four have blue auras and four are yellow; each is reported to have 1,500 HP.
4. **UFO Mothership:** begins with the Cluster formation, then spawns a large pink 20,000-HP mothership. It drains lives and creates 1,000-HP pink UFOs every 13.33 seconds; smaller UFOs reportedly drain both money and lives.

Stage statistics and the mothership description are community-reported.

## Source cross-check: drain and movement

The base `UFO_Bloon` Create event initializes `hitpoints = 2000 * global.bpower`, `drain = 1`, and movement speed `1 * global.bspeed`. Its alarms control movement and drain progression.

The Step event applies the following per-step drain:
- If `global.money > 0`, subtract `0.1 * drain` from money.
- Otherwise, subtract `0.005 * drain` from lives.

The drain alarm increases `drain` by `1/12` every 150 steps. Another alarm changes direction, selects a random vertical position, and sets movement speed to `2 * global.bspeed + random(6 * global.bspeed)`.

The source therefore confirms a gradually increasing drain and the money-to-lives transition. It does not establish the community page's ambiguous wording about a percentage-based life-drain rate.

## Community-suggested counters

TreeM, TackR, HeliM, and WizardS are community suggestions, not guaranteed solutions.

## Trivia

The drain is step-based and scales with the `drain` variable. It is not a single fixed amount per second written directly into the UFO's Step event.

## Evidence and open questions

- **Source-confirmed:** [UFO_Bloon/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/UFO_Bloon/Create_0.gml), [Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/UFO_Bloon/Step_0.gml), [Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/UFO_Bloon/Alarm_0.gml), and [Alarm_1.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/UFO_Bloon/Alarm_1.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for stage composition and counter suggestions.
- **Needs verification:** blue-aura projectile absorption, Mothership HP, child spawn interval, and exact life-drain interpretation.
