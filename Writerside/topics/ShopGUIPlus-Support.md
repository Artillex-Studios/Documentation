# ShopGUIPlus Support

* Sell spawners and boosters or buy them straight from ShopGUIPlus!

### Format:

**Spawners:**
```yaml
item:
  axspawners: "spawner|<name>|<stack size>|<level>"
```

**Boosters:**
```yaml
item:
  axspawners: "booster|<name>|<multiplier>|<length>"
```

**Wands:**
```yaml
item:
  axspawners: "wand|<name>|<multiplier>|<radius>|<uses>"

# unlimited uses
item:
  axspawners: "wand|<name>|<multiplier>|<radius>"
```

### Full example of all the variations:
```yaml
  items:
    0:
      type: item
      item:
        axspawners: "spawner|sheep|100|5"
        quantity: 1
      buyPrice: 5000
      sellPrice: 500
      slot: 0
    1:
      type: item
      item:
        axspawners: "booster|loot-booster|1.5|3m30s"
        quantity: 1
      buyPrice: 1000
      sellPrice: 50
      slot: 1
    2:
      type: item
      item:
        axspawners: "wand|sell-wand|1.5|5|100"
        quantity: 1
      buyPrice: 2500
      sellPrice: 150
      slot: 2
```