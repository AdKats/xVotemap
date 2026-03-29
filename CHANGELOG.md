# Changelog

## v2.0.0 — Procon v2 Refactor

- Move source to `src/` directory, convert encoding from UTF-16LE to UTF-8 with LF line endings
- Convert code style to System types (`String`, `Int32`, `Boolean`, etc.)
- Add `.editorconfig` and `xVotemap.csproj` for CI format checks
- Add CI and release GitHub Actions workflows
- Add `CLAUDE.md`, `README.md`, `CHANGELOG.md`, `LICENSE`, `.gitignore`
- Archive original Procon v1 code on `legacy` branch

## v1.5.6.0

- NEW: New gamemode Chain Link (Dragon's Teeth DLC) is now supported

## v1.5.5.1

- Fix: Added missing gamemode CA (CarrierAssaultSmall0) to vote options

## v1.5.5.0

- NEW: New gamemode Carrier Assault (Naval Strike DLC) is now supported
- Fix: Next map display on round over scoreboard limited to last round
- Fix: Vote threshold display did not take VIP votes into account

## v1.5.4.2

- Fix: Restarting a running vote did not properly reset the votes

## v1.5.4.1

- NEW: Options (say, yell) to control the display of the next map/winning map
- Fix: Added next map display when the scoreboard is displayed
- Fix: Changed Include/Exclude VIPs to Sync VIPs

## v1.5.4.0

- NEW: Automatic Update Check
- NEW: Customizable vote banner
- NEW: Show number of votes for each map
- NEW: Exclude current gamemode from vote options
- NEW: Time limit effective for all gamemodes (BF4 round time limit)
- Fix: Increase possible number of vote options
- Fix: Fixed error removing duplicates
- Fix: Version Number

## v1.5.3

- FIX: SetVoteStartAndEndTimes exception is now fixed (for all gamemodes)
- FIX: Changed some messages to better reflect current status
- FIX: If the game server reports total-rounds = 0, votemap will assume total-rounds = 1

## v1.5.2

- FIX: SetVoteStartAndEndTimes exception is now fixed
- FIX: Increased max players to start to 70
- NEW: Dynamic prefix vote options

## v1.5.1

- FIX: Short tags for BF4 GameModes

## v1.5

- NEW: BF4 Support

## v1.4.4

- FIX: Too many reservedSlots (ServerVIPs) requests
- NEW: Various improvements

## v1.4.3

- Added: End Game Modes (CTF)

## v1.4.2

- Fix: Public confirmation message was not updating correctly
- Fix: Removal of duplicates in vote options was not working under certain circumstances

## v1.4.1

- Added: Aftermath Modes (Scavenger)
- Added: Option to enable/disable auto including ServerVIPs/ReservedSlots in VIP List

## v1.4.0

- Added: VIP List
- Added: VIP VoteCount
- Fixed: Show maps only once if they are double in maplist
- Fixed: GameModes

## v1.3.1

- Fixed: /votemap to start a map vote

## v1.3.0

- Added: Yell announcement
- Added: In-game enable and disable

## v1.2.3

- Fixed: Mapnames fixed from patch

## v1.2.2

- Fixed: Maplist sort for Map Only and Gametype Only

## v1.2.1

- Added: Integration with Ultimate Map Manager
- Fixed: Remove current map bug
- Added: Improved map options display
- Fixed: Gamemode should appear throughout the in-game message if turned on

## v1.2.0

- Added: Ability to disable vote results from being displayed
- Added: Option to change the way the maplist is sorted
- Added: Option to display the nextmap before the vote
- Added: Option to set minimum and maximum player count limits

## v1.1.5

- Added: More debug messages
- Fix: Serverinfo bug
- Change: Renamed to xVotemap (delete old CxVotemap)

## v1.1.4

- Fix: /votemap command now works on all rounds
- Fix: Between rounds error bug

## v1.1.3

- Fix: Votemap starting too early

## v1.1.2

- Fix: Minimal changes

## v1.1.1

- Fix: Several bugs in the randomness code

## v1.1.0

- Added: Randomness algorithm for map option selection
- Added: Ability to disable votemap starting automatically

## v1.0.1

- Fixed: Tweaked various algorithms
- Fixed: Squad rush bug

## v1.0.0

- Added: Warning for incorrect vote command

## v0.0.8

- Fix: Exclude current map
- Fix: Change to rush start time estimate

## v0.0.7

- Fix: Mixed-mode bug
- Added: Customizable number of vote options
- Added: Option to display the gamemode in the vote options
- Added: Admins with mapchanging privileges can initiate/restart Votemap in-game

## v0.0.6

- Fix: Bug where the last map in the maplist would not be selected
- Added: /nextmap command

## v0.0.5

- Fixed: Last round bug

## v0.0.4

- Added: Exclude current map option
- Fixed: xVotemap stopping due to rush map detection

## v0.0.3

- Changed: Vote threshold compared to total votes cast rather than winning map
- Added: Random selection from tied maps in case of a draw
- Added: Rush and Deathmatch support

## v0.0.2

- Fix: Vote banner not showing

## v0.0.1

- Initial Beta
