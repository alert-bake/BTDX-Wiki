# S.L.P.Z. (Storm Lightning Powered Zeppelin)

## Overview

The S.L.P.Z. is described by the community reference as a Nightmare-only, shielded evolution of the L.P.Z. It reportedly has a large shield, a separate shell, piercing stun projectiles, and a speed increase after its shield is removed.

## Community-reported statistics

| Field | Reported value |
|---|---|
| Shell hits / HP | 1,000 |
| Shield | 3,500 |
| RBE | 5,910 + 3,500 shield |
| Shielded speed | About 65.63% of Red |
| Post-shield speed | About 109.38% of Red |
| Children | 10 Static Mini M.O.A.B.s |
| Availability | Nightmare-only |

## Reported mechanics

The community reference reports that the S.L.P.Z. fires piercing stun projectiles, stuns nearby towers after its shield is depleted, accelerates after losing its shield, and releases ten Static Mini M.O.A.B.s when popped.

These details remain community-reported. The exact shield/shell formulas, projectile cadence, post-shield behaviour, and child creation have not been matched to a source object in this pass.

## Implementation status

An exact `SLPZ_Branch` source path was not found in the inspected source tree. Do not assume it shares every implementation detail with the regular L.P.Z. merely because the names are related.

## Trivia

The reported speed changes after shield loss, but the page keeps shield and shell separate. Losing the shield is not the same event as popping the whole blimp.

## Evidence and open questions

- **Community-reported:** [BTDX Fandom — Bloons](https://bloons-tdx.fandom.com/wiki/Bloons).
- **Not yet source-confirmed:** shield and shell values, speed states, attack cadence, stun radius, children, and Nightmare restriction.
- **Next research targets:** identify the source object and spawn path, trace its attack projectile, and verify the shield-break event separately from shell depletion.
