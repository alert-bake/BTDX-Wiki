# Bloon hierarchy and nested layers

This page separates three ideas that are easy to accidentally collapse into one:

1. **Ordinary pop relationships** reported by the community reference.
2. **Fractional type values** used by BTDX's ordinary Bloon branch.
3. **Special attack routines** that create multiple copies of a lower type.

A source type value is not automatically a child count or an RBE value.

## Basic colour chain

The BTDX community reference describes this basic sequence:

| Outer Bloon | Reported child |
|---|---|
| Blue | Red |
| Green | Blue |
| Yellow | Green |
| Pink | Yellow |
| Black | Two Pink Bloons |

The Red Bloon is the base unit and has no smaller child. These relationships are community-reported; the source code inspected for the ordinary movement branch establishes type identities and speed selection, but does not by itself establish every ordinary pop result.

White is assigned its own ordinary type value (6.1), separate from Black (6). Its reported RBE and tier do not prove that it shares Black's child result.

## Ordinary branch type map

The normal Bloon Step event selects sprites and speed multipliers for the following values:

| Type | `bloonlayer` |
|---|---:|
| Red | 1 |
| Orange | 1.5 |
| Blue | 2 |
| Cyan | 2.5 |
| Green | 3 |
| Lime | 3.5 |
| Yellow | 4 |
| Amber | 4.5 |
| Pink | 5 |
| Purple | 5.5 |
| Black | 6 |
| White | 6.1 |
| Zebra | 7 |
| Rainbow | 8 |
| Prismatic | 8.5 |

These are **type/layer identifiers**, not a plain count of how many hits remain. The normal branch uses them to choose sprites and movement multipliers. See [Standard and nested Bloons](Standard/Overview.md) for the complete multiplier table and individual articles.

## Chipper's fractional-layer split

The Chipper branch has a special handler for half-step values. In its base case (`pophit = 0`), it subtracts 0.5 from the fractional `bloonlayer` and produces three instances at the resulting lower layer: the original instance plus two newly created instances.

| Fractional type | Starting value | Resulting type | Chipper base-case result |
|---|---:|---|---|
| Orange | 1.5 | Red (1) | 3 Reds |
| Cyan | 2.5 | Blue (2) | 3 Blues |
| Lime | 3.5 | Green (3) | 3 Greens |
| Amber | 4.5 | Yellow (4) | 3 Yellows |
| Purple | 5.5 | Pink (5) | 3 Pinks |
| Prismatic | 8.5 | Rainbow (8) | 3 Rainbows |

This table describes the Chipper's fractional-layer handling, not the ordinary pop result for these types. The code also subtracts `pophit`, so attacks with a non-zero value can produce a different resulting layer.

Source: [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).

## Other special splitting routines

The Challenge Drones alarm routine contains explicit layer-specific cases:
- A Zebra-layer case (`bloonlayer = 7`) uses `repeat(3)` to create three Bloon-branch instances.
- A Rainbow-layer case (`bloonlayer = 8`) uses `repeat(7)` to create seven Bloon-branch instances.

These are Challenge Drones attack behaviours. They are not proof that every Zebra or Rainbow pop has those child counts.

Source: [Challenge_Drones/Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Challenge_Drones/Alarm_0.gml).

## Durable forms are separate branches

Ceramic and Brick are not simply later entries in the ordinary colour ladder.

- Ceramic uses `Ceramic_Bloon_Branch` and armour based on `10 * global.bpower`.
- Brick uses `Brick_Bloon_Branch` and armour based on `30 * global.bpower`.
- Shielded handling uses large type values (18 for Ceramic and 48 for Brick) and a separate shield durability pool before creating the corresponding branch.

See [Ceramic Bloon](Standard/Ceramic-Bloon.md), [Brick Bloon](Standard/Brick-Bloon.md), and [Bloon properties](Properties.md).

## MOAB-class children

BTDX's documented blimps have their own child relationships. Examples reported by the community reference include:

| Parent | Children when popped |
|---|---|
| Mini M.O.A.B. | 4 Ceramics |
| M.O.A.B. | 4 Bricks |
| B.F.B. | 3 M.O.A.B.s |
| Z.O.M.G. | 3 B.F.B.s |
| D.D.T. | 6 Tattered Camo Lead Bricks |
| B.R.C. | 8 Mini M.O.A.B.s |
| D.D.D.T. | 6 D.D.T.s |

These are source-reported relationships; verify them against the intended game build before using them for exact calculations. MOAB-class source branches have their own shell and child-spawn logic, so do not extrapolate from the ordinary Bloon hierarchy.

## Special spawning and splitting

Some Bloons spawn enemies without being popped, release children off-track, or create hazards that block projectiles. These behaviours should be documented on their individual pages rather than forced into the simple nested-layer model.

## RBE warning

RBE is a comparison measure, not a universal leak-damage formula. Mission-specific and special Bloons can drain lives in custom ways. See [Properties](Properties.md) and the individual enemy pages.
