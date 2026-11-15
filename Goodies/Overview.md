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
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/spr_Monkey_Cap_Goodie/f6c54567-224e-4b29-976f-265c53442e78.png" alt="" width="32" /> Monkey Cap | “Monkeys Wear a Cap” | [Monkey Cap](Monkey-Cap.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/spr_Monkey_Beanie_Goodie/8127f917-3866-421e-8fc0-f463f9766693.png" alt="" width="32" /> Monkey Beanie | “Monkeys Wear a Beanie” | [Monkey Beanie](Monkey-Beanie.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/spr_Monkey_Party_Hat_Goodie/937664cc-a62d-4ec2-946f-0ba4e4389296.png" alt="" width="32" /> Monkey Party Hat | “Monkeys Wear a Party Hat” | [Monkey Party Hat](Monkey-Party-Hat.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/spr_Monkey_Super_Cape_Goodie/7b02cdaf-62d4-424a-ab09-d697103a7cd1.png" alt="" width="32" /> Monkey Cape | “Monkeys Wear a Cape” | [Monkey Cape](Monkey-Cape.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/spr_Monkey_Ram_Goodie/bcb43e4d-335f-4f2f-adc3-52b5b499696c.png" alt="" width="32" /> Monkey Ram | “Monkeys Look like Rams” | [Monkey Ram](Monkey-Ram.md) |

## Bloon cosmetics

| Goodie | In-game description | Article |
|---|---|---|
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/Bully_Bloon/78752601-5f40-4d0e-83b9-654deb51d65a.png" alt="" width="32" /> Bully Decal | “Bloons look Mean” | [Bully Decal](Bully-Decal.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/Big_Laughing_Bloon/big_laughing_bloon_001.png" alt="" width="32" /> Emoji Decal | “Bloons look Emoji” | [Emoji Decal](Emoji-Decal.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/Horror_Bloon/c890ca6e-8ca9-44f5-8b74-be3e0b249dd1.png" alt="" width="32" /> Horror Decal | “Bloons look Scary” | [Horror Decal](Horror-Decal.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/Clown_Bloon_spr/781ff8e8-bf62-469f-95b1-e8218c69d8f4.png" alt="" width="32" /> Clown Decal | “Bloons look Silly” | [Clown Decal](Clown-Decal.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/Weaz_Bloon_Spr/b50d4398-8574-4602-bae4-d882cd2b3fb3.png" alt="" width="32" /> Hacker Decal | “Bloons look Computery” | [Hacker Decal](Hacker-Decal.md) |

## Gameplay goodies

| Goodie | In-game description | Verified trigger/effect | Article |
|---|---|---|---|
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/spr_Love_Bloon/f577cd7b-76af-46d7-978e-8176c9b7d4a1.png" alt="" width="32" /> Loving Family | “Loving Family Gives Extra Vitality”; “Shows up at 50K+ Score” | Spawns 6 Love Bloons at each 50,000-score threshold. | [Loving Family](Loving-Family.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/Lit_Moab/1f1eca5a-ee1a-4967-b66d-e53d35b52e55.png" alt="" width="32" /> Lit MOAB | “Lit Moab gives money when hit”; “Shows up at 75K+ Score” | First spawn at 75,000 score; later spawns at 375,000-point multiples. | [Lit MOAB](Lit-MOAB.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/spr_BAD/4f027f79-61dd-44ab-b271-fa03564807ed.png" alt="" width="32" /> B.A.D. | “This Blimp is pretty Bad” | Spawns at each 666,000-score threshold. | [B.A.D.](BAD.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/spr_ULO/750faa47-e018-4bc8-9720-4f9811f631d5.png" alt="" width="32" /> U.L.O. | “Unidentified Laughing Object”; “Gives Extra Cash at start” | Spawns one U.L.O. at the beginning of a run. | [U.L.O.](ULO.md) |
| <img src="https://raw.githubusercontent.com/alert-bake/BTDX-source/main/sprites/Supra_spr/6c5ec7b1-8b90-43aa-ae99-c5f10a521db8.png" alt="" width="32" /> Super Storm | “Super Storm?”; “Shows up at 100K+ Score” | Spawns 10 Supra Storm enemies at each 100,000-score threshold. | [Super Storm](Super-Storm.md) |

## Source and verification notes

The catalogue and displayed descriptions above are read from the BTDX source's Goodie Draw events. Purchase/equip behaviour is read from the corresponding mouse events and the Goodie Controller. Gameplay spawn thresholds are read from `scripts/scr_Goodie_Use/scr_Goodie_Use.gml`.

Some store descriptions state the intended reward without exposing the full payout implementation in the Goodie spawn script. In particular, the exact vitality/cash amounts for Loving Family, Lit MOAB, and U.L.O. are not stated here because they have not yet been verified from their complete object event logic.

The source also stores and accounts for a `global.goodie16` value, but the current visible store objects and Goodie use script identify only slots 1–15. Slot 16 is therefore recorded as an unexplained save/controller field, **not** counted as a confirmed store item.

See [the Goodies source research notes](../Research/Goodies.md) for file-by-file evidence and remaining checks.
