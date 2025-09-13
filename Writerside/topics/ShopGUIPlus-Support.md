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

### Full example of all the variations:
```yaml
  items:
    0:
      type: item
      item:
        axspawners: "spawner|sheep|100|5"
        quantity: 2
      buyPrice: 500
      sellPrice: 5
      slot: 0
    1:
      type: item
      item:
        axspawners: "booster|loot-booster|1.5|3m30s"
        quantity: 2
      buyPrice: 500
      sellPrice: 5
      slot: 1
```