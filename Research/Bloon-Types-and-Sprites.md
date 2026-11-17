# Bloon type and sprite research (draft)

> **Status:** Research draft. This page combines source-code findings, sprite inspection, and previously collected unverified reports. It is not a final gameplay reference. Claims are labelled by evidence type; unverified interpretations stay unconfirmed.

## Scope

This document is the research hub for BTDX Bloon types, their visible sprite variants, the ordinary colour/layer hierarchy, and special Bloon behaviours. It links to the detailed wiki articles rather than duplicating every individual enemy's stats.

## Evidence labels

- **Source-confirmed:** directly visible in the checked BTDX source code.
- **Sprite-observed:** identified by inspecting the ordered frames in the source sprite metadata and the PNGs.
- **Unconfirmed:** plausible interpretation that still needs a matching code path or in-game test.

Source repository: [alert-bake/BTDX-source](https://github.com/alert-bake/BTDX-source)  
Wiki repository: [alert-bake/BTDX-Wiki](https://github.com/alert-bake/BTDX-Wiki)

---

## 1. The eleven recurring low-tier Bloon sprite states

**Sprite-observed:** the Red, Blue, and Green Bloon sprites have been inspected frame-by-frame. Red has **12 frames**; Blue and Green have **11 frames**. The first eleven positions correspond to the same recurring visual lineup. The extra Red frame is the exception.

The current identification of the eleven recurring states is:

| Frame (1-based) | Identified state | Notes |
|---:|---|---|
| 1 | Normal | Ordinary appearance |
| 2 | Tattered | Tattered appearance |
| 3 | Shielded | Shield visual |
| 4 | Regrow | Regrow visual |
| 5 | Camo | Camo visual |
| 6 | Lead | Lead visual |
| 7 | Static / Energized | Electrical appearance; the code branch is named `Static_Bloon_Branch` |
| 8 | Camo Lead | Combined Camo + Lead appearance |
| 9 | Regrow Tattered | Combined Regrow + Tattered appearance |
| 10 | Solar / Sun-Blessed | Solar Bloon appearance; confirmed by the Solar branch selecting sprite frame index 9 |
| 11 | Glued | Glue visual |

**Important distinction:** these are sprite-frame identities, not eleven entries in the ordinary Sandbox type selector. The Sandbox sender's basic type IDs only enumerate nine variants (0–8; see section 3). Solar and Glued have separate implementation paths and should not be forced into that nine-entry list.

### Sprite coverage

| Bloon sprite | Frames in metadata | Current identification |
|---|---:|---|
| Red | 12 | Frames 1–11 identified; frame 12 is the unusual extra |
| Blue | 11 | Same recurring lineup; no extra Red-like frame |
| Green | 11 | Same recurring lineup; no extra Red-like frame |
| Yellow | 11 | Frame count confirmed; full frame-by-frame labels still need visual/code verification |
| Pink | 11 | Frame count confirmed; full frame-by-frame labels still need visual/code verification |
| Black | 11 | Frame count confirmed; full frame-by-frame labels still need visual/code verification |
| White | 11 | Frame count confirmed; full frame-by-frame labels still need visual/code verification |
| Zebra | 11 | Frame count confirmed; full frame-by-frame labels still need visual/code verification |
| Rainbow | 11 | Frame count confirmed; full frame-by-frame labels still need visual/code verification |
| Ceramic | 15 | Different frame count; do not assume the low-tier 11-frame lineup applies |

Frame counts above are taken from the sprite metadata / existing sprite inventory. Only Red, Blue, and Green have had the full frame sequence manually inspected and labelled so far. Yellow through Rainbow still need the same full frame-by-frame pass.

See the [frame-by-frame embed test](https://github.com/alert-bake/BTDX-source/blob/main/Sillyembedtest.md) for the current PNG evidence. The PNGs remain in BTDX-source; the wiki can embed them directly with raw GitHub URLs.

### The extra Red frame: possible Ditto

**Sprite-observed:** Red has a twelfth frame after the eleven recurring states. It visually resembles the Normal Red Bloon.

**Unconfirmed interpretation:** it may be a Ditto Bloon. There is not yet a confirmed `Ditto_Bloon` code object or a verified spawn path establishing that name. A search for that exact identifier did not find a match, which does not rule out a differently named implementation.

Do not label this frame definitively as Ditto until one of the following is found:
- a source-code branch or sprite-selection path that selects Red frame 12;
- a spawn definition that creates the suspected Ditto form;
- an in-game observation with enough context to distinguish it from an ordinary Red Bloon.

Blue and Green do not have this extra frame. Their inspected sprites stop at frame 11.

---

## 2. Ordinary colour / layer hierarchy

**Source-confirmed:** the Solar Bloon movement script maps the `bloonlayer` value to the ordinary Bloon colour sprite. The code uses these thresholds:

| Colour / form | Layer condition in Solar branch | Speed multiplier |
|---|---:|---:|
| Red | `bloonlayer < 2` | `global.bspeed × 1.2` |
| Blue | `bloonlayer < 4` | `global.bspeed × 1.5` |
| Green | `bloonlayer < 6` | `global.bspeed × 1.8` |
| Yellow | `bloonlayer < 8` | `global.bspeed × 3.3` |
| Pink | `bloonlayer < 10` | `global.bspeed × 3.6` |
| Black | `bloonlayer = 11` | `global.bspeed × 1.8` |
| White | `bloonlayer = 11.1` | `global.bspeed × 2.1` |
| Zebra | `bloonlayer = 12` | `global.bspeed × 2.1` |
| Rainbow | `bloonlayer = 13` | `global.bspeed × 2.7` |

These are multipliers of the global base speed, not absolute movement speeds. The script does not assign a colour/speed in the visible section for every possible numeric layer value; do not interpolate missing values.

The same script applies the Tattered multiplier:
`fast = fast × (tattered + 1)`
Therefore, when `tattered = 1`, the Solar Bloon's listed speed multiplier is doubled.

The script also sets speed to zero when `stun = 1`, and uses a negative speed when `distraction > 0`. Those are movement effects, not additional sprite identities.

Source: [Solar_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Bloon_Branch/Step_0.gml)

### Nested children

**Unverified report:** the ordinary sequence is Red → Blue → Green → Yellow → Pink. Black is described as splitting into two Pink Bloons. See [Bloon hierarchy](../Bloons/Bloon-Hierarchy.md) for the currently documented child relationships and MOAB-class examples.

---

## 3. The nine basic Sandbox type IDs

**Source-confirmed:** `objects/sandbox_sender/Alarm_1.gml` maps the Sandbox sender's `stack1type` values as follows for ordinary low-tier layers:

| Type ID | Created branch / state | Meaning |
|---:|---|---|
| 0 | `Normal_Bloon_Branch` | Normal |
| 1 | `Normal_Bloon_Branch` + `tattered = 1` | Tattered |
| 2 | `Shielded_Bloon_Branch` | Shielded |
| 3 | `Regrow_Bloon_Branch` | Regrow |
| 4 | `Camo_Bloon_Branch` | Camo |
| 5 | `Lead_Bloon_Branch` | Lead |
| 6 | `Static_Bloon_Branch` | Static / Energized |
| 7 | `Camo_Lead_Bloon_Branch` | Camo Lead |
| 8 | `Regrow_Bloon_Branch` + `tattered = 1` | Regrow Tattered |

This list has **nine IDs**, not eleven. The eleven recurring sprite states include Solar and Glued, which are not separate entries in this basic sender mapping. This is why sprite-frame count and Sandbox type count must be documented separately.

The sender has additional handling for special layer values, including Ceramic, Brick, Mini MOAB, MOAB, BFB, ZOMG, DDT, LPZ, BRC, HTA, and other large/special forms. These are not extra values in the nine-entry low-tier modifier list.

Source: [sandbox_sender/Alarm_1.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/sandbox_sender/Alarm_1.gml)

---

## 4. Solar / Sun-Blessed Bloon

**Source-confirmed:** the mysterious tenth frame is the Solar Bloon appearance.

In `Solar_Bloon_Branch/Step_0.gml`:
- the branch selects the matching colour sprite according to `bloonlayer`;
- if `tattered = 1`, it sets `image_index = 1`;
- otherwise it sets `image_index = 9`.

Because sprite image indices are zero-based, `image_index = 9` selects the **10th frame**. This directly identifies the previously unknown Red/Blue/Green frame 10 as the Solar appearance, not Ditto.

The branch's alarm code also gives Solar Bloons an attack:
- it sets `range = 120`;
- it resets `alarm[0]` to 150;
- it searches for a Monkey within the collision-circle range;
- if it has a target, it creates a `Sun_Stun_Shot` and moves it toward that target;
- projectile potency is set to `round(10 + 3 × bloonlayer)`.

The exact stun duration/effect is not established by this file alone; the `Sun_Stun_Shot` implementation must be checked before documenting that detail.

Solar Storm spawning code creates `Solar_Bloon_Branch` for Solar Bloon entries, `Solar_Ceramic` for Solar Ceramic entries, and `Solar_Blimp` for Solar blimps.

Sources:
- [Solar_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Bloon_Branch/Step_0.gml)
- [Solar_Bloon_Branch/Alarm_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Bloon_Branch/Alarm_0.gml)
- [Solar_Storm_Go/Alarm_10.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Storm_Go/Alarm_10.gml)

The existing [Properties page](../Bloons/Properties.md) calls this form **Sun-Blessed**. The source object name is **Solar_Bloon_Branch**. Treat Solar and Sun-Blessed as the same documented form unless further evidence shows a distinction.

---

## 5. Other documented Bloon properties and special forms

The following are already covered in the wiki's [Bloon properties reference](../Bloons/Properties.md). This is a compact index, not a replacement for those detailed notes.

### Ordinary modifiers / properties
- **Camo:** cannot be targeted by towers without detection.
- **Regrow:** restores layers over time, up to its original layer.
- **Lead:** resists many sharp attacks.
- **Tattered:** moves faster; the source-reported multiplier is 2× and the effect is lost after a layer is popped.
- **Splitting:** releases multiple counterpart Bloons when popped.
- **Shielded:** has a shield layer that absorbs damage before the Bloon body.
- **Super Shield:** Nightmare Mode shield variant reported to absorb twice the damage of a regular shield.
- **Static / Energized:** shielded electrical form that periodically fires a projectile at towers.
- **Sun-Blessed / Solar:** Solar Storm form with a stunning projectile and its own movement handling.
- **Color Splash:** mission-specific Bloons that release multiple counterpart Bloons.

### Distinct special forms
- **Ninja Bloons:** Camo forms that fire homing projectiles and become Splitting Camo Bloons when popped.
- **Robo Bloons:** Lead forms that fire piercing lasers and become Splitting Lead Bloons when popped.
- **Rag Bloons:** Necropolis mission forms that can resurrect as Reincarnated Bloons.
- **Reincarnated Bloons:** resurrected forms that do not resurrect again.
- **Undying Rag Bloon:** Regrow-like Rag variant reported by the unverified report.

### Larger and mission-specific enemies
The wiki also documents Ceramic and Brick Bloons, MOAB-class enemies, special mission enemies, and Bounty Bloons. Their individual pages contain the current stats and should remain the canonical detail pages:

- [Bloon overview](../Bloons/Overview.md)
- [Properties and modifiers](../Bloons/Properties.md)
- [Bloon hierarchy](../Bloons/Bloon-Hierarchy.md)
- [Standard Bloons](../Bloons/Standard/Overview.md)
- [Special Bloons](../Bloons/Special/Overview.md)
- [MOAB-class Bloons](../Bloons/MOAB-Class/Overview.md)
- [Bounty Bloons](../Bloons/Bounty/Overview.md)

---

## 6. Base Bloon defaults

**Source-confirmed:** `Normal_Bloon_Branch/Create_0.gml` initializes several shared fields:

| Field | Initial value |
|---|---:|
| `glue` | 0 |
| `freeze` | 0 |
| `shielded` | 0 |
| `bigbloon` | 0 |
| `electric` | 0 |
| `normal` | 1 |
| `camo` | 0 |
| `lead` | 0 |
| `regrow` | 0 |
| `tattered` | 0 |
| `stun` | 0 |
| `distraction` | 0 |
| `corrosion` | 0 |
| `radiation` | 0 |
| `bloonlayer` | 0 |
| `bloonmaxlayer` | 0 |

It also sets the initial sprite to `Red_Bloon_Spr` and initializes `fast = 1.5` before other branch/step logic adjusts movement. These are object initialization defaults, not necessarily the final in-game stats of every spawned Bloon.

Source: [Normal_Bloon_Branch/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Create_0.gml)

---

## 7. Findings that must not be conflated

1. **Eleven recurring sprite states ≠ eleven Sandbox type IDs.** The sender mapping has nine basic IDs.
2. **Frame 10 ≠ Ditto.** It is Solar/Sun-Blessed, confirmed by the Solar branch's zero-based `image_index = 9`.
3. **Red frame 12 may be Ditto, but this is not confirmed.** It only currently has a visual resemblance to Normal.
4. **Static and Energized** refer to the electrical appearance/behaviour; the source branch name is Static.
5. **Solar and Sun-Blessed** are the names found in source and wiki documentation respectively; currently treated as one form.
6. **A sprite frame does not prove a gameplay property by itself.** Confirm actual behaviour from object code or controlled in-game tests.
7. **Unverified reported stats are not source-code facts.** Keep their evidence label visible and record the game version when testing.

---

## 8. Follow-up research checklist

- [ ] Inspect all eleven frames for Yellow, Pink, Black, White, Zebra, and Rainbow sprites.
- [ ] Identify the purpose of Red frame 12 by finding its sprite-selection path or a controlled in-game example.
- [ ] Search for alternate Ditto identifiers, not only the exact string `Ditto`.
- [ ] Inspect the Glued Bloon implementation and determine whether it is a modifier, branch, or visual-only state.
- [ ] Inspect `Sun_Stun_Shot` to document the exact stun effect and duration.
- [ ] Compare the Solar branch's speed values with the ordinary branches to determine which values are shared and which are Solar-specific.
- [ ] Verify the Unverified report modifier stacking combinations in-game.
- [ ] Record platform and version for every hands-on observation.

## Source index

### BTDX source code
- [Sandbox sender type mapping](https://github.com/alert-bake/BTDX-source/blob/main/objects/sandbox_sender/Alarm_1.gml)
- [Normal Bloon defaults](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Create_0.gml)
- [Solar Bloon movement and sprite selection](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Bloon_Branch/Step_0.gml)
- [Solar Bloon attack alarm](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Bloon_Branch/Alarm_0.gml)
- [Solar Storm spawn mapping](https://github.com/alert-bake/BTDX-source/blob/main/objects/Solar_Storm_Go/Alarm_10.gml)
- [Sprite frame inspection document](https://github.com/alert-bake/BTDX-source/blob/main/Sillyembedtest.md)


---
*Draft prepared from the source and sprite findings available on 2026-11-14. Update this page when new code paths or in-game evidence are verified.*

---

## 6. Ordinary-branch type and movement map

This section records the **Normal_Bloon_Branch** mapping separately from the Solar branch mapping in section 2. They are different code paths and their values must not be merged into one table.

**Source-confirmed:** `objects/Normal_Bloon_Branch/Step_0.gml` selects the following sprites and calculates the corresponding base movement multipliers:

| Bloon type | `bloonlayer` | Base speed multiplier |
|---|---:|---:|
| Red | 1 | 1.6× |
| Orange | 1.5 | 2.2× |
| Blue | 2 | 2.0× |
| Cyan | 2.5 | 2.6× |
| Green | 3 | 2.4× |
| Lime | 3.5 | 3.0× |
| Yellow | 4 | 4.4× |
| Amber | 4.5 | 5.0× |
| Pink | 5 | 4.8× |
| Purple | 5.5 | 5.4× |
| Black | 6 | 2.4× |
| White | 6.1 | 2.8× |
| Zebra | 7 | 2.8× |
| Rainbow | 8 | 3.8× |
| Prismatic | 8.5 | 4.4× |

The formula is:

```
fast = global.bspeed * type_multiplier * (tattered + 1)
path_speed = fast
```

Glue, freeze, stun, and distraction are then applied in the same Step event. The multiplier is relative to `global.bspeed`; it is not a fixed absolute speed. The table is specific to the normal branch and should not be copied to Ceramic, Brick, Shielded, MOAB, or special Bloon branches.

### Fractional-layer handling in Chipper

The source in `objects/Chipper_Bloon_Branch/Step_0.gml` calculates the fractional part of `bloonlayer`. For a half-step value, it reduces the layer by `0.5 + pophit` and creates two additional Chipper branch instances while retaining the original. With `pophit = 0`, this produces three instances at the lower layer:

| Input type | Input value | Lower type | Resulting instances |
|---|---:|---|---:|
| Orange | 1.5 | Red (1) | 3 |
| Cyan | 2.5 | Blue (2) | 3 |
| Lime | 3.5 | Green (3) | 3 |
| Amber | 4.5 | Yellow (4) | 3 |
| Purple | 5.5 | Pink (5) | 3 |
| Prismatic | 8.5 | Rainbow (8) | 3 |

This is a Chipper-specific attack interaction. It is not the universal pop behaviour for these types. A non-zero `pophit` changes the amount subtracted and must be traced separately.

### Ceramic and Brick are not fractional colour types

The Ceramic and Brick branches use separate armour systems:
- Ceramic: `maxarmour = ceil(10 * global.bpower)`.
- Brick: `maxarmour = ceil(30 * global.bpower)`.

The Shielded branch assigns layer 18 to Ceramic-tier forms and layer 48 to Brick-tier forms, with separate shield values before transforming into the corresponding armour branch. Do not treat those values as entries in the ordinary colour ladder.

Sources:
- [Normal_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Step_0.gml)
- [Chipper_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Chipper_Bloon_Branch/Step_0.gml)
- [Ceramic_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Ceramic_Bloon_Branch/Step_0.gml)
- [Brick_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Brick_Bloon_Branch/Step_0.gml)
- [Shielded_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Shielded_Bloon_Branch/Step_0.gml)
