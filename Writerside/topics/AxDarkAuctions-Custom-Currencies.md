# Custom Currencies

```yaml
# you can create your own currencies by using placeholders
# make sure that none of the placeholders have any formatting on them
# requires PlaceholderAPI
placeholder-currencies:
  Example-Currency:
    register: false
    name: "money"
    # if the currency uses whole numbers, then disable this
    # 100.5 - true
    # 100 - false
    uses-double: true
    # if the placeholder gets parsed even for offline players, enable this
    works-offline: false
    settings:
      raw-placeholder: "%\vault_eco_balance_fixed%"
      give-command: "eco give %\player% %\price%"
      take-command: "eco take %\player% %\price%"
```