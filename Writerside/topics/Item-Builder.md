# Item Builder

On this page you can find every item related configuration that is possible to create in our plugins!

Note that you don't need to use all of these values at once, only material is required!

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
    # this value is RGB separated by colons
    color: "255, 0, 0"
```
* RGB generator: [CLICK](https://htmlcolorcodes.com/color-picker/)

### Leather Armors:

```yaml
    # the material must be a leather armor piece
    material: LEATHER_HELMET
    # this value is RGB separated by colons
    color: "0, 255, 255"
```
* RGB generator: [CLICK](https://htmlcolorcodes.com/color-picker/)

### Tipped Arrows:

```yaml
    # the material must be TIPPED_ARROW
    material: TIPPED_ARROW
    # this value is RGB separated by colons
    color: "255, 255, 0"
```
* RGB generator: [CLICK](https://htmlcolorcodes.com/color-picker/)