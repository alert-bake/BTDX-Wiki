# tDoM (the Destroyer of Monkeys)

## Overview

The tDoM Bounty takes place on **Graveyard**. It is described by the community reference as a M.O.A.B.-like enemy that uses the longer route and can destroy towers with a devil blade. The community page lists exclusions for Trees, Villages, and right-side Alchemist upgrades.

## Encounter and stage progression

1. **tDoM:** one tDoM.
2. **tDoM Second Form:** after the normal form, a turbo-boosted second tDoM arrives and reportedly removes 200 lives if it leaks.
3. **tDoM Zero Form:** gains a shield layer with approximately as much HP as the tDoM itself. The second-form enemy also has more HP.
4. **tDoM Full Power:** all forms gain more HP and use monkey-nuke projectiles that destroy groups of towers.

The stage descriptions and leak penalty are community-reported.

## Source cross-check

The base `tDoM` Create event selects a path based on the current map/track and sets a base HP value of 40,000 before applying several `global.destroyerenable` variants:
- Variant 1 or 2: 51,000 × `global.bpower`.
- Variant 3: 46,000 × `global.bpower`.
- Variant 4: 60,000 × `global.bpower`.

The base movement value is `0.0775 * global.bspeed`. When the tDoM is destroyed, the source checks `global.destroyerenable`: the first variant grants the Bounty reward, while higher variants create a `tDoM_Phase_Two` instance.

This confirms a multi-phase source implementation, but the community's tower-destruction attacks and exact stage labels need separate event inspection.

## Community-suggested counters

EngineerS, Dart0 (blocking), TreeM, VillageM, and BombL (MA) are community suggestions, not guaranteed solutions.

## Trivia

The tDoM's path setup contains explicit handling for many different maps. It is not hard-coded to the Graveyard route alone; the active track determines which path logic is selected.

## Evidence and open questions

- **Source-confirmed:** [tDoM/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/tDoM/Create_0.gml) and [Destroy_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/tDoM/Destroy_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for stage descriptions, leak penalty, and counters.
- **Needs verification:** devil-blade targeting exclusions, shield values, monkey-nuke behaviour, and the exact relationship between source variants and four Bounty stages.
