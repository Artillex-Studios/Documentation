# ShopGUIPlus Support

* Sell crops or buy them straight from ShopGUIPlus!

### Format:

```yaml
item:
  axhoes: "<type>-<index>"
```
> `type` is the name of the crop from the crops.yml

> Because multiple drops can be configured for each crop, `index` is the order of the drop you want, starting with 0. 

### Full example:
```yaml
  items:
    0:
      type: item
      item:
        axhoes: "wheat-0"
        quantity: 1
      buyPrice: 1000
      sellPrice: 50
      slot: 0
```