# Lead

## Overview

Lead is a Bloon property that makes the Bloon resistant to many sharp attacks. The BTDX community reference lists darts, tacks, blades, shurikens, barbed darts, nails, grapes, road spikes, lower-tier Charge projectiles, and boomerangs as examples of attacks that cannot normally pop Lead.

## Implementation notes

**Source-confirmed:** ordinary Bloons initialize `lead = 0`, and BTDX has a dedicated `Lead_Bloon_Branch`. The branch uses the ordinary colour/type mapping and movement multipliers, while selecting the Lead sprite state. A separate `Camo_Lead_Bloon_Branch` exists for the combined Camo + Lead form.

This confirms that Lead is tracked separately from the Bloon's colour/type. The source excerpts inspected for this article do not establish a complete list of damage types that can or cannot damage Lead.

## Reported counterplay

The community reference reports that a 4L Monkey Village can grant Lead-popping capability to towers that otherwise lack it.

The upgrade identifier and exact tower interactions are unverified report and should be checked in the target game build.

## Stacking

The community reference lists Lead as compatible with:
- Camo
- Splitting

Camo Lead is also represented by a dedicated branch in the source.

## Trivia

Lead has its own branch, but it does not get a new colour progression. The Lead branch still chooses the ordinary Red-through-Prismatic sprites from the layer value. The material property rides on top of the Bloon's type.

## Evidence

- **Source-confirmed:** [Normal_Bloon_Branch/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Create_0.gml), [Lead_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Lead_Bloon_Branch/Step_0.gml), [Camo_Lead_Bloon_Branch](https://github.com/alert-bake/BTDX-source/tree/main/objects/Camo_Lead_Bloon_Branch).
- **Needs in-game verification:** exact damage-type exceptions and upgrade behaviour.
