# ShopGUIPlus Support

* Sell ores or buy them straight from ShopGUIPlus!

### Format:

```yaml
item:
  axhoes: "ore-<type>-<index>"
```
> `type` is the name of the ore from the ores.yml

> Because multiple drops can be configured for each ore, `index` is the order of the drop you want, starting with 0. 

### Full example:
```yaml
  items:
    0:
      type: item
      item:
        ores: "ore-diamond-0"
        quantity: 1
      buyPrice: 1000
      sellPrice: 50
      slot: 0
```