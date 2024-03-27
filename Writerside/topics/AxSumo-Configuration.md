# Configuration

## config.yml
|-|-|
| Name | Default | Description |
| timer-format | 1 | 1 - HH:MM:SS, for example 01:25:35<br></br>2 - short format, for example 20m<br></br>3 - text format, for example 01h 25m 35s |
| leaderboard-update-seconds | 180 | How often should leaderboards update? |
| waiting-time | 180 | How long should players have to wait for the arena to start? |
| broadcast-seconds | [150, 120, 90, 60, 45, 30, 15, 10, 5, 3, 2, 1] | Before the sumo starts, how many seconds before should there be a broadcast to the players? |
| seconds-between-rounds | 10 | How long should players have to wait after someone wins a round? |
| seconds-before-round-start | 5 | After getting teleported to the sumo arena, how many seconds should they have to wait before moving? |
| minimum-players | 2 | Minimum players needed for the sumo to start |
| maximum-players | -1 | Maximum players in that can join the arena, -1 to disable |
| allow-joining-after-start | true | If you enable this, people will be able to join the arena as a SPECTATOR even after it has started |
| force-empty-inventory | false | If you enable this, players will have to have an empty inventory to join a sumo |
| allowed-commands | [/axsumo, /sumo] | Allowed commands during sumo events |
| database.type | h2 | The database to use, values: h2, sqlite, mysql, postgresql |