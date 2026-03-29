# xVotemap — Procon v2 Plugin

## Project Overview

xVotemap is a C# map voting plugin for Procon v2 (Battlefield game server administration). It allows players to vote for the next map near the end of a round. The legacy Procon v1 version lives on the `legacy` branch.

- **Language:** C#
- **License:** GPLv3
- **Version:** 1.5.6.0
- **Author:** onegrizzlybeer/grizzlybeer, Hexacanon EG modification, Hand of Shadow, versions <=1.3.1 by aether
- **Supported games:** BF3, BF4
- **Dependencies:** None (uses only Procon core and .NET Framework types)

## Architecture

The plugin is a single file (`src/xVotemap.cs`) containing:

- **Class:** `xVotemap` in namespace `PRoConEvents`, extends `PRoConPluginAPI`, implements `IPRoConPluginInterface`
- **Inner class:** `Players` — tracks player state (name, team, squad, vote)
- **Inner class:** `Player` — individual player data
- **Inner class:** `Squad` — team/squad identifier
- **Enum:** `enumBoolYesNo` (from Procon API)

## Event Registrations

Registered in `OnPluginLoaded`:
- `OnListPlayers` — updates player count and player database
- `OnPlayerLeft` — removes player from tracking
- `OnServerInfo` — main logic driver; checks round time, scores, triggers vote timing
- `OnGameModeCounter` — updates ticket counter limit
- `OnMaplistList` — updates current map list, detects changes
- `OnMaplistGetMapIndices` — tracks current and next map indices
- `OnGlobalChat`, `OnTeamChat`, `OnSquadChat` — processes vote commands
- `OnRoundOver` — stops voting, displays results
- `OnLevelLoaded` — detects last round, starts voting system
- `OnRestartLevel` — stops voting system
- `OnEndRound` — registered but handled by base class
- `OnRunNextLevel` — stops voting, displays results
- `OnReservedSlotsList` — syncs VIP list
- `OnRoundOverTeamScores` — displays next map on scoreboard

## Threading Model

No dedicated threads. The plugin uses a timer-based approach driven by `OnServerInfo` events (throttled to every 20 seconds). Voting logic runs synchronously within event handlers. A single `derplock` object is used for locking around vote counting operations.

## Key Features

- Automatic or manual vote triggering
- Configurable number of map options (2-8)
- Weighted random map selection based on play history
- VIP vote multiplier (sync with reserved slots)
- Vote banner display (say/yell)
- Exclude current map/gamemode from options
- Minimum/maximum player count thresholds
- Public vote confirmation messages
- Next map display after voting ends

## Code Style

Style is enforced by `.editorconfig` and checked via `dotnet format` in CI.

**Critical conventions:**
- **Use `String`, `Int32`, `Boolean`, `Double`** — NOT `string`, `int`, `bool`, `double`. The codebase uses explicit System type names everywhere.
- **Allman brace style** — opening brace on its own line
- **4 spaces** for indentation, LF line endings
- **Block-scoped namespaces** (not file-scoped)
- **`using` directives outside namespace**, System usings first

## Build & CI

- `xVotemap.csproj` at root is a **CI-only artifact** for `dotnet format`. It is NOT a real build file — Procon v2 assemblies are unavailable for compilation.
- **CI workflow** (`.github/workflows/ci.yml`): runs on push to `master` and PRs. Checks `dotnet format whitespace` and `dotnet format style --exclude-diagnostics IDE1007`.
- **Release workflow** (`.github/workflows/release.yml`): triggered by `v*` tags. Packages `.cs` files from `src/` into a zip and creates a GitHub Release.

### Running style checks locally

```bash
dotnet restore
dotnet format whitespace --verify-no-changes
dotnet format style --verify-no-changes --severity warn --exclude-diagnostics IDE1007
```

## Branch Structure

- `master` — current development, Procon v2 only
- `legacy` — archived Procon v1 version, no longer maintained
