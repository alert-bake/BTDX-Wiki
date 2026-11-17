# Bloons

Bloons are the enemies encountered throughout **Bloons Tower Defense X (BTDX)**. Most travel along a track, while some mission-specific enemies use custom movement or encounter rules. A Bloon that reaches its leak point can cost lives, but leak damage is not universally equal to the Bloon's displayed durability or its RBE.

This reference is BTDX-specific. Similar names, artwork, or mechanics in other Bloons games are not evidence that BTDX behaves the same way.

## How to read this section

The wiki separates three kinds of information:

- **Source-confirmed:** directly supported by the checked BTDX GML source. This establishes what the inspected code does, not necessarily the developer's intended design.
- **Community-reported:** recorded by the BTDX community wiki but not independently confirmed in the target build.
- **Unverified:** a question or interpretation for which the available evidence is incomplete.

Unless an article says otherwise, source-code observations refer to the checked Windows source tree. The main reference builds are Windows 1.5.1 and unofficial Android 1.5.2. Do not silently combine observations from different builds.

## Bloon categories

| Category | What belongs here |
|---|---|
| Standard and nested Bloons | Ordinary colours, intermediate colour layers, and durable lower-tier forms such as Ceramic and Brick |
| Properties and modifiers | Camo, Regrow, Lead, Tattered, Shielded, Super Shielded, Static/Energized, and other traits layered onto a Bloon |
| Special Bloons | Enemies with their own objects, behaviours, mission restrictions, or unusual interactions |
| MOAB-class Bloons | Blimps with separate shell durability and child-spawn logic |
| Bounty Bloons | Multi-stage Bounty encounters and their boss-like enemies |

## Core terminology

### Layers, types, and children

A Bloon can represent multiple layers of smaller Bloons. Popping an outer layer may reveal a child Bloon or several children. The child relationship is specific to the Bloon and the code path that popped it.

BTDX's `bloonlayer` variable is **not a simple count of remaining layers**. The ordinary Bloon branch uses values such as 1, 1.5, 2, 2.5, through 8.5 to select distinct appearances and movement multipliers. Other branches use much larger composite values for Ceramic, Brick, and MOAB-class forms. See [Bloon hierarchy](Bloon-Hierarchy.md) and [Bloon properties](Properties.md).

### RBE

RBE means **Red Bloon Equivalent**. It is a comparison measure for the total popping workload represented by a Bloon or group. It is not interchangeable with HP, the number of hits required by a particular tower, or the number of lives lost on leak.

Where this wiki repeats an RBE value from the community source, it labels that value as reported until it has been independently checked.

### Durability: armour, shield, and shell

BTDX does not use one universal durability variable for every enemy.

- **Armour** is used by Ceramic and Brick branches.
- **Shield** is used by Shielded Bloons and some shielded blimp forms.
- **Shell** is used by MOAB-class and other shell-based enemies.

These systems can coexist on a larger enemy. Do not rewrite all three as generic HP.

### Speed

The ordinary Bloon branch calculates a movement value called `fast` and assigns it to `path_speed`. The calculation uses `global.bspeed`, a type-specific multiplier, and the Tattered state; glue, freeze, stun, and distraction can then alter the result. The multipliers in individual articles are source-code multipliers, not fixed real-world speeds or universal values across every game mode.

## Standard and nested Bloons

The familiar basic sequence documented by the community source is:

**Red → Blue → Green → Yellow → Pink**

The reported child relationship is that each of Blue, Green, Yellow, and Pink reveals the preceding colour when popped. Black is reported to split into two Pink Bloons. White is listed at the same tier as Black, but matching tier or RBE does not establish matching damage interactions or child behaviour.

BTDX's normal branch also recognises intermediate colour layers:

**Orange, Cyan, Lime, Amber, and Purple**, plus **Prismatic** above Rainbow.

These are real sprite/type states in the source's normal Bloon movement code. Their appearance and speed multipliers are documented separately. Their Chipper-specific three-way splitting behaviour must not be mistaken for the ordinary pop result.

Start here:
- [Standard and nested Bloons](Standard/Overview.md)
- [Bloon hierarchy](Bloon-Hierarchy.md)
- [Bloon type and sprite research](../Research/Bloon-Types-and-Sprites.md)

## Properties and modifiers

A Bloon can carry traits that change its appearance, targeting, damage handling, or movement. Examples include Camo, Regrow, Lead, Tattered, Shielded, and Static/Energized. Some combinations have their own branch objects, such as Camo Lead.

See [Bloon properties](Properties.md) for the consolidated reference and individual property articles as they are added.

## Special and mission-specific Bloons

Some Bloons are not just ordinary colour layers with a trait. They have separate source objects and bespoke logic. Examples in the source inventory include Ninja, Robo, Solar, Spectrum, Stuffed, Planetarium, Comet, Barrier, and many mission-specific enemies.

See [Special Bloons](Special/Overview.md). An object identifier in the source inventory does not automatically prove that the object appears in normal rounds or is available in every platform build.

## MOAB-class Bloons

MOAB-class enemies use separate branches and durability handling. The source confirms distinct shell and child-spawn logic; some forms also use shields. Their child composition must be documented per blimp rather than inferred from the ordinary colour ladder.

See [MOAB-class Bloons](MOAB-Class/Overview.md).

## Bounty Bloons

Bounty encounters have their own directory because they are multi-stage encounters rather than ordinary Bloon layers. Stage counts, rewards, and platform availability need to remain tied to the relevant Bounty family and game version.

See [Bounty Bloons](Bounty/Overview.md).

## Sources and version policy

Primary implementation reference: [BTDX-source](https://github.com/alert-bake/BTDX-source). Community-reported reference: [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons).

The source can establish what a particular script does. It cannot, by itself, prove that a branch is used in every mode or that a community-reported RBE is correct. In-game observations should include platform, version, mode, and enough context to reproduce the result.
