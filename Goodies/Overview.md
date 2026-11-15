# Goodies

The Goodie Store has **15 visible goodies in the current source catalogue**: ten cosmetics and five gameplay modifiers. Each visible item costs **1 Goodie Token** to unlock.

- [Monkey cosmetics](#monkey-cosmetics) change the appearance of monkeys.
- [Bloon cosmetics](#bloon-cosmetics) change the appearance of Bloons.
- [Gameplay goodies](#gameplay-goodies) add score-triggered spawns or a starting-run bonus.

## Currency and equipping

The Goodie Controller calculates Goodie Tokens as:

`floor(Trophies / 10) - number of purchased Goodies`

The in-game controller displays **“10 Trophies = 1 Goodie Token.”** A Goodie is purchased once; its state then toggles between owned-but-inactive and equipped. For the cosmetic categories, the source calls an off-switch script before equipping another item in the same category, so only one monkey cosmetic and one Bloon decal can be active at once.

Gameplay goodies are enabled by equipping them. Their run counters are initialized at the start of a game only when the corresponding Goodie is equipped.

## Monkey cosmetics

| Goodie | In-game description | Article |
|---|---|---|
| Monkey Cap | “Monkeys Wear a Cap” | [Monkey Cap](Monkey-Cap.md) |
| Monkey Beanie | “Monkeys Wear a Beanie” | [Monkey Beanie](Monkey-Beanie.md) |
| Monkey Party Hat | “Monkeys Wear a Party Hat” | [Monkey Party Hat](Monkey-Party-Hat.md) |
| Monkey Cape | “Monkeys Wear a Cape” | [Monkey Cape](Monkey-Cape.md) |
| Monkey Ram | “Monkeys Look like Rams” | [Monkey Ram](Monkey-Ram.md) |

## Bloon cosmetics

| Goodie | In-game description | Article |
|---|---|---|
| Bully Decal | “Bloons look Mean” | [Bully Decal](Bully-Decal.md) |
| Emoji Decal | “Bloons look Emoji” | [Emoji Decal](Emoji-Decal.md) |
| Horror Decal | “Bloons look Scary” | [Horror Decal](Horror-Decal.md) |
| Clown Decal | “Bloons look Silly” | [Clown Decal](Clown-Decal.md) |
| Hacker Decal | “Bloons look Computery” | [Hacker Decal](Hacker-Decal.md) |

## Gameplay goodies

| Goodie | In-game description | Verified trigger/effect | Article |
|---|---|---|---|
| Loving Family | “Loving Family Gives Extra Vitality”; “Shows up at 50K+ Score” | Spawns 6 Love Bloons at each 50,000-score threshold. | [Loving Family](Loving-Family.md) |
| Lit MOAB | “Lit Moab gives money when hit”; “Shows up at 75K+ Score” | First spawn at 75,000 score; later spawns at 375,000-point multiples. | [Lit MOAB](Lit-MOAB.md) |
| B.A.D. | “This Blimp is pretty Bad” | Spawns at each 666,000-score threshold. | [B.A.D.](BAD.md) |
| U.L.O. | “Unidentified Laughing Object”; “Gives Extra Cash at start” | Spawns one U.L.O. at the beginning of a run. | [U.L.O.](ULO.md) |
| Super Storm | “Super Storm?”; “Shows up at 100K+ Score” | Spawns 10 Supra Storm enemies at each 100,000-score threshold. | [Super Storm](Super-Storm.md) |

## Source and verification notes

The catalogue and displayed descriptions above are read from the BTDX source's Goodie Draw events. Purchase/equip behaviour is read from the corresponding mouse events and the Goodie Controller. Gameplay spawn thresholds are read from `scripts/scr_Goodie_Use/scr_Goodie_Use.gml`.

Some store descriptions state the intended reward without exposing the full payout implementation in the Goodie spawn script. In particular, the exact vitality/cash amounts for Loving Family, Lit MOAB, and U.L.O. are not stated here because they have not yet been verified from their complete object event logic.

The source also stores and accounts for a `global.goodie16` value, but the current visible store objects and Goodie use script identify only slots 1–15. Slot 16 is therefore recorded as an unexplained save/controller field, **not** counted as a confirmed store item.

See [the Goodies source research notes](../Research/Goodies.md) for file-by-file evidence and remaining checks.
