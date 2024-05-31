# Multi Currency Plugins

* If a plugin supports multiple currencies, you can use the following format to add multiple currencies to the trade gui:

First of all, make sure to enable all the currencies that you want, for example here the `coins` and `money` currency is enabled.
> The currency-name section refers to the internal name of the currency in your currency handler plugin!
> 
> The name section is used in the trade summary message, that can be set to anything that you would like!
{style="warning"}

Example CoinsEngine setup in the `currencies.yml`:
```yaml
currencies:
  CoinsEngine:
    register: true
    enabled:
      - currency-name: "coins"
        name: "special coin"
      - currency-name: "money"
        name: "special money"
```

After that you will also have to add it to the `guis.yml`,
first let's add both to the `own` section, this is how it will look like:

<code-block lang="yaml" ignore-vars="true" collapsible="false" show-white-spaces="true">
<![CDATA[
own:
  coinsengine-example-1:
    slot: 2
    currency: "CoinsEngine-coins"
    material: "GOLD_NUGGET"
    name: "&#00ffdd&lCoinsEngine Coins"
    lore:
      - "&7Your offer"
      - ""
      - " &7- &fAmount: &#00ffdd%amount%$"
      - ""
      - "&#00ffdd&l> &#00ffddClick &8- &#00ffddChange Amount"
  coinsengine-example-2:
    slot: 3
    currency: "CoinsEngine-money"
    material: "GOLD_NUGGET"
    name: "&#00ffdd&lCoinsEngine Money"
    lore:
      - "&7Your offer"
      - ""
      - " &7- &fAmount: &#00ffdd%amount%$"
      - ""
      - "&#00ffdd&l> &#00ffddClick &8- &#00ffddChange Amount"
]]>
</code-block>

If this is done, scroll a bit to the `partner` section and do almost the same thing once again:

<code-block lang="yaml" ignore-vars="true" collapsible="false" show-white-spaces="true">
    <![CDATA[
partner:
  coinsengine-example-1:
    slot: 6
    currency: "CoinsEngine-coins"
    material: "GOLD_NUGGET"
    name: "&#00ffdd&lCoinsEngine Coins"
    lore:
      - "&7%player%'s offer"
      - ""
      - " &7- &fAmount: &#00ffdd%amount%$"
      - ""
      - "&#00ffdd&l> &#00ffddClick &8- &#00ffddChange Amount"
  coinsengine-example-2:
    slot: 5
    currency: "CoinsEngine-money"
    material: "GOLD_NUGGET"
    name: "&#00ffdd&lCoinsEngine Money"
    lore:
      - "&7%player%'s offer"
      - ""
      - " &7- &fAmount: &#00ffdd%amount% EXP"
      - ""
      - "&#00ffdd&l> &#00ffddClick &8- &#00ffddChange Amount"
]]>
</code-block>