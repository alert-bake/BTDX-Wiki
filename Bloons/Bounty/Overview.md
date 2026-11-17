# Bounty Bloons

Bounty Bloons are a major BTDX feature introduced in version 1.2, according to the community update history. They are encounter bosses with multiple escalating stages. They are not ordinary round Bloons: their health, movement, attacks, spawned enemies, and life-drain rules can use bespoke object logic.

## How Bounty progression works


The listed difficulty ranks are:

1. Low
2. Medium
3. Moderately High
4. High
5. Very High
6. Impoppable
7. Almighty


## Reported reward table

The community source reports the following rewards per completed Bounty level:

| Rank | Monkey Money | Bloon Points | XP |
|---|---:|---:|---:|
| Low | 200 | 2 | 100,000 |
| Medium | 300 | 3 | 150,000 |
| Moderately High | 400 | 4 | 200,000 |
| High | 500 | 5 | 250,000 |
| Very High | 600 | 6 | 300,000 |
| Impoppable | 700 | 7 | 350,000 |
| Almighty | 900 | 9 | 450,000 |


## Bounty catalogue

The current community Bloons page documents fourteen Bounty families:

| Bounty | Associated map | Reported stages |
|---|---|---:|
| [Big Bully Bloon](Big-Bully-Bloon.md) | Monkey Meadows | 5 |
| [UFO Bloon](UFO-Bloon.md) | Bloon Oasis | 4 |
| [Blooming Bloon](Blooming-Bloon.md) | Autumn Acres | 4 |
| [Clown Bloon](Clown-Bloon.md) | Omega River | 5 |
| [Flying Bloon](Flying-Bloon.md) | Sky Battles | 4 |
| [Mighty MOAB](Mighty-MOAB.md) | Monkey Fort | 4 |
| [Super Bloon](Super-Bloon.md) | Swamp Spirals | 4 |
| [Worm Bloon](Worm-Bloon.md) | Rubber Rug | 4 |
| [Annoying Bloon](Annoying-Bloon.md) | Shade Woods | 5 |
| [Horror Bloon](Horror-Bloon.md) | The Depths | 4 |
| [Knight Bloon](Knight-Bloon.md) | Bloon Light Throwback | 4 |
| [The Mother](The-Mother.md) | Minecarts | 4 |
| [tDoM (the Destroyer of Monkeys)](tDoM.md) | Graveyard | 4 |
| [Track Crawler](Track-Crawler.md) | Bloon Circles X | 4 |


## What the source confirms so far

The source repository contains dedicated objects and event logic for the following Bounty families. These findings are implementation observations; they do not establish that every stage is available in every platform build.

| Family | Source-confirmed observation |
|---|---|
| Big Bully | Base object initializes 3,000 × `global.bpower` HP and a 1 × `global.bspeed` movement value. |
| UFO | Base object initializes 2,000 × `global.bpower` HP. It drains money by `0.1 × drain` per Step, or lives by `0.005 × drain` when money is empty; drain increases over time. |
| Blooming | HP changes with `global.flowerenable`; alarms relocate it, increase its speed variable, and create several Bloon-cluster patterns. |
| Clown | HP changes with `global.clownenable`; its alarms create Star Balls or Joker effects and alter track selection. |
| Flying | Base HP is 5,500 × `global.bpower` (or 4,000 × `global.bpower` for later enable values in the inspected Create event); alarms create Undying/Winged allies and Wind Gusts. |
| Mighty MOAB | Base HP is 27,000 × `global.bpower`; it periodically spawns Mini M.O.A.B.s, with the interval shrinking as `spawnspeed` increases. |
| Super Bloon | Base HP is 5,000 × `global.bpower`; a later form's Destroy event creates another Super Bloon form. |
| Worm | Base HP is 5,500 × `global.bpower`; it uses a dedicated path and periodically creates Undying and Winged allies. |
| Horror | `Horror_Bloon_X` has 12,666 HP in its Create event and can transition from a stationary state to a Prison Break path. |
| Knight | Base HP is 13,500 × `global.bpower`; its Step event creates two opposing Light Ball objects and changes path speed near the beginning. |
| The Mother | Base HP is 18,000 × `global.bpower`; its alarm creates Creep Bloons, stuns nearby Monkey/Necromancer objects, and increases its strength. |
| tDoM | Create logic selects paths by map and sets variant-dependent HP; its Destroy event can create a second-phase form. |
| Track Crawler | Base HP is 14,400 × `global.bpower`; it moves directly toward the End object and periodically fires a Web Shot at a nearby Monkey. |
| Annoying | Candidate objects include `Emoji_God`, `Terrible_1`, and `DDT_Terrible`; their stage mapping is not yet fully established. |

## Discrepancies worth preserving

Several community values do not match the inspected base objects:
- Mighty MOAB is reported at 40,000 HP for Stage 1, while its base Create event initializes 27,000 × `global.bpower`.
- The Mother is reported at approximately 12,000 HP, while its base Create event initializes 18,000 × `global.bpower`.
- Knight is reported at approximately 100,000 HP, while the inspected base Create event initializes 13,500 × `global.bpower`.
- The Flying Bloon community description says later stages gain HP, while the base Create event sets 4,000 × `global.bpower` for `global.flyingenable > 1`.
- The Annoying family description reports 200-HP D.D.T.-property Bloons, while the inspected `DDT_Terrible` object initializes 300 HP.

These are not necessarily errors in either source: stage-specific setup, mode multipliers, or different variants may explain them. Until traced, keep both observations and label their provenance.

The Mother source also has an `Alarm_2` event whose first statement is `exit;`. Tower-rearrangement code appears below that exit and is unreachable in the inspected event. The community claim may describe another build or code path.

## Individual page standard

Each Bounty article aims to document:
- Identity, appearance, and associated map.
- Every known stage and its named form.
- HP, speed, attacks, and leak penalties where reported.
- Recurring spawns, child enemies, and hazards.
- Tower interactions and status effects.
- Community-suggested counters, clearly labelled as suggestions.
- Source-confirmed mechanics, community-only reports, version differences, and unresolved questions.

## Research priorities

1. Verify whether all fourteen families are present in the target Android build.
2. Record exact stage health and leak penalties in-game.
3. Confirm whether the listed reward table is per stage, per rank, or another progression unit.
4. Resolve the source/community HP discrepancies listed above.
5. Inspect all later-stage variants, not only each family's base object.
6. Record any changes between Windows 1.5.1 and Android 1.5.2.

## Sources

- [BTDX-source](https://github.com/alert-bake/BTDX-source) — Create, Step, Alarm, and Destroy events.
