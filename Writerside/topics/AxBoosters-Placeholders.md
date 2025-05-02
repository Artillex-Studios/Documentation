# Placeholders

* Requires [PlaceholderAPI](https://placeholderapi.com/)

* You **must replace** the # with a number, for example for the first active booster is 1 the second is 2.. and so on.
* Example: **%\axboosters_active_3_multiplier%**
* If no such booster is active, you can define a 'no booster message' in the lang.yml!

|-|-|
| Placeholder | Description |
| %axboosters_active_#_audience% | Audience of the booster |
| %axboosters_active_#_type% | Type of the booster |
| %axboosters_active_#_multiplier% | Multiplier of the booster (example: +50%) |
| %axboosters_active_#_multiplier_decimal% | Multiplier of the booster in decimal format (example: 1.5x) |
| %axboosters_active_#_length% | The formatted length of the booster |
| %axboosters_active_#_lengthraw% | The length of of the booster in seconds |
| %axboosters_active_#_time% | The formatted time left from the booster |
| %axboosters_active_#_timeraw% | The time left from the booster in seconds |
| %axboosters_multiplier_[&lt;booster hook>](https://docs.artillex-studios.com/axboosters-supported-plugins.html#booster-hooks)% | Get the multiplier for a certain booster type |
| %axboosters_multiplier_[&lt;booster hook>](https://docs.artillex-studios.com/axboosters-supported-plugins.html#booster-hooks)_decimal% | Get the multiplier (in decimal format) for a certain booster type |
