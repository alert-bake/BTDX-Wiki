# Annoying Bloon

## Overview

The Annoying Bloon Bounty takes place on **Shade Woods** and has five reported stages. Its central mechanic is rapid life drain, with later stages adding regeneration, D.D.T.-like enemies, and an H.T.A.-property variant.

## Encounter and stage progression

1. **Annoying Bloon:** one Bloon follows the track and drains lives quickly.
2. **Irritating Bloon:** regenerates HP very quickly.
3. **Frustrating Bloon:** three reported 200-HP Bloons with D.D.T. properties appear first; each removes 15 lives if it leaks. An Irritating Bloon follows.
4. **4 Letter Word Bloon:** repeats the earlier pattern but ends with a giant 3,000-HP Annoying Bloon that drains lives much faster.
5. **Giga Emoji:** gives Bloons crying-face emojis and makes them faster. An unverified value lists a drain of 0.55 lives per second when more than ten are on-screen. An Annoying H.T.A. Bloon also appears. The listed completion rewards are 1,100 Monkey Money, 11 Bloon Points, and 550,000 XP.

These stage details and rewards have not been independently verified.

## Source cross-check

The source contains several candidate objects associated with this family:
- `Emoji_God` initializes 15,000 HP multiplied by `global.bpower` and a base speed of `2.5 * global.bspeed`.
- `Terrible_1` initializes 600 HP multiplied by `global.bpower`.
- `DDT_Terrible` initializes 300 HP and a base speed of `1.8 * global.bspeed`.

The source identifiers are not enough to prove which exact object corresponds to every reported stage. There is also a discrepancy between the listed 200-HP D.D.T.-property enemies and the 300 HP assigned by the inspected `DDT_Terrible` Create event.

## Unverified suggested counters

TreeM, TreeL, TreeR, VillageM, HeliM, HeliL, ChargeL, and TackR (for Stage 1) are unverified suggestions, not guaranteed solutions.

## Trivia

The source's `Emoji_God` object has 15,000 HP before the global power multiplier, while `DDT_Terrible` is initialized at 300 HP. The unverified stage description's 200-HP figure does not match that object as inspected.

## Evidence and open questions

- **Source-confirmed candidate objects:** [Emoji_God/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Emoji_God/Create_0.gml), [Terrible_1/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Terrible_1/Create_0.gml), and [DDT_Terrible/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/DDT_Terrible/Create_0.gml).
- **Needs verification:** exact mapping between stage names and source objects, the 200-vs-300 HP discrepancy, and the 0.55-lives-per-second condition.