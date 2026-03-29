# xVotemap

A map voting plugin for Procon (Battlefield 3 and Battlefield 4 game server administration).

xVotemap calls an in-game vote for the next map near the end of the round. It randomly selects maps from the current map list as vote options, tallies player votes, and sets the winning map as the next map.

## Features

- **Automatic vote triggering** based on round time, ticket count, and MCOM progress
- **Configurable vote options** (2-8 maps per vote)
- **Weighted random selection** — maps not played recently have a higher chance of appearing as options, controlled by a "Randomness" slider (0-10)
- **VIP vote multiplier** — reserved slot players can have their votes count multiple times
- **Vote banner** — customizable say/yell banner to announce voting
- **Exclude current map/gamemode** from vote options
- **Player count thresholds** — minimum and maximum player counts for votes to start
- **Public vote confirmation** — optionally announce each player's vote
- **Next map display** — periodically shows the winning map after voting ends
- **Admin commands** — in-game enable/disable and manual vote triggering for privileged users

## Installation

1. Download `xVotemap.cs` from the [Releases](../../releases) page.
2. Place the file in your Procon `Plugins/BF4/` (or `Plugins/BF3/`) directory.
3. Restart Procon or reload plugins.
4. Enable xVotemap in the plugin list and configure settings.

## In-Game Commands

| Command | Description |
|---------|-------------|
| `/#` | Vote for option number # (e.g., `/1`, `/2`) |
| `/v` | Display current vote options, or time until vote starts |
| `/nextmap` | Display the next map |
| `/votemap` | Initiate or restart a vote (requires map-changing privileges) |
| `enablevotemap` | Enable the plugin (requires map-changing privileges) |
| `disablevotemap` | Disable the plugin (requires map-changing privileges) |

## Settings

### Display

- **Enable Vote Banner?** — Show attention banner before voting: First, All, or Disabled
- **Banner Type** — Say, Yell, or Both
- **Banner Yell Duration** — How long the yell banner displays (seconds)
- **Show Gamemode in Voting Options?** — Include gamemode shorthand in vote options
- **Show Nextmap Before Vote?** — Display the default next map before voting starts
- **Voting Options Interval** — How often vote options are redisplayed (seconds)
- **Next Map Display Interval** — How often the winning map is shown after voting (-1 to disable)
- **Disable Vote Results Display?** — Hide detailed vote results
- **User Vote Prefix** — Single character prefix for vote commands (default: `/`)

### Voting

- **Voting Trigger** — Automatic or Manual
- **Voting Duration** — Length of the voting period (seconds)
- **Voting Threshold** — Minimum number of votes for a valid result
- **Time before Round End to Start Vote** — Seconds before estimated round end to start the vote
- **Time before Round End to Stop Vote** — Seconds before round end to close voting

### Map Options

- **Number of Vote Options** — How many maps to offer (2-8)
- **Exclude Current Map?** — Prevent the current map from appearing in options
- **Exclude Current Gamemode?** — Prevent the current gamemode from appearing in options
- **Sort Maplist by** — Map Only, Map and Gametype, or Gametype Only
- **Randomness** — Weight randomness of map selection (0 = strict rotation, 10 = fully random)

### Limits

- **Minimum Players for Start** — Minimum player count for voting to begin
- **Maximum Players for Start** — Maximum player count for voting to begin

### VIP

- **Sync Reserved Slots** — Automatically sync VIP list from reserved slots
- **VIP Vote Count** — Number of votes each VIP's vote counts as

## Supported Games

- Battlefield 3 (BF3)
- Battlefield 4 (BF4)

## License

This project is licensed under the GNU General Public License v3.0. See [LICENSE](LICENSE) for details.
