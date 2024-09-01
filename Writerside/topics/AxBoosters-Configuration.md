# Configuration

```yaml
# DOCUMENTATION: https://docs.artillex-studios.com/axboosters.html

prefix: "<gradient:#0099FF:#00BBFF><b>AxBoosters</b></gradient> &7» "

database:
  # h2, mysql, postgresql
  # for single server setups we recommend h2
  type: "h2"

  # you only need to touch these when using mysql/postgresql
  address: 127.0.0.1
  port: 3306
  database: admin
  username: admin
  password: "admin"
  pool:
    maximum-pool-size: 10
    minimum-idle: 10
    maximum-lifetime: 1800000
    keepalive-time: 0
    connection-timeout: 5000

# when using mysql/postgresql, how should data be sent between servers?
# values: none, sql
# if you don't need multi server support, set to none to disable
multi-server-support: "sql"

# formats:
# 0 - percentage format, example: 10%
# 1 - decimal format, example: 1.1x
# mode 0 has some advantages, it works better with negative boosts (-30% looks better than 0.7x)
multiplier-format: 0

# should personal boosters only be broadcasted to the player in chat? (also applies to team boosters)
only-broadcast-to-affected: true

# should the boss bar move (true) or should it just be a static bar? (false)
bossbar-progress: true

# how often should the bossbar switch between boosters? (in seconds)
bossbar-switch-every-x-seconds: 3

# if enabled, people will be able to click on booster messages and in the active booster menu to send a thank you message to the booster once
enable-thanking: true

# should the plugin broadcast all the active boosters to you a few seconds after joining?
enable-join-message: true

# https://docs.oracle.com/javase/tutorial/i18n/format/decimalFormat.html
# used for multipliers
# example: #,###.## (this will make percentages only show decimal places if there are any)
number-format: "#,###.##"

# https://docs.oracle.com/javase%2F8%2Fdocs%2Fapi%2F%2F/java/text/SimpleDateFormat.html
date-format: "yyyy-MM-dd HH:mm:ss"

# modes:
# 0 - no stacking, booster with the highest multiplier will be used
# 1 - additive, so if you have two 3x boosters, it will become 5x
# 2 - multiplied, so if you have two 3x boosters, it will become 9x
# note that currently this setting does not change anything visually
multiplier-stacking-mode: 0

# if enabled, it will not allow 2 of the same booster to be run
# note that this only prevents the same PERSONAL boosters from being activated
prevent-booster-stacking: false

# makes it possible to set a cap on booster multipliers
# this is useful to prevent people getting unlimited money by stacking up tens of boosters
# example: 1000 will make it stop at 11x
# -1 to disable
booster-max-multiplier: -1

# used to show the length of boosters
# in bossbars you have to use the %\time_formatted% placeholder for these to be used
# 1 - HH:MM:SS, for example 01:25:35
# 2 - short format, for example 20m
# 3 - text format, for example 01h 25m 35s
timer-format: 1

# should item boosters be enabled?
# this can improve performance if you are not using this feature
enable-item-boosters: true

# should permission boosters be enabled?
# this can improve performance if you are not using this feature
enable-permission-boosters: true

# should be plugin notify you if there is a new update?
update-notifier:
  # if enabled, it will display the message in the console
  enabled: true
  # if enabled, it will broadcast the update message to all players who have the <plugin-name>.update-notify permission
  on-join: true

# you must define at least 1
open-command-aliases:
  - "axboosters"
  - "boosters"
  - "axbooster"
  - "booster"
  - "boost"
  - "boosts"

# do not change
version: 10
```