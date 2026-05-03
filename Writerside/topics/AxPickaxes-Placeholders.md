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
| %\axpickaxes_event_running%                           | Is the event active? true or false                                            |
| %\axpickaxes_event_statistic%                         | Returns the total collected statistic                                         |
| %\axpickaxes_event_statistic_raw%                     | Returns the total collected statistic without formatting                      |
| %\axpickaxes_event_time_left%                         | How much time is left from the event?                                         |
| %\axpickaxes_event_next%                              | When is the next event happening?                                             |
| %\axpickaxes_event_next_raw%                          | When will the next event happen? (without formatting)                         |
| %\axpickaxes_event_value%                             | How much did the player collect since the start of the event                  |
| %axpickaxes_event_top_&lt;position>_name%             | The event top # player's name                                                 |
| %axpickaxes_event_top_&lt;position>_value%            | How much did the event top # player collected                                 |

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