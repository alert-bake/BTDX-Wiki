# Goodies research notes

Working notes for documenting the BTDX Goodie Store. This file is a research scratchpad, not a definitive item catalogue.

## Current findings

### Currency loop

- Trophies are earned from achievements, at one Trophy per achievement.
- 10 Trophies are exchanged for one Goodie Token.
- Goodie Tokens are spent in the Goodie Store.
- Page 1 is described as cosmetic changes for Bloons and monkeys.
- Page 2 is described as affecting gameplay and mechanics.
- The last item on page 2 is reported to grant 200 extra starting cash in every game when equipped.

### Named unlockable: B.A.D.

The spawn details for this item still need direct verification in the target build.

### Other research lead

A third-party video overview describes page 2 as containing permanent upgrades on the left and two Bloon-related options on the right, naming the B.A.D. and a "cursed super storm." This is a secondary lead only; it is not enough to add the latter as a confirmed item. Locate direct in-game evidence first.

## Verification checklist

- [ ] Capture or transcribe every item on Goodie Store page 1.
- [ ] Capture or transcribe every item on Goodie Store page 2.
- [ ] Record each item's displayed name, cost, description, and effect.
- [ ] Record whether the item is cosmetic, gameplay-affecting, or unlocks content.
- [ ] Confirm the 10-Trophy exchange rate in-game.
- [ ] Confirm whether the B.A.D. and starting-cash bonus are present in Android 1.5.2.
- [ ] Investigate the reported "cursed super storm" without assuming it is accurate.
- [ ] Note any differences between Android 1.5.2 and Windows 1.5.1.

## Source quality notes

- **Third-party video overview:** a lead for further investigation, not confirmation.

## Research log

Add dated observations here when new evidence is collected. Include the game version and platform for every hands-on observation.

---

# Source audit: current catalogue

**Scope:** `alert-bake/BTDX-source`, branch `main`. These notes distinguish source-confirmed behaviour from store copy and unverified assumptions.

## Catalogue

A source search for the exact locked-item label **"Spend 1 Goodie Token to Unlock"** returned 15 visible Goodie Draw objects, corresponding to slots 1–15:

| Slot | Object | Category | Exact displayed description |
|---:|---|---|---|
| 1 | `Monkey_Caps_Goodie` | Monkey cosmetic | Monkeys Wear a Cap |
| 2 | `Monkey_Beanie_Goodie` | Monkey cosmetic | Monkeys Wear a Beanie |
| 3 | `Monkey_Party_Hat_Goodie` | Monkey cosmetic | Monkeys Wear a Party Hat |
| 4 | `Monkey_Cape_Goodie` | Monkey cosmetic | Monkeys Wear a Cape |
| 5 | `Monkey_Ram_Goodie` | Monkey cosmetic | Monkeys Look like Rams |
| 6 | `Bully_Decal_Goodie` | Bloon cosmetic | Bloons look Mean |
| 7 | `Emoji_Decal_Goodie` | Bloon cosmetic | Bloons look Emoji |
| 8 | `Horror_Decal_Goodie` | Bloon cosmetic | Bloons look Scary |
| 9 | `Clown_Decal_Goodie` | Bloon cosmetic | Bloons look Silly |
| 10 | `Hacker_Decal_Goodie` | Bloon cosmetic | Bloons look Computery |
| 11 | `Loving_Family_Goodie` | Gameplay | Loving Family Gives Extra Vitality; Shows up at 50K+ Score |
| 12 | `Lit_Moab_Goodie` | Gameplay | Lit Moab gives money when hit; Shows up at 75K+ Score |
| 13 | `BAD_Goodie` | Gameplay | This Blimp is pretty Bad |
| 14 | `ULO_Goodie` | Gameplay | Unidentified Laughing Object; Gives Extra Cash at start |
| 15 | `Super_Goodie` | Gameplay | Super Storm?; Shows up at 100K+ Score |

Every one of these Draw events displays **"Spend 1 Goodie Token to Unlock"** when its state is zero.

## Currency and state

- `objects/Goodie_Controller/Draw_0.gml` displays **"10 Trophies = 1 Goodie Token."**
- `objects/Goodie_Controller/Step_0.gml` sets tokens to `floor(global.trophies / 10)`, then subtracts one for each Goodie state greater than zero, including `goodie16`.
- The visible Goodie Mouse events check `global.goodieTokens > 0`. A first click changes a Goodie's state from 0 to 1 (owned); the next click equips it by changing 1 to 100; clicking again changes 100 back to 1.
- Monkey cosmetic Mouse events call `scr_Monkey_Goodie_Off()` before equipping. Bloon decal Mouse events call `scr_Bloon_Goodie_Off()`. The cosmetic groups are therefore mutually exclusive within their own category.
- `objects/Control/Create_0.gml` initializes each gameplay-goodie run counter to -1, then sets it to 0 if that Goodie is equipped.

## Gameplay spawn logic

All thresholds below come from `scripts/scr_Goodie_Use/scr_Goodie_Use.gml`.

### Loving Family (slot 11)

Condition: `global.points >= 50000 * (global.loveGoodieUse + 1)`, with the Goodie equipped.

Action: creates six `obj_Love_Bloon` instances, then increments `loveGoodieUse`. With the counter initialized to zero, this means six Love Bloons at 50k, 100k, 150k, and every 50k thereafter.

The Goodie panel says this gives extra vitality. The exact amount and award implementation are not established by this spawn script.

### Lit MOAB (slot 12)

First condition: score at least 75,000 and `litGoodieUse = 0`.

Later condition: `global.points >= 375000 * global.litGoodieUse`, with the counter at least 1.

Spawn thresholds are therefore 75k, 375k, 750k, 1.125m, and so on. Each spawned `obj_Lit_Moab` is assigned shell 999,000 and layer values 40,000 by the Goodie script.

The panel says it gives money when hit. The cash amount and exact award event are not established by the spawn script.

### B.A.D. (slot 13)

Condition: `global.points >= 666000 * (global.badGoodieUse + 1)`.

Action: creates `obj_BAD` at the `BloonSpawn` position, assigns shell 999,000 and layer values 40,000, then increments the counter. Thresholds: 666k, 1.332m, 1.998m, and so on.

### U.L.O. (slot 14)

Condition: score at least zero and `uloGoodieUse = 0`.

Action: creates one `obj_ULO` off the left side of the screen at a randomized vertical position, with speed 3–4 and direction 0; increments the counter so it only happens once per run.

The panel says it gives extra cash at the start. The exact payout is not established by the spawn script.

### Super Storm (slot 15)

Condition: `global.points >= 100000 * (global.superGoodieUse + 1)`.

Action: creates ten `obj_Supra_Storm` instances off the left edge at randomized vertical positions, assigns each a randomized speed from 1 to 4, sets direction to 0, and increments the counter. Thresholds: 100k, 200k, 300k, and so on.

## Slot 16 anomaly

`global.goodie16` appears in:
- `objects/Goodie_Controller/Step_0.gml` (token accounting),
- `objects/Variable_set_upper/Create_0.gml` (restoring the variable),
- `scripts/scr_save_career_3/scr_save_career_3.gml` (save data),
- `scripts/scr_bettersave_career/scr_bettersave_career.gml` (INI save data).

However, the exact locked-item-label search and the Goodie Draw objects found in this audit cover slots 1–15. No slot-16 store object or use effect was identified. Do not invent a sixteenth Goodie based on this orphaned field.

## Primary source files

- Display descriptions: `objects/*_Goodie/Draw_0.gml`
- Purchase/equip clicks: `objects/*_Goodie/Mouse_4.gml`
- Cosmetic selection: `scripts/scr_Draw_Skins/scr_Draw_Skins.gml`
- Cosmetic off-switches: `scripts/scr_Monkey_Goodie_Off/scr_Monkey_Goodie_Off.gml`, `scripts/scr_Bloon_Goodie_Off/scr_Bloon_Goodie_Off.gml`
- Token calculation: `objects/Goodie_Controller/Step_0.gml`, `objects/Goodie_Controller/Draw_0.gml`
- Run setup: `objects/Control/Create_0.gml`
- Gameplay spawns: `scripts/scr_Goodie_Use/scr_Goodie_Use.gml`
