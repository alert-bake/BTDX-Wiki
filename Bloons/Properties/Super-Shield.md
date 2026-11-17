# Super Shield

## Overview

Super Shield is a stronger shield variant reported to appear in Nightmare Mode. an unverified report describes it as absorbing twice as much damage as a regular Shielded Bloon's shield.

## Reported behaviour

- Appears in Nightmare Mode.
- Absorbs twice the damage of a regular shield.
- No stacking combinations are listed by the unverified report.

The available source inspection confirms the ordinary Shielded branch's shield calculations and a separate Static branch with doubled shield coefficients. It does **not** yet establish a distinct Super Shield object or prove that Nightmare Mode's Super Shield is implemented by the same code path as Static.

## Implementation status

| Question | Status |
|---|---|
| Dedicated Super Shield branch/object | Not established |
| Exact multiplier in the target build | unverified report 2× |
| Whether it shares Static's implementation | Unconfirmed |
| Mode availability | unverified report Nightmare Mode |

Do not identify Super Shield and Static as the same property without locating the relevant Nightmare Mode spawn and damage paths.

## Trivia

The source has a doubled shield formula for Static Bloons, but that is not enough to declare every 2× shield a Static Bloon. Same arithmetic, different evidence.

## Evidence

- **Related source:** [Static_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Static_Bloon_Branch/Step_0.gml).
- **Needs source tracing and in-game verification:** Nightmare Mode spawn setup, exact shield multiplier, and whether a dedicated Super Shield state exists.
