# Multi Currency Plugins

* If a plugin supports multiple currencies, you can allow multiple currencies to be used in AxAuctions.

Example CoinsEngine setup with 2 currencies in the `currencies.yml`:

We have 2 currencies set up in CoinsEngine:

![image_52.png](image_52.png)

And in The AxAuctions currencies.yml, this is how the 2 currencies are set up:
```yaml
currencies:
  CoinsEngine:
  register: true
  # CoinsEngine supports multiple currencies, so you can also add multiple here
  # "coins" is the name of the currency
  # first currency
  coins:
    tax: 0
    display:
      raw: "CoinsEngine-coins"
      gui: "&f%\price% &#AAFFFFcoins"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFCoinsEngine coins"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  # second currency
  money:
    tax: 0
    display:
      raw: "CoinsEngine-money"
      gui: "&f%\price% &#AAFFFFmoney"
      item:
        material: GOLD_NUGGET
        name: "&#00DDFFCoinsEngine money"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
```

You can register any amount of custom currencies if the plugin supports it.