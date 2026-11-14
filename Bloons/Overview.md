# Bloons

Bloons are the enemies in Bloons Tower Defense X (BTDX). They travel along a track or follow a mission-specific movement pattern. If a Bloon reaches its leak point, it removes lives; the amount depends on the Bloon's leak behaviour and is not always identical to its displayed hit points.

This section documents BTDX specifically. Similar names and mechanics in other Bloons games are not proof that BTDX behaves the same way.

## Bloon categories

- **Regular Bloons:** the basic colour progression and its nested children.
- **Modified Bloons:** Bloons with properties such as Camo, Regrow, Lead, shielding, splitting, or other effects.
- **Mission-specific Bloons:** enemies that appear only in particular missions and may have unusual movement or interactions.
- **MOAB-class Bloons:** large blimps with their own health, speed, and child-spawn behaviour.
- **Bounty Bloons:** multi-stage boss encounters tied to Bounty mode. These receive their own detailed directory.

## Core terminology

### Layers and children

A Bloon can contain one or more layers. Popping its outer layer may reveal one or more smaller Bloons rather than removing all of its remaining threat. The exact child relationship is specific to each Bloon.

### RBE

RBE means Red Bloon Equivalent. It is a measure of the total number of basic Red-Bloon-equivalent hits represented by a Bloon or group. It is useful for comparing total popping workload, but it should not be confused with the number of lives lost when a Bloon leaks: BTDX has special enemies whose leak effects do not follow a simple one-RBE-one-life rule.

### HP and hit counts

Community documentation sometimes uses HP, hits to pop, and RBE in the same entry. These values are not automatically interchangeable. This wiki preserves the terminology used by the source and flags uncertain or contradictory values.

### Track speed

Speed values are often described relative to a Red Bloon. A value such as 200% means twice the reference speed, not twice the health.

## Regular Bloons

The BTDX community Bloons page documents Red, Blue, Green, Yellow, Pink, and Black as the basic regular sequence. Blue, Green, Yellow, and Pink reveal lower-colour Bloons when popped. Black is described as splitting into two Pink Bloons.

See the [Standard and Nested Bloons index](Standard/Overview.md) for the full list of individual articles.

Basic pages:
- [Red Bloon](Standard/Red-Bloon.md)
- [Blue Bloon](Standard/Blue-Bloon.md)
- [Green Bloon](Standard/Green-Bloon.md)
- [Yellow Bloon](Standard/Yellow-Bloon.md)
- [Pink Bloon](Standard/Pink-Bloon.md)
- [Black Bloon](Standard/Black-Bloon.md)

## Modified and special Bloons

BTDX adds many enemy behaviours beyond the basic colour sequence. Some are properties applied to existing Bloons; others are distinct enemies with their own health, movement, attacks, or spawning rules.

See [Properties](Properties.md) for cross-cutting mechanics and [Special Bloons](Special/Overview.md) for mission-specific enemies.

## MOAB-class Bloons

The community wiki uses MOAB-class for large blimps that require substantially more damage than ordinary Bloons. BTDX has several unusual types beyond the familiar MOAB, B.F.B., and Z.O.M.G., including LPZs, B.R.C.s, and other Nightmare-related enemies.

See [MOAB-class Bloons](MOAB-Class/Overview.md).

## Bounty Bloons

Bounty Bloons are a major BTDX feature introduced in version 1.2. They are powerful multi-stage encounters. The community wiki reports that most have four stages, while Big Bully, Clown, and Annoying have five. Beating a stage unlocks the next stage, which increases the difficulty and reward.

The Bounty directory deliberately has much longer entries than the standard Bloon pages. Each article aims to record the full stage sequence, map, attacks, spawned enemies, leak effects, reward information, and counter suggestions. Strategy recommendations are community claims and should be tested before being treated as universal.

See [Bounty Bloons](Bounty/Overview.md).

## Version and verification policy

The source wiki is community-maintained and may be incomplete, outdated, or internally inconsistent. Most values in this section are transcribed as reported rather than independently tested.

The main versions relevant to this project are:
- **Windows:** developer-listed version 1.5.1.
- **Android:** unofficial 1.5.2 adaptation.

Do not silently merge observations from these builds. Every hands-on observation should include platform, version, and (where useful) device details.

## Sources

- [BTDX Fandom: Bloons](${sources.bloons}) — primary community reference for the entries in this section.
- [BTDX Fandom: Updates](${sources.updates}) — version history and additions/fixes relevant to Bloons.

Pages marked **TBD** are intentionally incomplete. They are placeholders for researched expansion, not claims that all listed details are already known.
