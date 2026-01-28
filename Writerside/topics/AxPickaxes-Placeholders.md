# Placeholders

- List of the PlaceholderAPI placeholders provided by the plugin.

| Placeholder                                           | Description                                                                   |
|-------------------------------------------------------|-------------------------------------------------------------------------------|
| %axpickaxes_top_&lt;leaderboard>_&lt;position>_name%  | Name of the top # player                                                      |
| %axpickaxes_top_&lt;leaderboard>_&lt;position>_value% | Value of the top # position                                                   |
| %axpickaxes_broken_&lt;crop>%                         | The number of the given ores the player has broken.                           |
| %\axpickaxes_broken_blocks%                           | The number of ores the player has broken.                                     |
| %\axpickaxes_essence%                                 | The essence balance of the player.                                            |
| %\axpickaxes_player_xp%                               | The xp of the player.                                                         |
| %\axpickaxes_player_level%                            | The level of the player.                                                      |
| %\axpickaxes_player_xp_next%                          | The required xp for the next player level.                                    |
| %\axpickaxes_player_progress_percentage%              | The percentage of progress towards the next player level.                     |
| %\axpickaxes_player_progress_bar%                     | The progress towards the next player level displayed with a progress bar.     |
| %axpickaxes_last_&lt;statistic>%                      | Displays the amount of collected statistic. (this is used for the action bar) |

> Most numerical placeholders have a raw version, for example `&lt;axpickaxes_broken_blocks_raw%`

### Leaderboards:
- blocksbroken (blocks broken leaderboard)
- essence (essence leaderboard)
- level (player level leaderboard)
- xp (player xp leaderboard - note: this only show xp since last level up)
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