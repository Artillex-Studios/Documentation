# Configuration

<procedure title="config.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[prefix: "&#00DDFF&lAxAuctions &7» "

    database:
      # h2, mysql, postgresql
      type: "h2"
      prefix: "axauctions"

      # you only need to touch these when using mysql/postgresql
      address: 127.0.0.1
      port: 3306
      database: admin
      username: admin
      password: 'admin'
      pool:
        maximum-pool-size: 10
        minimum-idle: 10
        maximum-lifetime: 1800000
        keepalive-time: 0
        connection-timeout: 5000

    # format: language_COUNTRY
    # after changing this, the server will download the default item names
    language: en_US

    # when using mysql/postgresql, how should data be sent between servers?
    # values: none, sql
    # if you don't need multi server support, set to none to disable
    multi-server-support: "sql"

    # should sellers get their money only when they join?
    # with some currency plugins this option is automatically enabled
    # the sellers will still be notified about sold items even if this is false
    # if you change this while the plugin is used, some players may get their money twice or lose their money
    only-give-money-on-join: false

    # https://docs.oracle.com/javase/tutorial/i18n/format/decimalFormat.html
    # how money should be formatted?
    number-format: "#,###.##"

    # used to show the length of boosters
    # in bossbars you have to use the %time_formatted% placeholder for these to be used
    # 1 - HH:MM:SS, for example 01:25:35
    # 2 - short format, for example 20m
    # 3 - text format, for example 01h 25m 35s
    timer-format: 1

    # after how long should items expire?
    # in seconds
    item-expire-time: 86400

    # after how long should items get deleted?
    # only starts if the item have expired
    # in seconds
    item-deletion-time: 604800

    # the minimum price for an item
    # do not set below 0.01
    min-price: 10.0

    # the maximum price for an item
    # set to -1 to disable
    max-price: -1

    # if true, even if there is only 1 loaded currency, the selector will show
    force-currency-selector: false

    # list of items that CAN'T be sold in the auction house
    # note: the name-contains string shouldn't include any color codes
    blacklisted-items:
      "1":
        material: "barrier"
        name-contains: "Banned item's name"

    # do not change this
    version: 3]]>
</code-block></step>
</procedure>

<procedure title="discord.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[# These are all the options that you can use in the webhook section: (most of them are optional, you can remove them)
    #    # the message before the embed, you can put a ping here in the <@&1234567890123456789> format
    #    content: "<@&1234567890123456789>"
    #    # color in hex
    #    color: "#FF6600"
    #    description: "Your description"
    #    title:
    #      # required
    #      text: "Title!"
    #      icon: ""
    #    author:
    #      # required
    #      name: "Author name"
    #      icon-url: ""
    #      url: ""
    #    footer:
    #      # required
    #      text: "Footer"
    #      icon: ""
    #    image-url: ""
    #    thumbnail-url: ""
    #    fields:
    #      1:
    #        # required
    #        inline: false
    #        # required
    #        name: "Field1"
    #        # required
    #        value: "Value1"

    # REQUIRED
    url: ""
    
    auction-start:
    enabled: true
    color: "#00DDFF"
    title:
    text: "New Auction"
    fields:
    "1":
    inline: false
    name: Seller
    value: "%player%"
    "2":
    inline: false
    name: Item
    value: "%amount%x %item%"
    "3":
    inline: false
    name: Price
    value: "%price%"
    
    auction-buy:
    enabled: true
    color: "#00DDFF"
    title:
    text: "Item Purchased"
    fields:
    "1":
    inline: true
    name: Buyer
    value: "%player%"
    "2":
    inline: true
    name: Seller
    value: "%seller%"
    "3":
    inline: false
    name: Item
    value: "%amount%x %item%"
    "4":
    inline: true
    name: Price
    value: "%price%"
    
    # do not change this
    version: 1]]>
</code-block></step>
</procedure>

<procedure title="currencies.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[currencies:
      Level:
        register: true
        display:
          raw: "Level"
          gui: "&f%price% &#AAFFFFlevels"
          item:
            material: EXPERIENCE_BOTTLE
            name: "&#00DDFFLevel"
            lore:
              - " "
              - "&#00DDFF&l(!) &#00DDFFClick here to select!"
      Vault:
        register: true
        display:
          # the way the currency will be shown in the lores of the auction gui
          gui: "&f%price% &#AAFFFFcoins"
          # used in the currency switcher and tab completion
          raw: "Vault"
          # the item shown in the currency selector
          item:
            material: GOLD_INGOT
            name: "&#00DDFFVault"
            lore:
              - " "
              - "&#00DDFF&l(!) &#00DDFFClick here to select!"
      PlayerPoints:
        register: true
        display:
          raw: "PlayerPoints"
          gui: "&f%price% &#AAFFFFpoints"
          item:
            material: GOLD_INGOT
            name: "&#00DDFFPlayerPoints"
            lore:
              - " "
              - "&#00DDFF&l(!) &#00DDFFClick here to select!"
      RoyaleEconomy:
        register: true
        display:
          raw: "RoyaleEconomy"
          gui: "&f%price% &#AAFFFFcoins"
          item:
            material: GOLD_INGOT
            name: "&#00DDFFRoyaleEconomy"
            lore:
              - " "
              - "&#00DDFF&l(!) &#00DDFFClick here to select!"
      CoinsEngine:
        register: true
        # the name of the currency to use
        currency-name: "coins"
        display:
          raw: "CoinsEngine"
          gui: "&f%price% &#AAFFFFcoins"
          item:
            material: GOLD_INGOT
            name: "&#00DDFFCoinsEngine"
            lore:
              - " "
              - "&#00DDFF&l(!) &#00DDFFClick here to select!"
      UltraEconomy:
        register: true
        # the name of the currency to use
        currency-name: "coins"
        display:
          raw: "UltraEconomy"
          gui: "&f%price% &#AAFFFFcoins"
          item:
            material: GOLD_INGOT
            name: "&#00DDFFUltraEconomy"
            lore:
              - " "
              - "&#00DDFF&l(!) &#00DDFFClick here to select!"
      KingdomsX:
        register: true
        # the name of the currency to use
        currency-name: "nexus points"
        display:
          raw: "KingdomsX"
          gui: "&f%price% &#AAFFFFnexus points"
          item:
            material: GOLD_INGOT
            name: "&#00DDFFKingdomsX"
            lore:
              - " "
              - "&#00DDFF&l(!) &#00DDFFClick here to select!"
    
    # do not change this
    version: 1]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[help:
      - " "
      - "&#00DDFF&lAxAuctions Help &7»"
      - " &7- &f/ah &7| &#00DDFFOpen auction menu"
      - " &7- &f/ah view &7| &#00DDFFView your auctions"
      - " &7- &f/ah view [player] &7| &#00DDFFView auctions of a player"
      - " &7- &f/ah sell <price> [amount] [currency] &7| &#00DDFFSell item"
      - " &7- &f/ah search [text] &7| &#00DDFFSearch for items by type/name/lore"
      - " &7- &f/ah history &7| &#00DDFFCheck sell and buy history"
      - " "
    
    admin-help:
    - " "
      - "&#00DDFF&lAxAuctions Admin Help &7»"
      - " &7- &f/ahadmin reload &7| &#00DDFFReload plugin"
      - " &7- &f/ahadmin history <player> &7| &#00DDFFOpen history GUI"
      - " &7- &f/ahadmin limit give/set/take/reset <player> <amount> &7| &#00DDFFIncreate limit of player"
      - " &7- &f/ahadmin convert <plugin> &7| &#00DDFFConvert from another plugin"
      - " "
    
    reload:
    success: "&#33FF33Plugin successfully reloaded!"
    failed: "&#FF3333Failed to reload the plugin! Something is wrong in the &f%file%&#FF3333 file, look in the console or use a yaml validator to fix the errors!"
    
    item-lore:
    - "%lore%"
      - " "
      - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
      - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
      - " &#999999» &#00DDFFSeller: &#AAFFFF%seller%"
      - " &#999999» &#00DDFFExpires: &#AAFFFF%expires%"
      - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFPurchase Item"
    
    item-lore-own:
    - "%lore%"
      - " "
      - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
      - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
      - " &#999999» &#00DDFFExpires: &#AAFFFF%expires%"
      - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFCancel Auction"
    
    history-item-lore:
    - "%lore%"
      - " "
      - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
      - " &#999999» &#00DDFFSeller: &#AAFFFF%seller%"
      - " &#999999» &#00DDFFBuyer: &#AAFFFF%buyer%"
      - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
      - " &#999999» &#00DDFFSold Time: &#AAFFFF%time%"
      - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
    
    sell:
    limit-reached: "&#FF0000You have reached the auction limit! &7(%current%/%limit%)"
    no-item: "&#FF0000Hold something in your hand to sell it!"
    price-too-low: "&#FF0000The price you have set is below the minimum of &f%amount%&#FF0000!"
    price-too-high: "&#FF0000The price you have set is above the maximum of &f%amount%&#FF0000!"
    success: "&#33FF33You have successfully put &f%amount% &#33FF33items on the auction house for &f%price%&#33FF33!"
    # set to "" to disable
    action-bar-broadcast: "&#00DDFF%player% &fhas started selling &#00DDFF%amount% &fof &#00DDFF%item% &ffor &#00DDFF%price%&f! &#DDDDDD/ah"
    
    buy:
    not-enough-money: "&#FF0000You can't afford this item!"
    item-not-found: "&#FF0000The item is not found! Somebody must have bought it or the seller cancelled it!"
    inventory-full: "&#FF0000Your inventory is full!"
    success: "&#33FF33You have purchased &f%amount%x %item% &#33FF33from the auction house for &f%price%&#33FF33!"
    notify-seller: "&#00DDFF%player% &fhave purchased your &#00DDFF%amount%x &#00DDFF%item% &ffor &#00DDFF%price% &ffrom the auction house!"
    # set to "" to disable
    action-bar-purchase: "&#00DDFF%player% &fhas purchased &#00DDFF%amount% &fof &#00DDFF%item% &ffrom &#00DDFF%seller% &ffor &#00DDFF%price%&f! &#DDDDDD/ah"
    
    admin-action:
    cancelled: "&#00DDFF%staff% &fhas cancelled your &#00DDFF%amount%x &#00DDFF%item% &fin the auction house at &#00DDFF%date%&f!"
    removed: "&#00DDFF%staff% &fhas removed your &#00DDFF%amount%x &#00DDFF%item% &ffrom the auction house at &#00DDFF%date%&f!"
    cancelled-info: "&#FF3333You have successfully cancelled the item in the auction house!"
    removed-info: "&#FF3333You have successfully removed the item from the auction house!"
    
    my-items:
    removed: "&#FF0000You have successfully removed the item from the auction house!"
    
    limit-changed: "&#33FF33You have changed &f%player%&#33FF33's limit to &f%amount%&#33FF33!"
    date-format: "yyyy. MM. dd HH:mm:ss"
    limit-bypass-icon: "∞"
    expired: "Expired"
    blacklisted: "&#FF0000This item is blacklisted!"
    converting: "&#33FF33Started converter, check the console for more information!"
    
    # do not change this
    version: 1]]>
</code-block></step>
</procedure>

*There are many GUI configs, here is the most complex one:*
<procedure title="guis/main-gui.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[title: "&0Auction House (%current_page%/%max_page%)"
    # a gui can only have 1-6 rows
    rows: 6
    # how many item should be shown on a single page?
    page-size: 54
    
    # ----- ITEMS -----
    
    my-items:
    slot: 45
    material: "ENDER_CHEST"
    name: "&#00DDFF&lᴍʏ ɪᴛᴇᴍs"
    lore:
    - " "
      - " &fClick here to go"
      - " &fto the my items page!"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFMy Items Page"
    # list of sounds: https://www.digminecraft.com/lists/sound_list_pc.php
    # the sound played when clicking this item
    # set to "" to disable
    sound: "ui.button.click"
    
    sorting:
    slot: 46
    # only the active item will be shown
    newest:
    material: "GLOWSTONE_DUST"
    name: "&#00DDFF&lsᴏʀᴛɪɴɢ"
    lore:
    - " "
      - " &#00DDFFCurrently selected:"
      - "  &#444444❙ &#AAFFAANewest to oldest"
      - "  &#444444❙ &#BBBBBBOldest to newest"
      - "  &#444444❙ &#BBBBBBCheapest to priciest"
      - "  &#444444❙ &#BBBBBBPriciest to cheapest"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Sorting"
      oldest:
      material: "REDSTONE"
      name: "&#00DDFF&lsᴏʀᴛɪɴɢ"
      lore:
      - " "
      - " &#00DDFFCurrently selected:"
      - "  &#444444❙ &#BBBBBBNewest to oldest"
      - "  &#444444❙ &#AAFFAAOldest to newest"
      - "  &#444444❙ &#BBBBBBCheapest to priciest"
      - "  &#444444❙ &#BBBBBBPriciest to cheapest"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Sorting"
      cheapest:
      material: "GLOWSTONE_DUST"
      name: "&#00DDFF&lsᴏʀᴛɪɴɢ"
      lore:
      - " "
      - " &#00DDFFCurrently selected:"
      - "  &#444444❙ &#BBBBBBNewest to oldest"
      - "  &#444444❙ &#BBBBBBOldest to newest"
      - "  &#444444❙ &#AAFFAACheapest to priciest"
      - "  &#444444❙ &#BBBBBBPriciest to cheapest"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Sorting"
      priciest:
      material: "REDSTONE"
      name: "&#00DDFF&lsᴏʀᴛɪɴɢ"
      lore:
      - " "
      - " &#00DDFFCurrently selected:"
      - "  &#444444❙ &#BBBBBBNewest to oldest"
      - "  &#444444❙ &#BBBBBBOldest to newest"
      - "  &#444444❙ &#BBBBBBCheapest to priciest"
      - "  &#444444❙ &#AAFFAAPriciest to cheapest"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Sorting"
      sound: "ui.button.click"
    
    previous-page:
    slot: 48
    material: "ARROW"
    name: "&#00DDFF&lᴘʀᴇᴠɪᴏᴜs ᴘᴀɢᴇ"
    lore:
    - " "
      - " &fClick here to go back"
      - " &fto the previous page!"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFPrevious Page"
      sound: "ui.button.click"
    
    refresh:
    slot: 49
    material: "SUNFLOWER"
    name: "&#00DDFF&lʀᴇғʀᴇsʜ"
    lore:
    - " "
      - " &fClick here to"
      - " &frefresh the page!"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFRefresh Page"
      sound: "ui.button.click"
    
    next-page:
    slot: 50
    material: "ARROW"
    name: "&#00DDFF&lɴᴇxᴛ ᴘᴀɢᴇ"
    lore:
    - " "
      - " &fClick here to go"
      - " &fto the next page!"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFNext Page"
      sound: "ui.button.click"
    
    currency:
    slot: 52
    material: "HOPPER"
    name: "&#00DDFF&lᴄᴜʀʀᴇɴᴄʏ"
    lore:
    - " "
      - " &#00DDFFCurrently selected:"
      - "  &#444444❙ &#AAFFAA%selected_currency%"
      - " "
      - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Currency"
    # used for the %selected_currency% when none is selected
    no-currency: "All"
    sound: "ui.button.click"
    
    information:
    slot: 53
    material: "BOOK"
    name: "&#00DDFF&lɪɴғᴏʀᴍᴀᴛɪᴏɴ"
    lore:
    - " "
      - " &fIn this menu, you can"
      - " &fsell or buy items!"
      - " "
      - "&#AADDFFYou are selling &f%sell_count%/%sell_limit% &#AADDFFitems!"
      - " "
      - "&#00DDFF&lSell Items &#DDDDDD» &#AAFFFF/ah sell"]]>
</code-block></step>
</procedure>