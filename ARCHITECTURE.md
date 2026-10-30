# Architecture

## Runtime layers

```text
Falix / local host
└── Axolotl-PM 5.50.0
    ├── Lourdes-Addon
    │   ├── player/rank state
    │   ├── Bedrock forms and inventory interactions
    │   ├── scoreboard/bossbar
    │   └── compatibility helpers
    ├── Lourdes-UHC-main
    │   ├── match lifecycle
    │   ├── scenarios
    │   ├── teams, scatter and border
    │   └── lobby/practice/staff flows
    ├── Anti-Switch
    └── AuroraUHC texture pack
```

## Match lifecycle

1. Players wait in `Lobby`.
2. The host configures an arena, teams, border and scenarios.
3. The server loads a clean arena copy and scatters active players.
4. Grace period, PvP, final heal and border schedules advance through named
   game states.
5. Eliminated players become spectators; winner and kill feeds are emitted.
6. The modified arena is discarded and replaced with a clean copy for the
   next match.

The last step is operationally important: the UHC modifies its selected world
and is not a world-reset plugin.

## Compatibility boundary

The original code targeted an older PocketMine API. The port replaces removed
APIs with API 5 equivalents, including:

- `VanillaItems`, `VanillaBlocks` and modern enchantment/effect managers;
- API 5 task handlers and world/chunk loading;
- Bedrock inventory stack requests and modern fishing-hook entities;
- named game states instead of numeric state assumptions;
- safe legacy item/block conversion for old UHC scenarios.

The source tree is intentionally separate from `server/` runtime state so a
clean deployment can be recreated without copying player identities or a
modified arena.
