# Controls

This page separates the original game's keyboard shortcuts from the touch interface in the unofficial Android port. They should not be assumed to behave identically.

## Original game: keyboard shortcuts

| Input | Action |
|---|---|
| `Z` | Select the left upgrade path |
| `X` | Select the middle upgrade path |
| `C` | Select the right upgrade path |
| `Escape` | Deselect |
| `Space` | Start the next round / speed up |
| `Backspace` | Sell the selected tower |

### Tower-selection shortcuts

The following keyboard-to-tower assignments are an unverified transcription and should be checked against the target Windows build before being treated as definitive.

| Key | Tower |
|---|---|
| `1` | Dart Monkey |
| `Q` | Tack Shooter |
| `2` | Boomerang Thrower |
| `W` | Sniper Monkey |
| `3` | Ninja Monkey |
| `E` | Bomb Shooter |
| `4` | Monkey Submarine |
| `R` | Charge Tower |
| `5` | Glue Gunner |
| `T` | Ice Monkey |
| `6` | Monkey Buccaneer |
| `Y` | Monkey Engineer |
| `7` | Monkey Ace |
| `8` | Monkey Village |
| `O` | Banana Tree |
| `9` | Monkey Apprentice |
| `I` | Monkey Alchemist |
| `0` | Mortar Launcher |
| `P` | Dartling Gun |
| `F` | Spike Factory |
| `V` | Heli Pilot |
| `G` | Plasma Monkey |
| `B` | Super Monkey |
| `N` | Exploding Pineapple |
| `H` | Road Spikes |

**Verification status:** The mapping above has not been independently checked against every release. Some agent hotkeys may differ.

## Unofficial Android port

The Android adaptation is credited to Albiot1 and is listed as version 1.5.2. A touch interface is necessary on Android, but the available release listing does not document a complete control map.

For this wiki, Android controls need to be recorded from the actual 1.5.2 port rather than guessed from the Windows shortcuts.

### Touch controls

*Pending hands-on verification.*

Record each action with the exact gesture and the screen/UI element involved. Distinguish a normal intended action from an accidental or inconsistent behavior.

### Control shenanigans

#### Exploding Pineapple and Road Spikes can remain selected together

<badge>Player-reported on Android 1.5.2</badge>

The unofficial Android port can apparently allow the player to place an **Exploding Pineapple** and **Road Spikes** at the same time, rather than making the player switch cleanly from one to the other.

**Observed behavior:** Both placement items can be active together on the touch interface.

**Suspected explanation:** The original keyboard selection logic may clear the previous selection when another tower is selected. Exploding Pineapple and Road Spikes are not ordinary towers, so the Android touch-selection cleanup may not handle them in the same way. This is a plausible explanation, not a confirmed description of the port's internal code.

**Verification notes:** This report is based on a player's observation. The exact reproduction steps, device details, and whether the behavior occurs consistently still need to be recorded.

Use this section for port-specific quirks such as:
- Touches registering on the wrong UI element
- Gestures behaving differently depending on where they begin
- Controls overlapping or becoming difficult to reach
- Unexpected selection, placement, upgrade, or sell behavior
- Differences between the Android port and the original keyboard controls

Do not list a behavior as a confirmed bug until it has been reproduced or clearly attributed to a source. Include the device, Android version, game version, steps, and result where possible.

## Sources

1. [APKPure — BTD X 1.5.2](https://apkpure.net/btd-x/btdrrx.RamafpartyxAlbiot1) — third-party listing identifying the Android adaptation and version.

---

*Port-specific touch behavior is intentionally incomplete until verified in the Android build.*
