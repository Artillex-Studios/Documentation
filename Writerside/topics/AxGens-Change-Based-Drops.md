# Chance-Based Drops

### Normal single drop:
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[drop-item:
      # the sell price only works if hooks.price-plugin is set to "builtin"
      sell-price: 50.0
      # you can customize the item, you can even remove its lore/name
      material: WHEAT
      name: "&#FFCC00&lWHEAT"
      lore:
        - ""
        - " &7- &fSell price: &#33FF33%sell-price%$"
        - ""]]>
</code-block>

### Chance-based multi-drops:
- The chances don't have to add up to 100%
- You can add as many as you wish
- Currently, ONLY the first item is used in placeholders, but ofc you don't have to use placeholders like %\drop-name% and %\drop-material%
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[drop-item:
      # chances don't have to add up to 100%
      - chance: 90.0
        # the sell price only works if hooks.price-plugin is set to "builtin"
        sell-price: 50.0
        # you can customize the item, you can even remove its lore/name
        material: WHEAT
        name: "&#FFCC00&lWHEAT"
        lore:
          - ""
          - " &7- &fSell price: &#33FF33%sell-price%$"
          - ""
      - chance: 10.0
        sell-price: 100.0
        material: HAY_BLOCK
        name: "&#FFCC00&lHAY BALE"
        lore:
          - ""
          - " &7- &fSell price: &#33FF33%sell-price%$"
          - ""]]>
</code-block>