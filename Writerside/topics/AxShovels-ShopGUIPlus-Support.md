# ShopGUIPlus Support

* Sell blocks or buy them straight from ShopGUIPlus!

### Format:

```yaml
item:
  axshovels: "<type>-<index>"
```
> `type` is the name of the block from the blocks.yml

> Because multiple drops can be configured for each block, `index` is the order of the drop you want, starting with 0. 

### Full example:
```yaml
  items:
    0:
      type: item
      item:
        axshovels: "sand-0"
        quantity: 1
      buyPrice: 1000
      sellPrice: 50
      slot: 0
```