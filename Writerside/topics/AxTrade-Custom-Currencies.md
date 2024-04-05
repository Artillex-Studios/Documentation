# Custom Currencies

```yaml
# you can create your own currencies by using placeholders
# make sure that none of the placeholders have any formatting on them
# requires PlaceholderAPI
placeholder-currencies:
  Example-Currency:
    register: true # < MAKE SURE TO TURN THIS ON
    name: "money"
    # if the currency uses whole numbers, then disable this
    # 100.5 - true
    # 100 - false
    uses-double: true
    # if the placeholder gets parsed even for offline players, enable this
    works-offline: false
    settings:
      raw-placeholder: "%\vault_eco_balance_fixed%"
      give-command: "eco give %\player% %\amount%"
      take-command: "eco take %\player% %\amount%"
```

### Adding them to the gui
* Make sure to add it to both the `own` and `partner` section and change the slot!
```yaml
  currency-example1:
    slot: 1
    currency: "Example-Currency" # < THIS IS THE IMPORTANT PART
    material: "GOLD_NUGGET"
    name: "&#00ffdd&lᴍᴏɴᴇʏ"
    lore:
      - "&7Your offer"
      - ""
      - " &7- &fAmount: &#00ffdd%\amount%$"
      - ""
      - "&#00ffdd&l> &#00ffddClick &8- &#00ffddChange Amount"
```