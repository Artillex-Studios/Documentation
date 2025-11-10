# Placeholders

- List of the PlaceholderAPI placeholders provided by the plugin.

| Placeholder                                       | Description                                                                   |
|---------------------------------------------------|-------------------------------------------------------------------------------|
| %axhoes_top_&lt;leaderboard>_&lt;position>_name%  | Name of the top # player                                                      |
| %axhoes_top_&lt;leaderboard>_&lt;position>_value% | Value of the top # position                                                   |
| %axhoes_top_xp_&lt;position>_level%               | Displays the level of the player (use the `value` for the raw xp)             |
| %axhoes_broken_&lt;crop>%                         | The number of the given crop the player has broken.                           |
| %\axhoes_broken_blocks%                           | The number of crops the player has broken.                                    |
| %\axhoes_essence%                                 | The essence balance of the player.                                            |
| %\axhoes_player_xp%                               | The xp of the player.                                                         |
| %\axhoes_player_level%                            | The level of the player.                                                      |
| %\axhoes_player_xp_next%                          | The required xp for the next player level.                                    |
| %\axhoes_player_progress_percentage%              | The percentage of progress towards the next player level.                     |
| %\axhoes_player_progress_bar%                     | The progress towards the next player level displayed with a progress bar.     |
| %axhoes_last_&lt;statistic>%                      | Displays the amount of collected statistic. (this is used for the action bar) |

> Most numerical placeholders have a raw version, for example `&lt;axhoes_broken_blocks_raw%`

### Leaderboards:
- blocksbroken (blocks broken leaderboard)
- essence (essence leaderboard)
- xp (player xp leaderboard)
- ... every other crop type (from the crops.yml, like wheat, carrots, beetroots)

### Position:
- Leaderboard positions start from 1.
- You can customize how many positions do you need with the `config.yml -> leaderboard -> loaded-placements` setting.

### Crops:
- The crop name is the same as the material of the crop block. (in lowercase)
- See the crops.yml for the list of crops.

### List of statistics:
- money_gained,
- essence_gained,
- player_xp_gained
- tool_xp_gained,
- blocks_broken