# MOAB-class Bloons

MOAB-class Bloons are large blimp enemies with their own movement, durability, and child-spawn logic. The BTDX community reference defines the class as Bloons that require more than 74 hits to pop their outer layer. That is a community definition, not a universal source-code threshold.

## How their durability works

The inspected source uses `shell` and `maxshell` for several blimp branches. The base shell coefficient is multiplied by `global.bpower`, so the resulting shell value can change with game modifiers. Shielded blimps can also have a separate `shield` / `maxshield` pool.

Do not merge these into one generic HP stat:
- **Shell:** blimp durability in the relevant MOAB branches.
- **Shield:** a separate protective pool, as seen on the L.P.Z.
- **Armour:** used by Brick and Ceramic children after some blimps split.

## Documented roster

The table below preserves unverified report values. Source-confirmed shell coefficients and child routines are called out in individual pages. RBE, hit counts, and speed percentages remain unverified report unless the page explicitly notes a source comparison.

| Blimp | Reported hits / shell | Reported RBE | Reported children |
|---|---:|---:|---|
| [Mini M.O.A.B.](Mini-MOAB.md) | 75 | 491 | 4 Ceramics |
| [M.O.A.B.](MOAB.md) | 300 | 1,252 | 4 Bricks |
| [B.F.B.](BFB.md) | 900 | 4,656 | 3 M.O.A.B.s |
| [Z.O.M.G.](ZOMG.md) | 4,000 | 17,968 | 3 B.F.B.s |
| [H.T.A.](HTA.md) | 60 | 628 | 4 Shielded Prismatics |
| [P.H.T.A.](PHTA.md) | 10,000 | 13,326 | 9 Spectrum + 1 H.T.A. |
| [B.R.C.](BRC.md) | 500 | 4,428 | 8 Mini M.O.A.B.s |
| [M.B.R.C.](MBRC.md) | 2,000 | 13,994 | 32 Bricks + 1 B.R.C. |
| [D.D.T.](DDT.md) | 303 | 1,731 | 6 Tattered Camo Lead Bricks |
| [D.D.D.T.](DDDT.md) | 4,000 | 14,386 | 6 D.D.T.s |
| [L.P.Z.](LPZ.md) | 300 shell + 500 shield | 1,340 + shield | 10 Static Ceramics |
| [S.L.P.Z.](SLPZ.md) | 1,000 shell + 3,500 shield | 5,910 + 3,500 shield | 10 Static Mini M.O.A.B.s |
| [Rocket Blimp](Rocket-Blimp.md) | 300 | 1,252 | 4 Tattered Bricks |
| [Party Blimp](Party-Blimp.md) | 15,000 | 55,504 | 18 Rocket Blimps + 1 Z.O.M.G. |

These numbers are not a substitute for the source formulas. In particular, `global.bpower` can scale shell and shield values, and some community speed descriptions do not match the raw movement multipliers in the inspected branches.

## Source-confirmed shell and movement examples

| Source branch | Shell coefficient | Base movement formula | Pop result in source |
|---|---:|---:|---|
| Mini M.O.A.B. | 75 | `2.1 × global.bspeed` | 4 Ceramic |
| M.O.A.B. | 300 | `1.5 × global.bspeed` | 4 Brick |
| B.F.B. | 900 | `1.15 × global.bspeed` | 3 M.O.A.B. |
| Z.O.M.G. | 4,000 | `0.95 × global.bspeed` | 3 B.F.B. |
| H.T.A. | 60 | `1.8 × global.bspeed` | 4 Shielded Bloon branches |
| B.R.C. | 500 | `1.0 × global.bspeed` | 8 Mini M.O.A.B. |
| D.D.T. | 303 | `4.0 × global.bspeed` | 6 Camo Lead Tattered Bricks |
| L.P.Z. | 300 shell + 500 shield | `1.5 × global.bspeed` shielded; `3 ×` unshielded | 10 Static Bloon branches |
| Rocket Blimp | 300 | `6.5 × global.bspeed` | 4 Tattered Brick |
| Party Blimp | 15,000 | `0.9 × global.bspeed` | 18 Rocket Blimps + 1 Z.O.M.G. |

The source formulas above are from the respective branch Step events. They are not absolute speeds. The Mini M.O.A.B. and M.O.A.B. pages explicitly note discrepancies between community speed descriptions and the source multipliers when compared with the ordinary Red branch.

## Status effects

MOAB-class branches do not all share the ordinary Bloon status formulas. The inspected branches use different thresholds for freeze and glue, and can handle stun, distraction, and corrosion differently. A status-effect claim must name the relevant branch.

## Individual articles

- [Mini M.O.A.B.](Mini-MOAB.md)
- [M.O.A.B.](MOAB.md)
- [B.F.B.](BFB.md)
- [Z.O.M.G.](ZOMG.md)
- [H.T.A.](HTA.md)
- [P.H.T.A.](PHTA.md)
- [B.R.C.](BRC.md)
- [M.B.R.C.](MBRC.md)
- [D.D.T.](DDT.md)
- [D.D.D.T.](DDDT.md)
- [L.P.Z.](LPZ.md)
- [S.L.P.Z.](SLPZ.md)
- [Rocket Blimp](Rocket-Blimp.md)
- [Party Blimp](Party-Blimp.md)

## Important caveat

BTDX's roster is not identical to other Bloons games. Some entries are unique to BTDX or appear only in higher-difficulty content. The existence of a source object does not prove that it appears in normal rounds, and a community-only entry should not be promoted to source-confirmed without locating its spawn and behaviour code.

## Sources

- [BTDX-source](https://github.com/alert-bake/BTDX-source) — branch Step/Create/Alarm events.
