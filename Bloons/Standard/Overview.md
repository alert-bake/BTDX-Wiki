# Standard and nested Bloons

This directory documents the ordinary Bloon colour/layer system and the durable or intermediate forms connected to it. It distinguishes the **normal Bloon branch's type values** from **reported pop relationships** and from **special attack behaviour**.

## The ordinary colour ladder

The following values are read from `objects/Normal_Bloon_Branch/Step_0.gml`. They are values of `bloonlayer`, not a conventional integer layer count.

| Bloon | `bloonlayer` | Normal-branch speed multiplier | Sprite selected by source |
|---|---:|---:|---|
| Red | 1 | 1.6× | `Red_Bloon_Spr` |
| Orange | 1.5 | 2.2× | `Orange_Bloon_Spr` |
| Blue | 2 | 2.0× | `Blue_Bloon_Spr` |
| Cyan | 2.5 | 2.6× | `Cyan_Bloon_Spr` |
| Green | 3 | 2.4× | `Green_Bloon_Spr` |
| Lime | 3.5 | 3.0× | `Lime_Bloon_Spr` |
| Yellow | 4 | 4.4× | `Yellow_Bloon_Spr` |
| Amber | 4.5 | 5.0× | `Amber_Bloon_Spr` |
| Pink | 5 | 4.8× | `Pink_Bloon_Spr` |
| Purple | 5.5 | 5.4× | `Purple_Bloon_Spr` |
| Black | 6 | 2.4× | `Black_Bloon_Spr` |
| White | 6.1 | 2.8× | `White_Bloon_Spr` |
| Zebra | 7 | 2.8× | `Zebra_Bloon_Spr` |
| Rainbow | 8 | 3.8× | `Rainbow_Bloon_Spr` |
| Prismatic | 8.5 | 4.4× | `Prismatic_Bloon_Spr` |

The movement formula is `global.bspeed × multiplier × (tattered + 1)` before the later status-effect adjustments in the same Step event. Therefore the table is not a fixed speed in pixels per frame, and it is not a universal formula for Brick, Ceramic, MOABs, or every special branch.

Source: [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml).

## Basic child relationships

The following are **unverified report** pop relationships, not all independently verified by the source files inspected for this pass.

| Bloon | Reported pop result | Reported RBE |
|---|---|---:|
| Red | No smaller child | 1 |
| Blue | Red | 2 |
| Green | Blue | 3 |
| Yellow | Green | 4 |
| Pink | Yellow | 5 |
| Black | Two Pink Bloons | 11 |
| White | Child result not established here | 11 |

Do not infer a child's behaviour from the layer number alone. In particular, Black and White are separate type values (6 and 6.1), even though an unverified report groups them at the same tier.

## Intermediate colour layers

Orange, Cyan, Lime, Amber, and Purple are present in the ordinary branch's sprite-selection and speed logic. They use fractional `bloonlayer` values between the main colour values.

The Chipper branch has a specific interaction with these fractional values: when it handles a half-step layer with the ordinary `pophit = 0` case, it reduces the layer by 0.5 and produces three instances at the lower layer (the original plus two newly created instances). The source-backed examples are Orange → three Reds, Cyan → three Blues, Lime → three Greens, Amber → three Yellows, and Purple → three Pinks. This is **Chipper behaviour**, not a claim that every ordinary pop produces three children.

Prismatic is also a fractional layer (8.5); the Chipper's corresponding mapping produces three Rainbow-layer Bloons in the documented base case.

Source: [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml).

## Higher durability forms

- [Ceramic Bloon](Ceramic-Bloon.md) — separate Ceramic branch; armour-based durability.
- [Brick Bloon](Brick-Bloon.md) — separate Brick branch; heavier armour and its own movement formula.

Their large `bloonlayer` values are not simply the next entries after Prismatic in the ordinary colour ladder.

## Individual articles

### Basic colours
- [Red Bloon](Red-Bloon.md)
- [Blue Bloon](Blue-Bloon.md)
- [Green Bloon](Green-Bloon.md)
- [Yellow Bloon](Yellow-Bloon.md)
- [Pink Bloon](Pink-Bloon.md)
- [Black Bloon](Black-Bloon.md)
- [White Bloon](White-Bloon.md)

### Intermediate colours
- [Orange Bloon](Orange-Bloon.md)
- [Cyan Bloon](Cyan-Bloon.md)
- [Lime Bloon](Lime-Bloon.md)
- [Amber Bloon](Amber-Bloon.md)
- [Purple Bloon](Purple-Bloon.md)
- [Zebra Bloon](Zebra-Bloon.md)
- [Rainbow Bloon](Rainbow-Bloon.md)
- [Prismatic Bloon](Prismatic-Bloon.md)

### Durable forms
- [Ceramic Bloon](Ceramic-Bloon.md)
- [Brick Bloon](Brick-Bloon.md)

## Terminology note

"Standard" in this directory means the ordinary layer/type family and its directly related durable forms. It does not mean every listed form is necessarily sent in normal rounds, nor that every type is a separate player-facing round-set entry.
