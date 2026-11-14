# Bloon hierarchy and nested layers

This page explains how Bloons can contain, reveal, or spawn other Bloons. Exact relationships are game-specific.

## Basic colour chain

The BTDX community reference describes this basic sequence:

| Outer Bloon | Revealed child |
|---|---|
| Blue | Red |
| Green | Blue |
| Yellow | Green |
| Pink | Yellow |
| Black | Two Pink Bloons |

The Red Bloon is the base unit and has no smaller child.

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

These are source-reported relationships; verify them against the intended game build before using them for exact calculations.

## Special spawning and splitting

Some Bloons spawn enemies without being popped, release children off-track, or create hazards that block projectiles. These behaviours should be documented on their individual pages rather than forced into the simple nested-layer model.

## RBE warning

RBE is a comparison measure, not a universal leak-damage formula. Mission-specific and special Bloons can drain lives in custom ways. See [Properties](Properties.md) and the individual enemy pages.
