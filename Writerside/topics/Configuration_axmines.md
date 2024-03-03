# Configuration

## Example configuration
```yaml

display-name: "<red>Example"

contents:
  gold_block: 11
  diamond_block: 10
  emerald_block: 25
  iron_block: 10

selection:
  1: "world;10;10;10;10;10"
  2: "world;10;10;10;10;10"

teleport-location: "world;10;10;10;10;10"

# To top block at player's location: 0
# To teleport to teleport-location: 1
# To disable, set to anything else
teleport-on-reset: 0

actionbar:
  enabled: true
  range: 10

# For broadcast in range: >= 1
# For whole world: 0
# For all worlds: -1
# For silent mode: -2
broadcast-reset: -1

# How often the mine should reset
# 20 ticks = 1 second
reset:
  ticks: 12000 # (10 minutes)
  # At what percent the mine should automagically
  # reset set to 0 to disable
  percent: 10

random-rewards:
  - chance: 0.001
    blocks: # If you want it to work on any block, leave it empty, or don't even add it
      - "diamond_block"
      - "emerald_block"
    items: # Item reward
      - type: stone
        name: "oreo"
    commands: # Command reward
      - "eco give <player> 100000"

# The commands to run when the mine is reset
reset-commands:
  - "say Mine A has been reset!"
```

### Random-rewards:
You can add as many rewards as you want, all the rewards are rolled every time,
meaning you can get more rewards from breaking one block!

* Chance: The chance of the reward
* Blocks: The blocks on which the reward will try to be rolled
* Items: The item rewards
* Commands: The commands that are executed when the reward is given