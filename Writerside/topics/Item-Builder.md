# Item Builder

On this page you can find every item related configuration that is possible to create in our plugins!

Note that you don't need to use all of these values at once, only material is required!

### Example:

```yaml
    material: STICK
    custom-model-data: 100
    glow: true
    lore:
    - "&fthis is a lore,"
    - "&eit can be multiple lines!"
```

### Material:

```yaml
  material: DIAMOND
```
* List of materials: [CLICK](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html)

### Item Name:

```yaml
  name: "<red>Name"
```

### Item Lore:

```yaml
  # you can define as many lines as minecraft allows
  lore:
    - "&cline 1"
    - "&eline 2"
```

### Item Amount:

```yaml
  # amount can be a number between 1 and 64
  # this value may be ignored in some situations
  amount: 1
```

### Glowing Items:

```yaml
  # should the item be enchanted? can be true of false
  glow: true
```

### Unbreakable Items:

```yaml
  # make the item unbreakable
  unbreakable: true
```

### Custom Model Data:

```yaml
  # this value is used to display textured items, can be any integer
  custom-model-data: 1
```

### Enchants:

```yaml
  # you can add as many enchants as you want
  # the format is enchant_name:enchant_level
  enchants:
    - protection:4
```
* List of enchantments: [CLICK](https://www.digminecraft.com/lists/enchantment_list_pc.php) - use the 'Minecraft ID Name' parts

### Item Flags:

```yaml
  # you can add as many item flags as you want
  item-flags:
      - HIDE_ENCHANTS
```
* List of item flags: [CLICK](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html)

### Player Heads:

```yaml
    # the material must be PLAYER_HEAD
    material: PLAYER_HEAD
    # replace base64-here with the base64 of the skull
    texture: "base64-here"
```

### Potions:

```yaml
    # the material must be POTION
    material: POTION
    # this value is RGB separated by commas
    color: "255, 0, 0"
```
* RGB generator: [CLICK](https://htmlcolorcodes.com/color-picker/)

### Leather Armors:

```yaml
    # the material must be a leather armor piece
    material: LEATHER_HELMET
    # this value is RGB separated by commas
    color: "0, 255, 255"
```
* RGB generator: [CLICK](https://htmlcolorcodes.com/color-picker/)

### Tipped Arrows:

```yaml
    # the material must be TIPPED_ARROW
    material: TIPPED_ARROW
    # this value is RGB separated by commas
    color: "255, 255, 0"
```
* RGB generator: [CLICK](https://htmlcolorcodes.com/color-picker/)

## Advanced

### SNBT

1.20.4 and older:
```yaml
    snbt: |-
        {
            DataVersion: 3578,
            Count: 1b,
            id: "minecraft:turtle_helmet",
            tag: {
                Damage: 0,
                axboosters-item: "flying-helmet",
                display: {
                    Lore: [],
                    Name: '{"italic":false,"extra":[{"bold":true,"color":"#0099FF","text":"F"},{"bold":true,"color":"#009CFF","text":"l"},{"bold":true,"color":"#009FFF","text":"y"},{"bold":true,"color":"#00A2FF","text":"i"},{"bold":true,"color":"#00A4FF","text":"n"},{"bold":true,"color":"#00A7FF","text":"g"},{"bold":true,"color":"#00AAFF","text":" "},{"bold":true,"color":"#00ADFF","text":"h"},{"bold":true,"color":"#00B0FF","text":"e"},{"bold":true,"color":"#00B3FF","text":"l"},{"bold":true,"color":"#00B5FF","text":"m"},{"bold":true,"color":"#00B8FF","text":"e"},{"bold":true,"color":"#00BBFF","text":"t"}],"text":""}'
                }
            }
        }
```
1.20.5 and newer:
```yaml
    snbt: |-
        {
           DataVersion: 3955,
           components: {
               "minecraft:custom_data": {
                   axboosters-item: "flying-helmet"
               },
               "minecraft:custom_name": '{"extra":[{"bold":true,"color":"#0099FF","text":"F"},{"bold":true,"color":"#009CFF","text":"l"},{"bold":true,"color":"#009FFF","text":"y"},{"bold":true,"color":"#00A2FF","text":"i"},{"bold":true,"color":"#00A4FF","text":"n"},{"bold":true,"color":"#00A7FF","text":"g"},{"bold":true,"color":"#00AAFF","text":" "},{"bold":true,"color":"#00ADFF","text":"h"},{"bold":true,"color":"#00B0FF","text":"e"},{"bold":true,"color":"#00B3FF","text":"l"},{"bold":true,"color":"#00B5FF","text":"m"},{"bold":true,"color":"#00B8FF","text":"e"},{"bold":true,"color":"#00BBFF","text":"t"}],"italic":false,"text":""}',
               "minecraft:enchantment_glint_override": 1b
           },
           count: 1,
           id: "minecraft:turtle_helmet"
        }
```
* SNBT is the best format to use for complex (custom) items, it can store all nbt that minecraft supports, however, it is much more complicated than our item builder.