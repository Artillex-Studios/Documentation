# Configuration

## config.yml

### timer-format (default: 1)
* There are 3 modes:
  * 1 - HH:MM:SS, for example 01:25:35
  * 2 - short format, for example 20m
  * 3 - text format, for example 01h 25m 35s

### command-aliases
* You can add or edit the command aliases here
* The first element of the list will be used as the "main" command

### reset-after-reward (default: false)
* Should the timer reset after a player gets their afk zone rewards?
* This is just for the placeholders, it will not change functionality

### zone-per-ip-limit (default: -1)
* How many players can gain rewards at once from a single ip at one zone?
* Set to -1 for unlimited

## Zone configuration files

### reward-time-seconds (default: 60)
* How often should players in the zone get rewards?
* This is in seconds

### roll-amount (default: 3)
* How many rewards should be rolled after the time has passed?