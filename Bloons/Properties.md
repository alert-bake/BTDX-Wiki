# Bloon forms and properties

BTDX has several kinds of Bloon variation. This page separates **properties/modifiers** that can be applied to an existing Bloon from **special forms** that have their own attacks or behaviour.

The descriptions below are transcribed and reorganized from the [BTDX community Bloons page](https://bloons-tdx.fandom.com/wiki/Bloons). That page may be incomplete or version-dependent. Treat its details as source-reported until tested in the target build.

## Individual property articles

The pages below provide dedicated entries for each property or special modifier. This file remains the consolidated quick-reference table; the individual pages carry the longer explanations, source notes, and verification gaps.

### Core properties
- [Camo](Properties/Camo.md)
- [Regrow](Properties/Regrow.md)
- [Lead](Properties/Lead.md)
- [Tattered](Properties/Tattered.md)
- [Splitting](Properties/Splitting.md)

### Shield and special modifiers
- [Shielded](Properties/Shielded.md)
- [Super Shield](Properties/Super-Shield.md)
- [Static / Energized](Properties/Static-Energized.md)
- [Sun-Blessed / Solar](Properties/Sun-Blessed-Solar.md)
- [Color Splash](Properties/Color-Splash.md)

---

## Properties and modifiers

Modifiers are special layers or effects that can be applied to many Bloons. Some can be combined; the source explicitly lists combinations for each modifier below. A modifier generally does not add to the number of lives lost, with **Splitting** being the stated exception.

### Camo

Camo Bloons cannot be targeted or damaged by towers without Camo detection.

The community page lists three ways to handle Camo:
- Use a tower or upgrade with Camo detection.
- Use a 3L Monkey Village.
- Remove the Camo modifier with 3M Monkey Submarines or 3R Monkey Engineers.

**Stacking:** Lead and Splitting.

### Regrow

Regrow Bloons restore one layer every two seconds, up to their original layer.

When a Regrow Bloon splits into multiple children, each child can regenerate toward the original layer. This can multiply the number of Bloons and greatly increase the total popping workload.

Regrow Bloons cannot regenerate while frozen.

**Stacking:** Tattered and Splitting.

### Lead

Lead Bloons resist most sharp attacks. The source gives darts, tacks, blades, shurikens, barbed darts, nails, grapes, road spikes, lower-tier Charge projectiles, and boomerangs as examples.

A 4L Monkey Village can grant Lead-popping capability to towers that otherwise lack it.

**Stacking:** Camo and Splitting.

### Tattered

Tattered Bloons move at twice their normal speed. The property is lost after one layer is popped. Tattered Purple Bloons are described as the fastest Bloons in the game.

**Stacking:** Regrow and/or Splitting.

### Splitting

Splitting Bloons pop into three Bloons of their counterpart type and move faster than their ordinary counterpart.

| Form | Speed relative to Red | Children | Reported RBE |
|---|---:|---|---:|
| Orange | 137.5% | 3 Red | 4 |
| Cyan | 162.5% | 3 Blue | 7 |
| Lime | 187.5% | 3 Green | 10 |
| Amber | 312.5% | 3 Yellow | 13 |
| Purple | 337.5% | 3 Pink | 16 |
| Prismatic | 275% | 3 Rainbow | 142 |

**Stacking:** Camo, Lead, Regrow, Tattered, Shielded, and Static. The source notes that not all combinations can occur simultaneously.

### Shielded

Shields absorb damage before the underlying Bloon can be damaged and protect the Bloon from status effects until the shield is removed.

The community source reports that Shielded Bloons:
- Resist low-damage explosions.
- Cannot be frozen or glued while shielded.
- Are not bypassed by M.I.B. immunities.
- Take an additional 0.25 damage from all sources against the shield.

Shielded Splitting Bloons have twice the shield value of the Bloon they split into.

The source provides the following shield strengths:

| Bloon | Base RBE | Shield strength |
|---|---:|---:|
| Red | 1 | 1 |
| Blue | 2 | 2 |
| Green | 3 | 3 |
| Yellow | 4 | 4 |
| Pink | 5 | 5 |
| Black / White | 11 | 8 |
| Zebra | 23 | 11 |
| Rainbow | 47 | 15 |
| Ceramic | 104 | 25 |
| Brick | 238 | 55 |
| Mini M.O.A.B. | 491 | 100 |
| M.O.A.B. | 1,252 | 355 |
| B.F.B. | 5,908 | 1,255 |
| L.P.Z. | 2,090 | 500 |
| Z.O.M.G. | 27,632 | 5,255 |
| B.R.C. | 4,428 | 600 |
| H.T.A. | 308 | 68 |
| D.D.T. | 927 | 358 |

Some entries are explicitly marked by the source as never occurring in normal gameplay. These values should not be used as verified gameplay data without testing.

**Stacking:** Splitting or Static.

### Super Shield

Super Shields appear in Nightmare Mode and absorb twice as much damage as a regular shield.

**Stacking:** None reported.

### Static (also described as Energized)

Static Bloons are Shielded Bloons that periodically fire a projectile at towers. A tower hit by the projectile is stunned/disabled. The source says Static shields absorb twice as much damage as regular shields and that Static Bloons move more slowly than their unmodified forms.

The visual appearance is electrical and glowing. **Energized** is a descriptive name used in this wiki for this electrical form; **Static** is the name used by the community reference.

**Stacking:** None reported.

### Sun-Blessed

Sun-Blessed Bloons appear in the Solar Storm mission. They fire a stunning projectile like Static Bloons, move more slowly than their original form, and do not have shields. The source says this effect can apply to all layers.

**Stacking:** None reported.

### Color Splash

Color Splash Bloons appear in the Color Splash mission. They pop into ten Bloons of their counterpart type and move faster than ordinary Splitting Bloons.

| Form | Reported RBE | Leak damage reported by source |
|---|---:|---:|
| Red | 1 | 10 lives |
| Blue | 2 | 20 lives |
| Green | 3 | 30 lives |
| Yellow | 4 | 40 lives |
| Pink | 5 | 50 lives |

**Stacking:** None reported.

The source also mentions Red Bomb Bloons in connection with a Trojan Blimp; that is a separate spawned enemy, not a Color Splash form.

## Special forms

These are not ordinary modifiers. They are distinct Bloon forms with their own attacks, spawning behaviour, or mission restrictions.

### Ninja Bloons

Ninja Bloons have the Camo property and periodically fire homing ninja stars at towers. The stars can hit moving towers and stun them. When popped, a Ninja Bloon becomes a Splitting Camo Bloon of the same colour.

Higher-tier Ninja Bloons are faster and have greater projectile range and stun duration.

| Form | Reported hits / HP | Reported RBE |
|---|---:|---:|
| Red | 9 | 12 |
| Blue | 18 | 25 |
| Green | 27 | 37 |
| Yellow | 36 | 49 |
| Pink | 45 | 61 |
| Rainbow | 90 | 232 |

**Stacking:** None reported.

### Robo Bloons

Robo Bloons have the Lead property and fire piercing lasers that stun towers. When popped, they become a Splitting Lead Bloon of the same colour.

Higher-tier Robo Bloons are faster and have greater laser range and stun duration.

| Form | Reported HP | Reported RBE |
|---|---:|---:|
| Red | 12 | 16 |
| Blue | 24 | 31 |
| Green | 36 | 46 |
| Yellow | 48 | 61 |
| Pink | 60 | 76 |
| Rainbow | 120 | 262 |

**Stacking:** None reported.

### Rag and Reincarnated Bloons

Rag Bloons appear in the Necropolis mission. They retain their original Bloon layers despite their altered appearance. When popped, they resurrect as Reincarnated Bloons.

Reincarnated Bloons resemble Rag Bloons but cannot resurrect again. They retain the initial layer of the Rag Bloon.

The source also describes an **Undying Rag Bloon**, which behaves like a Rag Bloon with Regrow properties.

**Stacking:** Regen is reported for the Undying Rag Bloon.

## Ordinary Bloon resistances are not universal modifiers

Black and White are ordinary colour types, not the same thing as the BTDX modifier system:
- The community source explicitly says BTDX Black Bloons are **not immune to explosives**.
- It explicitly says BTDX White Bloons are **not immune to freezing**.

This differs from mechanics in other Bloons games. If hands-on testing in a particular BTDX build contradicts the community page, record the platform, version, attack used, and result rather than silently merging the claims.

## Related pages

- [Bloons overview](Overview.md)
- [Bloon hierarchy and nested layers](Bloon-Hierarchy.md)
- [Standard and nested Bloons](Standard/Overview.md)
- [Special Bloons](Special/Overview.md)
- [MOAB-class Bloons](MOAB-Class/Overview.md)

## Source

- [BTDX Fandom: Bloons](https://bloons-tdx.fandom.com/wiki/Bloons) — community-maintained reference for the forms, properties, stacking notes, and values summarized here.

