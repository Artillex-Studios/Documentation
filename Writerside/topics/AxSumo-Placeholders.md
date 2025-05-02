# Placeholders

* You can use these placeholders in almost all the builtin messages, just make sure to remove the `axsumo_<SUMO>_` part, for example:

|-|-|
| PlaceholderAPI | Builtin |
| %axsumo_&lt;SUMO>_name% | %\name% |

## List of placeholders:
|-|-|
| Placeholder | Description |
| %axsumo_&lt;SUMO>_name% | The raw name of the sumo |
| %axsumo_&lt;SUMO>_displayName% | The display name of the sumo |
| %axsumo_&lt;SUMO>_player1% | The player currently fighting |
| %axsumo_&lt;SUMO>_player2% | The second player currently fighting |
| %axsumo_&lt;SUMO>_round% | The current round number of the arena |
| %axsumo_&lt;SUMO>_alivePlayers% | The number of the players alive in the arena |
| %axsumo_&lt;SUMO>_players% | The players in the arena |
| %axsumo_&lt;SUMO>_maxPlayers% | The player limit in the arena |
| %axsumo_&lt;SUMO>_time% | The time related to the current state |
| %axsumo_&lt;SUMO>_time_formatted% | The time related to the current state, formatted |
| %axsumo_&lt;SUMO>_state% | The state of the sumo arena |
| %\axsumo_player_wins% | wins of the player |
| %axsumo_top_[[time]](AxSumo-Time.md)_&lt;placement>_player_name% | leaderboard |
| %axsumo_top_[[time]](AxSumo-Time.md)_&lt;placement>_player_wins% | leaderboard |
| %axsumo_top_&lt;placement>_player_name% | leaderboard |
| %axsumo_top_&lt;placement>_player_wins% | leaderboard |
| %axsumo_&lt;SUMO>_next% | next sumo schedule run time, in seconds |
| %axsumo_&lt;SUMO>_next_formatted% | time until next sumo event, formatted |
| %axsumo_next_&lt;SCHEDULE>% | schedule next run time, in seconds |
| %axsumo_next_&lt;SCHEDULE>_formatted% | schedule next run time, formatted |