# Regrow

## Overview

Regrow is a Bloon property that allows the Bloon to restore lost layers over time. an unverified report reports that Regrow Bloons restore one layer every two seconds, up to their original layer.

## Implementation notes

**Source-confirmed:** ordinary Bloons initialize `regrow = 0`, and BTDX has a dedicated `Regrow_Bloon_Branch`. That branch uses the same ordinary type-to-sprite and movement mapping while selecting the Regrow appearance. It also uses an alarm when frozen, which is consistent with freeze affecting the Regrow branch's normal timing.

The existence of the branch and flag is source-confirmed. The two-second regeneration interval and the exact layer-restoration logic remain unverified report until the relevant alarm/collision paths are fully traced and tested.

## Reported behaviour

- Restores one layer every two seconds.
- Regrows only up to the Bloon's original layer.
- When a Regrow Bloon splits into children, each child can reportedly regenerate toward the original layer.
- Regrow Bloons reportedly cannot regenerate while frozen.

The child-regrowth rule can cause the number of Bloons to increase substantially if multiple children are allowed to regenerate. Treat this as a gameplay interaction, not as a statement that every split attack behaves identically.

## Stacking

an unverified report lists Regrow as compatible with:
- Tattered
- Splitting

It also describes an Undying Rag Bloon as a Rag variant with Regrow-like behaviour. That is a special mission form, not an ordinary Regrow Bloon.

## Trivia

The source's Regrow branch still uses the same type map as the normal branch. A Regrow Purple is still layer 5.5; Regrow is an added property, not a replacement type number.

## Evidence

- **Source-confirmed:** [Normal_Bloon_Branch/Create_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Normal_Bloon_Branch/Create_0.gml), [Regrow_Bloon_Branch/Step_0.gml](https://github.com/alert-bake/BTDX-source/blob/main/objects/Regrow_Bloon_Branch/Step_0.gml).
- **Needs in-game verification:** exact regeneration timing, freeze interaction, and child-regrowth edge cases.
