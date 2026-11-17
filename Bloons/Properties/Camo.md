# Camo

## Overview

Camo is a Bloon property that changes whether towers can detect and target the Bloon. In the community reference, a Camo Bloon cannot be targeted or damaged by a tower without Camo detection.

## Implementation notes

**Source-confirmed:** the ordinary Bloon Create event initializes `camo = 0`. BTDX also has a dedicated `Camo_Bloon_Branch`, and a separate `Camo_Lead_Bloon_Branch` for the combined form. The Camo branch uses the ordinary layer-to-sprite mapping and movement multipliers, while selecting the Camo sprite frame when the Bloon is not Tattered.

This confirms that Camo is tracked independently from the colour/type value. It does not, by itself, establish the full targeting rule or every tower's detection behaviour.

## Reported counterplay

The BTDX community reference lists three ways to handle Camo:
- Use a tower or upgrade with Camo detection.
- Use a 3L Monkey Village.
- Remove the Camo property with 3M Monkey Submarines or 3R Monkey Engineers.

These upgrade identifiers and effects are community-reported and should be checked against the intended build.

## Stacking

The community reference lists Camo as compatible with:
- Lead
- Splitting

It does not list every theoretically possible combination as valid. Do not assume arbitrary property stacking.

## Trivia

Camo is not a different colour ladder. The source gives it a dedicated branch, but that branch still selects Red, Blue, Green, Yellow, Pink, Black, White, Zebra, Rainbow, and the intermediate sprites from the Bloon's layer value. The disguise changes; the underlying type still matters.

## Evidence

- **Source-confirmed:** [Normal_Bloon_Branch/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Create_0.gml), [Camo_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Camo_Bloon_Branch/Step_0.gml).
- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons), for targeting and counterplay.
- **Needs in-game verification:** exact detection rules, tower exceptions, upgrade identifiers, and platform differences.
