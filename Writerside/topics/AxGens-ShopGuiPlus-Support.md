# ShopGUIPlus Support

* Sell generators and drops or buy them straight from ShopGUIPlus!

### Format:

**Generators:**
```yaml
item:
  axgens: "generator-<TIER>"
```

**Drops: (first/single)**
```yaml
item:
  axgens: "drop-<TIER>"
```

**Drops: (if you use multiple drops, index is a number, starting from 0)**
```yaml
item:
  axgens: "drop-<TIER>-<INDEX>"
```

### Full example of all the variations:
```yaml
  items:
    0:
      type: item
      item:
        axgens: "generator-5" # tier 5 generator
        quantity: 1
      buyPrice: 50
      sellPrice: 5
      slot: 0
    1:
      type: item
      item:
        axgens: "drop-6" # tier 6 drop
        quantity: 1
      buyPrice: 50
      sellPrice: 5
      slot: 1
    2:
      type: item
      item:
        axgens: "drop-1-0" # the first tier 1 drop
        quantity: 1
      buyPrice: 50
      sellPrice: 5
      slot: 2
    3:
      type: item
      item:
        axgens: "drop-1-1" # the second tier 1 drop
        quantity: 1
      buyPrice: 50
      sellPrice: 5
      slot: 3
```