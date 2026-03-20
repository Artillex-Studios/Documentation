# ShopGUIPlus Support

* Sell chests and boosters or buy them straight from ShopGUIPlus!

### Format:

**Sell chests:**
```yaml
item:
  axsellchests: "chest|<name>"
```

**Boosters:**
```yaml
item:
  axsellchests: "booster|<name>|<multiplier>|<length>"
```

### Full example of all the variations:
```yaml
  items:
    0:
      type: item
      item:
        axsellchests: "chest|basic"
        quantity: 1
      buyPrice: 5000
      sellPrice: 500
      slot: 0
    1:
      type: item
      item:
        axsellchests: "booster|money-booster|1.5|5m30s"
        quantity: 1
      buyPrice: 1000
      sellPrice: 50
      slot: 1
```