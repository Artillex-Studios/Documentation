# Enchant Types

| Name            | Parameters                                                                   | Description                                          |
|-----------------|------------------------------------------------------------------------------|------------------------------------------------------|
| auto_sell       | only-sell-drops (true or false)<br/>multiplier ([calculation](#calculation)) | Sells all sellable items from the player's inventory |
| boost_player_xp | multiplier ([calculation](#calculation))                                     | Increases gained player XP                           |
| boost_tool_xp   | multiplier ([calculation](#calculation))                                     | Increases gained tool XP                             |
| boost_essence   | multiplier ([calculation](#calculation))                                     | Increases gained essence                             |
| boost_money     | multiplier ([calculation](#calculation))                                     | Increases gained money                               |
| boost_drops     | multiplier ([calculation](#calculation))                                     | Increases gained drops                               |
| give_player_xp  | amount ([calculation](#calculation))                                         | Gives a random amount of player XP                   |
| give_tool_xp    | amount ([calculation](#calculation))                                         | Gives a random amount of tool XP                     |
| give_money      | amount ([calculation](#calculation))                                         | Gives a random amount of money                       |
| give_essence    | amount ([calculation](#calculation))                                         | Gives a random amount of essence                     |
| give_drops      | amount ([calculation](#calculation))                                         | Gives a random amount of drops                       |
| execute_command | [command](#command)                                                          | Runs a console command                               |
| give_item       | [give](#give)                                                                | Gives item to the player                             |
| give_effect     | [effect](#effect)                                                            | Applies a potion effect to the player                |
| enchant_tool    | [enchant](#enchant)                                                          | Applies a minecraft enchantment to the player's tool |
| break_area      | area ([calculation](#calculation))                                           | Breaks all collectable blocks within an area         |
| explode_area    | strength ([calculation](#calculation))                                       | Explodes all collectable blocks within an area       |

## Base parameters
```yaml
name: "Enchant name %\level%"
# what type of enchantment is this? check the wiki for the list
type: "enchant type"
# the enchant's max possible level
max-level: 10
# optional, required levels to be able to upgrade this enchant
required-player-level: 0
required-tool-level: 0
# optional, what permission is required to upgrade this enchant?
required-permission: ""
# should the enchant get reset when the tool is prestiged?
reset-on-prestige: true

# the amount of essence required to upgrade the enchantment
price:
  # TYPES
  # - formula (uses the given formula)
  # - manual (set every level manually)
  # note: levels start from 0
  type: "formula"
  formula: "%\level% ^ 2 * 1000 + 100"
  manual:
    1: "100"
    2: "500"
    3: "1500"
    4: "5000"

# chance for this enchantment to trigger when a collectable is broken (0-100%)
chance:
  # TYPES
  # - formula (uses the given formula)
  # - manual (set every level manually)
  # note: levels start from 1
  type: "formula"
  formula: "%\level% * 2"
  manual:
    1: "2"
    2: "5"
    3: "8"
    4: "12"
```

## Enchant specific parameters

### Calculation
```yaml
<name>:
  # TYPES
  # - formula (uses the given formula)
  # - manual (set every level manually)
  # note: levels start from 1
  type: "formula"
  formula: "%\level% * 2"
  manual:
    1: "2"
    2: "4"
    3: "6"
```

### Command
> The %\player% placeholder will be replaced with the player's name. 
```yaml
# levelling up changes the rewards given
command:
  1:
    - "give %\player% COAL 1"
  5:
    - "give %\player% IRON_INGOT 1"
  10:
    - "give %\player% DIAMOND 1"
```

### Give
> You can use all [ItemBuilder](Item-Builder.md) options here!
```yaml
# levelling up changes the rewards given
give:
  1:
    - material: COAL
  5:
    - material: IRON_INGOT
  10:
    - material: DIAMOND
```

### Effect
```yaml
# levelling up changes the effects given
# list of potion effect types: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html
# format: <type>:<strength starting at 1>:<time in seconds>
effect:
  1:
    - "HASTE:1:5"
  25:
    - "HASTE:2:5"
  50:
    - "HASTE:3:5"
  75:
    - "HASTE:4:5"
  100:
    - "HASTE:5:5"
```

### Enchant
```yaml
# levelling up changes the enchantments applied
# list of enchantments: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/enchantments/Enchantment.html
# format: <type>:<level>
enchant:
  1:
    - "FORTUNE:1"
  2:
    - "FORTUNE:2"
  3:
    - "FORTUNE:3"
```