# AuroraUHC

AuroraUHC is a Bedrock UHC minigame server ported from a legacy PocketMine
codebase to Axolotl-PM API 5.

This repository is the public project summary for a private, reproducible
server backup. It intentionally contains no live server files, player data,
worlds, host credentials or proprietary third-party source.

## What was built

- FFA and team-based UHC matches with configurable grace, final heal and
  border schedules.
- Random player scattering, spectator/staff flows and clean arena handling.
- Scenario system with 20 gameplay modifiers.
- Bedrock forms, waiting/spectator kits, scoreboard, bossbar and a forced
  Aurora-themed resource pack.
- API 5 compatibility work for items, effects, packets, entities, tasks,
  world loading and Bedrock inventory interactions.
- Local static tests, server smoke tests and a successful end-to-end UHC run.

## Engineering focus

The port separates source code from runtime state and uses a repeatable build
to package plugins and the resource pack. The tested deployment uses
Axolotl-PM 5.50.0 with RakNet on Bedrock protocol v26.50.

See:

- [`ARCHITECTURE.md`](ARCHITECTURE.md)
- [`TESTING.md`](TESTING.md)
- [`ATTRIBUTIONS.md`](ATTRIBUTIONS.md)

The private repository contains the operational source and deployment
documentation. Contact the project owner for access to the complete backup.
