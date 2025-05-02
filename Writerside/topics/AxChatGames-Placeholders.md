# Placeholders

* Requires [PlaceholderAPI](https://placeholderapi.com/)
* Note: You can autocomplete the placeholders in the `/papi parse me %axchatgames_` command!

![image_106.png](image_106.png)

### Valid game types:
- completion
- math
- trivia
- type
- unreverse
- unscramble
- guess_the_number

### Player Placeholders
|-|-|
| Placeholder | Description |
| %\axchatgames_wins%                            | Total wins of player |
| %\axchatgames_record%                          | Record of player |
| %axchatgames_wins_&lt;GAME TYPE>%           | Get wins of player in given GAME TYPE |
| %axchatgames_record_&lt;GAME TYPE>%         | Get record of player in given GAME TYPE |

### Game Start Placeholders
| Placeholder         | Description                       |
|---------------------|-----------------------------------|
| %\axchatgames_next% | Seconds left until next chat game |

### Leaderboard Placeholders
* Note: The number of positions can be changed with the leaderboard -> positions setting in the config.yml. Default is 1-10

| Placeholder                                                    | Description                                                     |
|----------------------------------------------------------------|-----------------------------------------------------------------|
| %axchatgames_top_wins_&lt;PLACEMENT>_name%                     | Get name of number # from global wins leaderboard               |
| %axchatgames_top_records_&lt;PLACEMENT>_name%                  | Get name of number # from global record time leaderboard        |
| %axchatgames_top_wins_&lt;PLACEMENT>_guess_the_number_name%    | Get name of number # from game specific wins leaderboard        |
| %axchatgames_top_records_&lt;PLACEMENT>_guess_the_number_name% | Get name of number # from game specific record time leaderboard |
| %axchatgames_top_wins_&lt;PLACEMENT>_stat%                     | Get wins of number # from global wins leaderboard               |
| %axchatgames_top_records_&lt;PLACEMENT>_stat%                  | Get time of number # from global record time leaderboard        |
| %axchatgames_top_wins_&lt;PLACEMENT>_guess_the_number_stat%    | Get wins of number # from game specific wins leaderboard        |
| %axchatgames_top_records_&lt;PLACEMENT>_guess_the_number_stat% | Get time of number # from game specific record time leaderboard |
