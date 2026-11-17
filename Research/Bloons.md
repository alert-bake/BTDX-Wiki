# Bloons research log

Working research register for the BTDX Bloons section. This is a research index, not a claim that every unverified report value has been independently reproduced in-game.

## Primary references

- [BTDX-source](https://github.com/alert-bake/BTDX-source) — primary implementation reference for source-backed mechanics.

## Version policy

- Main reference builds: Windows 1.5.1 and unofficial Android 1.5.2.
- Never merge observations from different platforms/builds without labels.
- Unverified reported values remain unverified until independently tested.
- A source object proves that code exists in the inspected source tree; it does not prove the object appears in every mode or platform.
- Do not fill BTDX gaps with BTD5/BTD6 stats.

## Current documentation coverage

### Standard and nested Bloons

- [x] Main Bloon overview expanded.
- [x] Standard Bloon index expanded with normal-branch `bloonlayer` values and speed multipliers.
- [x] Hierarchy article distinguishes ordinary pop reports from Chipper fractional-layer splitting.
- [x] 17 individual entries expanded: Red, Orange, Blue, Cyan, Green, Lime, Yellow, Amber, Pink, Purple, Black, White, Zebra, Rainbow, Prismatic, Ceramic, and Brick.
- [x] Corrupted Red, Blue, Green, Yellow, and Pink articles replaced.

### Properties and modifiers

- [x] Consolidated properties reference linked to individual pages.
- [x] 10 individual property pages expanded: Camo, Regrow, Lead, Tattered, Splitting, Shielded, Super Shield, Static/Energized, Sun-Blessed/Solar, and Color Splash.
- [ ] Ninja, Robo, Rag, Reincarnated Rag, and Undying Rag remain special-form research rather than ordinary property pages.

### MOAB-class Bloons

- [x] MOAB-class overview expanded with a reported-stat table and source formula comparison.
- [x] All 14 individual MOAB-class articles expanded.
- [x] Source-backed child relationships documented for Mini M.O.A.B., M.O.A.B., B.F.B., Z.O.M.G., H.T.A., B.R.C., D.D.T., L.P.Z., Rocket Blimp, and Party Blimp.
- [x] Entries without a located implementation explicitly labelled as not yet located for P.H.T.A., M.B.R.C., D.D.D.T., and S.L.P.Z.
- [x] Mini M.O.A.B. and M.O.A.B. speed discrepancies recorded as unresolved pending build-specific testing.

### Bounty Bloons

- [x] Bounty overview expanded with all 14 families, reported stage counts, reward ranks, and source cross-checks.
- [x] All 14 individual Bounty articles expanded.
- [x] Source-backed behaviour added where matching objects/events were found.
- [x] Differences between observed reports and source defaults recorded for Mighty MOAB, Flying Bloon, The Mother, Knight Bloon, and Annoying Bloon.
- [x] The Mother's early `exit;` in Alarm 2 documented as making later tower-rearrangement code unreachable in the inspected source.

## Source-backed findings worth preserving

### Ordinary Bloon type map

The normal branch uses integer and fractional type values from Red (1) through Prismatic (8.5). Its movement formula uses `global.bspeed × type_multiplier × (tattered + 1)`, followed by status-effect adjustments. These values are not simple remaining-hit counts.

### Chipper fractional handling

The Chipper branch handles half-step Bloon layers by reducing the type by 0.5 in the base `pophit = 0` case and creating two additional instances alongside the original. This is a Chipper-specific three-instance result, not a universal pop rule for every fractional Bloon.

### Durable and shielded types

Ceramic and Brick use separate armour branches. Shielded forms use a distinct shield pool and map large `bloonlayer` values to underlying branches. Static forms have their own doubled shield coefficients and projectile-creation logic.

### MOAB-class

The source uses `shell` and `maxshell` for several blimps, with shell coefficients multiplied by `global.bpower`. The L.P.Z. separately tracks shield and shell, changes speed after shield loss, and creates Static Bloon children when shell is depleted.

### Bounty bosses

Bounty objects use independent `hitpoints`, `maxpoints`, and custom movement/attack logic rather than the ordinary Bloon layer system. Some reported stage values differ from base Create-event values; stage-specific setup must be traced before deciding which value is correct.

## Remaining verification priorities

1. Verify all standard Bloon RBE, hit, leak, and child values in-game.
2. Verify every property interaction and combination, especially shield damage and Super Shield.
3. Trace unlocated MOAB-class entries and their mission spawn paths.
4. Verify every Bounty family and stage on Windows 1.5.1 and Android 1.5.2.
5. Resolve the source-versus-observation discrepancies recorded in the individual articles.
6. Verify reward tiers and whether rewards apply per stage, rank, or completed Bounty level.
7. Add screenshots or exact player observations with platform/version labels.
8. Continue special-form research for Ninja, Robo, Rag, Reincarnated Rag, Undying Rag, and other mission-only Bloons.

## Scope note

This register tracks documentation pages and source-research coverage. It is not a count of unique enemy entities in the game: some pages describe properties, alternate forms, hazards, mission variants, or Bounty stages rather than standalone Bloon classes.
