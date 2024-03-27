# Placeholders

* You can use these placeholders in almost all the builtin messages, just make sure to remove the `axsumo_<SUMO>_` part, for example:

|-|-|
| PlaceholderAPI | Builtin |
| %axsumo_\<SUMO\>_name\% | %\name% |

## List of placeholders:
|-|-|
| Placeholder | Description |
| %axsumo_\<SUMO>_name% | The raw name of the sumo |
| %axsumo_\<SUMO>_displayName% | The display name of the sumo |
| %axsumo_\<SUMO>_player1% | The player currently fighting |
| %axsumo_\<SUMO>_player2% | The second player currently fighting |
| %axsumo_\<SUMO>_round% | The current round number of the arena |
| %axsumo_\<SUMO>_alivePlayers% | The number of the players alive in the arena |
| %axsumo_\<SUMO>_players% | The players in the arena |
| %axsumo_\<SUMO>_maxPlayers% | The player limit in the arena |
| %axsumo_\<SUMO>_time% | The time related to the current state |
| %axsumo_\<SUMO>_time_formatted% | The time related to the current state, formatted |
| %axsumo_\<SUMO>_state% | The state of the sumo arena |
| %\axsumo_player_wins% | wins of the player |
| %axsumo_top_[\[time\]](AxSumo-Time.md)_\<placement\>_player_name% | leaderboard |
| %axsumo_top_[\[time\]](AxSumo-Time.md)_\<placement\>_player_wins% | leaderboard |
| %axsumo_top_\<placement\>_player_name% | leaderboard |
| %axsumo_top_\<placement\>_player_wins% | leaderboard |
| %axsumo_\<SUMO>_next% | next sumo schedule run time, in seconds |
| %axsumo_\<SUMO>_next_formatted% | time until next sumo event, formatted |