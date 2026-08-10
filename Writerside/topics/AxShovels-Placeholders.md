# Placeholders

- List of the PlaceholderAPI placeholders provided by the plugin.

| Placeholder                                          | Description                                                                   |
|------------------------------------------------------|-------------------------------------------------------------------------------|
| %axshovels_top_&lt;leaderboard>_&lt;position>_name%  | Name of the top # player                                                      |
| %axshovels_top_&lt;leaderboard>_&lt;position>_value% | Value of the top # position                                                   |
| %axshovels_broken_&lt;block>%                        | The number of the given blocks the player has broken.                         |
| %\axshovels_broken_blocks%                           | The number of blocks the player has broken.                                         |
| %\axshovels_essence%                                 | The essence balance of the player.                                            |
| %\axshovels_player_xp%                               | The xp of the player.                                                         |
| %\axshovels_player_level%                            | The level of the player.                                                      |
| %\axshovels_player_xp_next%                          | The required xp for the next player level.                                    |
| %\axshovels_player_progress_percentage%              | The percentage of progress towards the next player level.                     |
| %\axshovels_player_progress_bar%                     | The progress towards the next player level displayed with a progress bar.     |
| %axshovels_last_&lt;statistic>%                      | Displays the amount of collected statistic. (this is used for the action bar) |
| %\axshovels_event_running%                           | Is the event active? true or false                                            |
| %\axshovels_event_statistic%                         | Returns the total collected statistic                                         |
| %\axshovels_event_statistic_raw%                     | Returns the total collected statistic without formatting                      |
| %\axshovels_event_time_left%                         | How much time is left from the event?                                         |
| %\axshovels_event_next%                              | When is the next event happening?                                             |
| %\axshovels_event_next_raw%                          | When will the next event happen? (without formatting)                         |
| %\axshovels_event_value%                             | How much did the player collect since the start of the event                  |
| %axshovels_event_top_&lt;position>_name%             | The event top # player's name                                                 |
| %axshovels_event_top_&lt;position>_value%            | How much did the event top # player collected                                 |

> Most numerical placeholders have a raw version, for example `&lt;axshovels_broken_blocks_raw%`

### Leaderboards:
- blocksbroken (blocks broken leaderboard)
- essence (essence leaderboard)
- level (player level leaderboard)
- xp (player xp leaderboard - note: this only show xp since last level up)
- ... every other block type (from the blocks.yml, like sand, gravel, mud)

### Position:
- Leaderboard positions start from 1.
- You can customize how many positions do you need with the `config.yml -> leaderboard -> loaded-placements` setting.

### Blocks:
- The block name is the same as the material of the block. (in lowercase)
- See the blocks.yml for the list of blocks.

### List of statistics:
- money_gained,
- essence_gained,
- player_xp_gained
- tool_xp_gained,
- blocks_broken