# Finding about Bloons

Research target: Bloon-related instance variables in the GML source of [BTDX-SOURCE](https://github.com/alert-bake/BTDX-SOURCE).

> **Evidence rule:** meanings below are inferred from actual reads, writes, conditions, and calculations in the source. They are not developer-confirmed statements unless explicitly labelled as such. Ramaf is the game's developer; no confirmation from Ramaf is being claimed here.

## Core movement and pathing

### `fast`
**Meaning: movement speed value used by the path system.**  
**Evidence: code-confirmed.**

Bloon Step events calculate or modify `fast`, then assign it to `path_speed`. For example, `Normal_Bloon_Branch/Step_0.gml` sets it from `global.bspeed` multiplied by a layer-specific factor and `(tattered + 1)`, then applies status-effect modifiers before `path_speed = fast`.

Examples from the normal branch:
- Red layer (1): `global.bspeed * 1.6 * (tattered+1)`
- Blue layer (2): `global.bspeed * 2 * (tattered+1)`
- Pink layer (5): `global.bspeed * 4.8 * (tattered+1)`
- Rainbow layer (8): `global.bspeed * 3.8 * (tattered+1)`
- Prismatic layer (8.5): `global.bspeed * 4.4 * (tattered+1)`

This is not a developer confirmation. It is directly supported by the code's assignment to `path_speed`.

### `path_speed`
**Meaning: speed consumed by the path movement system.**  
**Evidence: code-confirmed.**

The normal, shielded, brick, and MOAB branch Step events assign `path_speed = fast`. This makes `fast` the calculated speed input and `path_speed` the path-following speed property.

### `global.bspeed`
**Meaning: global Bloon speed multiplier/base value.**  
**Evidence: strongly supported by code.**

Branch speed calculations multiply this value by Bloon-specific factors. Exact units and where the global is configured still need tracing.

### `path`, `move`, `path_position`
**Meaning: path identity/reference, path movement state, and current progress along the path, respectively.**  
**Evidence: code-supported; exact engine-level semantics partly inferred.**

When Bloons split or transform, code copies `path` and `move`, calls `path_start(move, ...)`, and restores `path_position`. Child Bloons often receive a slightly offset `path_position` so they do not occupy precisely the same point.

## Layer and Bloon identity

### `bloonlayer`
**Meaning: current layer/type value used to select Bloon appearance, behavior, and transformations.**  
**Evidence: code-confirmed.**

The normal branch Step event compares this value against numbers such as 1, 1.5, 2, 2.5, through 8.5 to choose sprites and speed multipliers. The shielded branch uses values including 18, 48, 93, 348, 1248, and 5248 to select Ceramic/Brick/MOAB-class transformations.

It is not simply a conventional integer layer count: fractional values and large composite values are used.

### `bloonmaxlayer`
**Meaning: stored maximum/original layer value associated with a Bloon.**  
**Evidence: strongly supported by code; exact intended distinction from `bloonlayer` needs more tracing.**

Transformation and child-spawn code frequently copies `bloonmaxlayer` while reducing `bloonlayer` by a fixed amount. This indicates it preserves a separate layer reference while the current layer changes.

### `normal`, `bigbloon`, `shielded`, `electric`
**Meaning: Bloon class/state flags or class identifiers.**  
**Evidence: code-confirmed usage; exact enum documentation is incomplete.**

- `normal`: set to 1 for the ordinary and several armoured/MOAB branches; set to 0 for the shielded branch.
- `bigbloon`: class identifier used in collision/damage logic. Examples include 2 for Brick, 4 for MOAB, and 5/6 for larger blimps in the relevant branch Create events.
- `shielded`: set to 1 on Shielded_Bloon_Branch and checked in damage handling to route hits through shield logic.
- `electric`: checked in Bloon damage/collision logic; electric Bloons have shield-related handling. Its full gameplay meaning needs further tracing.

Do not treat `bigbloon` as a simple true/false boolean: code compares it to multiple numeric values.

## Damage and durability

### `shell`, `maxshell`
**Meaning: current and maximum shell durability for MOAB-class and other shell-based Bloons.**  
**Evidence: code-confirmed.**

In `Moab_Branch/Step_0.gml`, `maxshell` is set to `ceil(300 * global.bpower)`, `shell` is clamped to it, and the shell is initialized from `maxshell` once via `spawned`. When shell reaches zero, the MOAB splits into child Bloons.

The shielded branch also assigns shell values when shielded MOAB-tier Bloons transform into their corresponding blimp branches. Therefore shell is not a universal health variable for every Bloon; it is used by specific classes.

### `shield`, `maxshield`
**Meaning: current and maximum shield durability.**  
**Evidence: code-confirmed.**

`Shielded_Bloon_Branch/Step_0.gml` calculates `maxshield` from `bloonlayer` and `global.bpower`, clamps `shield` to the maximum, and transforms the Bloon when shield reaches zero. Other branches such as LPZ also maintain shell and shield separately.

### `armour`, `maxarmour`
**Meaning: current and maximum armour durability.**  
**Evidence: code-confirmed.**

Brick and Ceramic branches initialize armour and maximum armour, clamp armour to its maximum, and use the armour ratio to select damage-state sprites. Collision handling subtracts damage from armour and triggers child-Bloon transformations when it reaches zero.

### `global.bpower`
**Meaning: global Bloon durability/power scaling factor.**  
**Evidence: strongly supported by code.**

It scales maximum shell, shield, and armour values in several branches. Exact configuration and all effects still need tracing.

### `spawned`
**Meaning: one-time initialization guard for durability or spawn setup.**  
**Evidence: code-confirmed.**

For example, the MOAB Step event initializes `shell = maxshell` only when `spawned = 0`, then sets it to 1. Brick uses the same pattern for armour.

## Status effects and traits

### `glue`
**Meaning: glue status intensity/amount affecting movement.**  
**Evidence: code-confirmed; scale interpretation incomplete.**

Normal Bloons modify `fast` when glue is positive. MOAB-class code instead checks high glue values (for example, `glue >= 2000`) and can stop movement. Different branches implement glue differently, so do not assume one universal formula.

### `freeze`
**Meaning: freeze status value affecting movement.**  
**Evidence: code-confirmed.**

Normal Bloons set speed to zero at `freeze >= 1` and further divide speed for positive freeze values. MOAB code uses a different threshold (`freeze >= 2000`) and reduces the value over time.

### `stun`
**Meaning: stun status/state that reduces or stops movement.**  
**Evidence: code-confirmed.**

Normal Bloons set speed to zero when `stun = 1`; other branches use different numeric states (for example 1.1 or 0.3 speed handling). Some collision code decrements stun over time.

### `distraction`
**Meaning: distraction status that reverses or redirects movement by assigning negative speed.**  
**Evidence: code-confirmed.**

Normal Bloons use `fast = global.bspeed * -3 * distraction`; Brick and MOAB branches also assign negative speed under distraction conditions. Exact behavior depends on branch and the value used.

### `tattered`
**Meaning: damaged/tattered visual state that also changes speed calculations.**  
**Evidence: code-confirmed.**

Branches use `(tattered + 1)` in speed calculations and change the sprite frame when `tattered = 1`. In the ordinary branch this multiplier makes the calculated speed twice the untattered value when tattered is 1; confirm whether this is intentional gameplay behavior before describing it as a debuff/buff.

### `corrosion`
**Meaning: corrosion status value, with effects on MOAB-class Bloons.**  
**Evidence: code-confirmed usage; full behavior incomplete.**

MOAB Step code changes its visual blend when corrosion reaches 21. `obj_BAD/Alarm_4.gml` uses corrosion to schedule repeated damage ticks and subtracts shell. The exact full set of corrosion effects needs more tracing.

### `radiation`
**Meaning: radiation status/property propagated to child Bloons.**  
**Evidence: code-confirmed propagation; effect not fully established here.**

Several collision/transformation routines copy `radiation` from a parent Bloon to spawned children. Its complete mechanics are not established by the files examined for this note.

### `camo`, `lead`, `regrow`
**Meaning: Bloon trait flags.**  
**Evidence: code-confirmed.**

These are initialized to 0 on ordinary Bloons and checked during damage/collision handling. The code also sets these flags on spawned children, and Brick branch sprite selection reflects combinations of camo, lead, and regrow. Exact detection rules belong in a separate damage/targeting trace.

### `hurt`
**Meaning: damage-related state on Brick Bloons.**  
**Evidence: weak/incomplete.**

It is initialized to 0 in Brick_Bloon_Branch Create code, but the examined Step code does not establish its complete purpose. Leave undocumented beyond noting its initialization until its reads and writes are traced.

## Collision bookkeeping and splitting

### `hits`
**Meaning: per-Bloon list used to track which attackers have already registered a hit.**  
**Evidence: strongly supported by collision code.**

Collision routines search the list for an attacker identifier before applying damage, then add an entry. When a Bloon transforms or splits, code copies the list to its children. Some code paths add literal 0 rather than an instance ID, so the exact conventions need a broader audit.

### `split`
**Meaning: counter/index used to offset child Bloons during a split.**  
**Evidence: code-confirmed.**

MOAB and other blimp Step/collision routines reset it to 0, increment it for each child, and use it to calculate each child's `path_position` offset.

### `damage`
**Meaning: local damage amount used during collision processing.**  
**Evidence: code-confirmed in collision routines.**

Collision code assigns values such as `damage = 7`, subtracts damage from armour or shell, and then checks whether the durability reached zero. This is often a local variable in the collision event, not necessarily a persistent Bloon instance variable.

## Important distinctions

- `fast` is supported as a movement-speed value by GML usage, **not by a statement from Ramaf**.
- `shell`, `shield`, and `armour` are separate durability systems. Do not merge them into one generic health stat.
- `bloonlayer` is a numeric type/layer encoding, not a plain count. Fractional and large values are used.
- Variables can differ between branches. A formula found in Normal_Bloon_Branch should not automatically be applied to MOAB, Brick, Shielded, or special Bloons.
- Names alone are not enough to establish meaning. The entries above distinguish direct code behavior from inferred intent.

## Source files examined

- `objects/Normal_Bloon_Branch/Create_0.gml`
- `objects/Normal_Bloon_Branch/Step_0.gml`
- `objects/Shielded_Bloon_Branch/Create_0.gml`
- `objects/Shielded_Bloon_Branch/Step_0.gml`
- `objects/Brick_Bloon_Branch/Create_0.gml`
- `objects/Brick_Bloon_Branch/Step_0.gml`
- `objects/Moab_Branch/Create_0.gml`
- `objects/Moab_Branch/Step_0.gml`
- `objects/Bloon/Create_0.gml`
- `objects/Bloon/Step_0.gml`
- `objects/Sai/Create_0.gml`
- `objects/Alt_Sai/Create_0.gml`
- `objects/LPZ_Branch/Step_0.gml`
- `objects/obj_BAD/Alarm_4.gml`

This is a source-backed first-pass inventory of the shared and representative Bloon variables, not a claim that every special Bloon object and every event has been exhaustively audited. Special Bloons may introduce additional fields or override these behaviors.
