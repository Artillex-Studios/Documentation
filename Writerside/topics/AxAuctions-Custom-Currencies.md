# Custom Currencies

```yaml
# you can create your own currencies by using placeholders
# make sure that none of the placeholders have any formatting on them
# requires PlaceholderAPI
placeholder-currencies:
  Example-Currency:
    register: true
    # if the currency uses whole numbers then disable this
    # 100.5 - true
    # 100 - false
    uses-double: true
    # if the placeholder gets parsed even for offline players, enable this
    works-offline: false
    tax: 0
    settings:
      # this placeholder most return a number ONLY, no formatting
      raw-placeholder: '%\vault_eco_balance_fixed%'
      give-command: eco give %\player% %\amount%
      take-command: eco take %\player% %\amount%
    display:
      raw: Money
      gui: '&f%\price% &#AAFFFFmoney'
      item:
        material: EMERALD
        name: '&#00DDFFMoney'
        lore:
        - ' '
        - '&#00DDFF&l(!) &#00DDFFClick here to select!'
```