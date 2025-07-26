# Crate

Crates are what actually spawn in envoys, so you need to configure them accordingly!

```yaml

# This crate needs to be clicked 50 times to get the loot
# so this is a sort of miniboss, I guess!

# Cooldown in seconds until a player can collect a new crate of this type
# THIS OVERRIDES THE SAME SETTING IN THE ENVOY'S CATEGORY! If you do NOT want to override it, remove it from here
collect-cooldown: 10
broadcast-collect: true

display-name: "&cCommon"
block: iron_block

required-interactions:
  amount: 50
  cooldown: 0 # In ticks. 1 second is 20 ticks! Set to 0 to disable!

falling-block:
  enabled: false # If a falling block should be spawned where a crate is spawned
  height: 10 # The height where the falling block will fall from
  block: end_rod # The type of the block that is falling
  speed: -1 # The speed at which the block will fall (blocks per second)

firework:
  enabled: true
  color: #ff0000
  type: ball

flare:
  enabled: true
  every: 200 # ticks, 20 ticks is 1 second
  firework:
    color: #ff0000
    type: ball

rewards:
  - chance: 10.0
    messages:
      - "&7Wow!"
    commands:
      - "eco give %\player% 1000"
  - chance: 30.0
    commands:
      - "eco give %\player% 500"
  - chance: 100.0
    commands:
      - "eco give %\player% 50"

hologram:
  enabled: true
  height: 2.0
  lines:
    - "&7Envoy!"
    - "&fRarity: &acommon."
    - ""
    - "Hits: %\hits%/%\max_hits%"


```

# Explanation

## collect-cooldown
That's the cooldown until a player can collect a crate of that type again

## broadcast-collect
Whether or not the collection of this crate should be broadcasted

## block
The type of the block that you'd like the spawned crate to have. You can use ItemsAdder or Oraxen 
materials here! For Oraxen: `oraxen:&lt;block_id>`, and for ItemsAdder: `itemsadder:&lt;block_id>`

## required-interactions
The amount of times the crate has to be clicked to be collected. If the player attempting to collect it is
on a cooldown, the crate won't be able to be collected

## rewards
 ### chance
  The chance for this reward. This is relative, so the chances don't have to add up to 100
 ### messages
  The messages that will be sent to use to the player. Can use formatting
 ### commands
  The commands that will be ran. You can use PlaceholderAPI placeholders here
 ### items
  The items that will be given to the player. They follow the same scheme as the other items in the plugin