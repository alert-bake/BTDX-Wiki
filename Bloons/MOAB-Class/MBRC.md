# M.B.R.C. (Mega Big Rubbery Carrier)

## Overview

The M.B.R.C. is a Nightmare-only carrier described by the unverified report as both a blimp and a recurring Bloon spawner. It reportedly releases Bloons during its journey, then produces a large group of Brick children and one B.R.C. when popped.

## Unverified reported statistics

| Field | Reported value |
|---|---|
| Hits / HP | 2,000 |
| RBE | 13,994 |
| Speed | 37.5% of Red |
| Final children | 32 Bricks and 1 B.R.C. |
| Availability | Nightmare-only |

## Reported recurring spawns

An unverified report states that the M.B.R.C. launches 15 Purple Bloons and 3 Prismatic Bloons off-track every two seconds, summons 3 Bricks on-track every ten seconds, and releases 32 Bricks plus 1 B.R.C. when popped.

These timings and counts remain unverified. The exact spawn scheduling, whether the counts are per interval or cumulative under every mode, and the source object implementing the M.B.R.C. have not been independently confirmed.

## Implementation status

The expected `MBRC_Branch` path was not found in the source tree during this pass. That is not proof that no implementation exists; the object may use a different identifier or be assembled by mission scripts.

## Trivia

This is one of the few entries whose reported threat is not just its shell: it keeps adding enemies while it travels. Its pop result is also a carrier plus a stack of Bricks, not a single tidy child tier.

## Evidence and open questions

- **Not yet source-confirmed:** all listed statistics, spawn intervals, child composition, and Nightmare restriction.
- **Next research targets:** find the actual object identifier, inspect its recurring alarms, and verify whether the RBE includes its spawned children.
