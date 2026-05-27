# Configuration

### Directory Structure
<code-block lang="text">
AxAuctions/
├── guis/
│   ├── admin-removal-gui.yml
│   ├── category-gui.yml
│   ├── confirm-purchase-gui.yml
│   ├── currency-selector-gui.yml
│   ├── deleted-gui.yml
│   ├── expired-items-gui.yml
│   ├── history-gui.yml
│   ├── logs-gui.yml
│   ├── main-gui.yml
│   ├── my-items-gui.yml
│   └── shulker-preview-gui.yml
├── categories.yml
├── config.yml
├── currencies.yml
├── discord.yml
└── lang.yml
</code-block>

### Default Contents
<procedure title="categories.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html
#
# some supported regex: (optional)
# - 'name' #  only 'name' is disallowed
# - 'name*' #  disallows text starting with 'name'
# - '*name' #  disallows text ending with 'name'
# - '*name*' #  disallows text containing 'name'
#
# you can use some sections from our item builder: (https://docs.artillex-studios.com/item-builder.html)
#  > name
#  > material / type
#  > custom-model-data (only the old variant)
#
# note: category items are always matched with the "OR" logic gate, which means that if any of the "items" sections match the item, it will be part of the category
#
# you should not include color codes as the plugin removes them before checking for matches,
# instead you should put names like this: "name: '*Name*'" meaning that if the item name contains the name, it will match it
# and of course, every field is case-sensitive!

# should the category system be enabled?
# note: the category selector item is disabled by default, you need to uncomment the section as well (in the main-gui.yml and my-items.yml) to make it work!
enabled: false

# the "all" category just matches all materials
all:
  # formatted name of the category, can contain colors
  name: "All"
  items:
    - material: "*"

tools:
  name: "Tools"
  items:
    - material: "*_PICKAXE" # match items with their material ending in _PICKAXE
    - material: "*_AXE"
    - material: "*_SHOVEL"
    - material: "*_HOE"

weapons:
  name: "Weapons"
  items:
    - material: "*_SWORD"
    - material: "*_AXE"
    - material: "SHIELD"
    - material: "TRIDENT"
    - material: "*BOW"
    - material: "*ARROW"

armors:
  name: "Armors"
  items:
    - material: "*_HELMET"
    - material: "*_CHESTPLATE"
    - material: "*_LEGGINGS"
    - material: "*_BOOTS"

minerals:
  name: "Minerals"
  items:
    - material: "*_ORE"
    - material: "*_INGOT"
    - material: "DIAMOND"
    - material: "EMERALD"
    - material: "COAL"
    - material: "QUARTZ"
    - material: "REDSTONE"
    - material: "ANCIENT_DEBRIS"

custom:
  name: "Custom"
  items:
    - custom-model-data: 100
      name: "*Some custom item*"
    - custom-model-data: 150
      name: "*Another custom item*"

# do not change this
version: 1

]]>
</code-block>
</procedure>

<procedure title="config.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html

prefix: "<gradient:#00BBFF:#00DDFF><b>AxAuctions</b></gradient> &7» "

database:
  # h2, mysql
  type: "h2"
  prefix: "axauctions"

  # you only need to touch these when using mysql
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

# if enabled, auctions will be synchronized across all connected servers
# you must use mysql (and connect all servers to the same database) for this to work!
# requires a restart to change
multi-server-support:
  # modes:
  # - disabled (no multiserver sync)
  # - sql (uses the database to send messages, no setup required)
  # - proxy (uses plugin messaging, no setup required as long as you are using a bungeecord/velocity proxy)
  # - redis (requires a redis server)
  # - rabbitmq (requires a rabbitmq server)
  # which should i choose? use rabbitmq or redis for the best performance, use sql or proxy is you don't want to set up anything.
  mode: "disabled"
  # the channel name to use (the final name will be axauctions:<channel-name>)
  # keep this value the same for every server where you want the items to be synced
  channel-name: "primary"
  # redis credentials
  redis:
    address: 127.0.0.1
    port: 6379
    username: ''
    password: ''
  # rabbitmq credentials
  rabbitmq:
    address: 127.0.0.1
    port: 5672
    vhost: "/"
    username: 'guest'
    password: 'guest'

# should sellers get their money only when they join?
# with some currency plugins this option is automatically enabled
# the sellers will still be notified about sold items even if this is false
only-give-money-on-join: false

# some economy plugins take time to load, (especially on synced servers) with this setting you can
# control how many seconds should we wait before giving money to player after login
delay-money-give-seconds: 3

number-formatting:
  # modes:
  # 0 - formatted (customizable, look at the formatted part)
  # 1 - short (1K)
  # 2 - raw (1000.4242421412)
  mode: 0
  # https://docs.oracle.com/javase/tutorial/i18n/format/decimalFormat.html
  formatted: "#,###.##"
  # format: language_COUNTRY
  short: "en_US"

# 1 - HH:MM:SS, for example 01:25:35
# 2 - short format, for example 20m
# 3 - text format, for example 01h 25m 35s
timer-format: 1

# https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/SimpleDateFormat.html
# some examples:
# - day/month/year (most used) format: dd/MM/yyyy hh:mm:ss
# - month/day/year (usa) format: MM/dd/yyyy h:mm:ss a
# - year/month/day (default) format: yyyy/MM/dd hh:mm:ss
date-format: "yyyy/MM/dd HH:mm:ss"

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

# what menu should be opened when the /ah or /ah open command is ran without any arguments?
# it is recommended to chose main (the primary auction menu) or category (the category selector)
# possible values: main, category, my-items, expired-items, history, deleted
default-menu: "main"

# what input method should the /ah search or the [search] action use?
# possible options:
# - sign
# - chat
# - anvil
# you can customize the texts in the lang.yml -> input section
search-mode: "sign"

# if true, even if there is only 1 loaded currency, the selector will show
force-currency-selector: false

# if disabled, the currency selector will never show
enable-currency-selector: true

# how often should people be able to refresh the gui?
# all items are stored in memory which should be fast, so this value won't hurt performance unless it is set very low
gui-refresh-cooldown-milliseconds: 150

# what is the largest item that can be put on the auction house?
# this limit is recommended to make sure that people can't slow down the opening by spamming massive items
# enable the debug mode and reload the plugin to get the item sizes printed in the console when /ah sell is used
# in bytes, the default limits are very high so they are not a problem, but increase this if people are getting "item too large" messages
# you can set values to -1 to disable the limits
content-limit-bytes:
  item: 5000
  shulker: 20000
  bundle: 20000

# in the /ah history gui, how many items should be shown at most?
# note that this doesn't delete any data, it will just not request more than the selected amount
# set to -1 to allow unlimited
max-history-length: -1

# if enabled, /ah history will show all auctions made instead of only showing ones related to the player
# if disabled, you can still access this data with the /ahadmin history admin command
show-global-history: false

# if enabled, an expired-items-gui.yml will be generated in the guis folder where the player's expired items will be shown
# and the my items gui will only show the player's active items
# note: to make this gui accessible, you will have to manually edit gui files and add an item with a "[MENU] expired-items" action
# requires a restart to enable
separate-expired-items: false

# you must define at least 1 alias for both
# requires a restart to update
command-aliases:
  auction:
    - "axah"
    - "ah"
    - "auctionhouse"
    - "axauction"
    - "auction"
    - "axauctionhouse"
  admin:
    - "axahadmin"
    - "ahadmin"
    - "auctionhouseadmin"
    - "axauctionadmin"
    - "auctionadmin"
    - "axauctionhouseadmin"

# list of items that CAN'T be sold in the auction house
#
# supported regex: (optional)
# - 'name' #  only 'name' is disallowed
# - 'name*' #  disallows text starting with 'name'
# - '*name' #  disallows text ending with 'name'
# - '*name*' #  disallows text containing 'name'
#
# you can use some sections from our item builder: (https://docs.artillex-studios.com/item-builder.html)
#  > name
#  > material / type
#  > custom-model-data (only the old variant)
blacklist-items:
  - custom-model-data: 100
    material: BARRIER
    name: "*Some custom item*"
  - custom-model-data: 150
    material: BARRIER
    name: "*Another custom item*"

# should be plugin notify you if there is a new update?
update-notifier:
  # if enabled, it will display the message in the console
  enabled: true
  # if enabled, it will broadcast the update message to all players who have the <plugin-name>.update-notify permission
  on-join: true

# in case an exploit is found, if enabled, the plugin will disable some (or all) features to prevent people from abusing them on your server
# requires a restart to change
enable-safety: true

# prints out a lot of information about the plugin in the console
# this can cause a lot of spam, only use if a developer asks you to
debug: false

# do not change this
version: 16

]]>
</code-block>
</procedure>

<procedure title="currencies.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html

# you can create your own currencies by using placeholders
# make sure that none of the placeholders have any formatting on them
# requires PlaceholderAPI
# you will have to restart the server to apply changes
placeholder-currencies:
  Example-Currency:
    register: false
    # if the currency uses whole numbers, then disable this
    # 100.5 - true
    # 100 - false
    uses-double: true
    # if the placeholder gets parsed even for offline players, enable this
    works-offline: false
    # optional: tax (example: 5 is 5% tax)
    tax: 0
    settings:
      raw-placeholder: "%vault_eco_balance_fixed%"
      give-command: "eco give %player% %amount%"
      take-command: "eco take %player% %amount%"
    display:
      raw: "Money"
      gui: "&f%price% &#AAFFFFmoney"
      item:
        material: EMERALD
        name: "&#00DDFFMoney"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"

# supported currencies
currencies:
  Experience:
    register: true
    # optional: tax (example: 5 is 5% tax)
    tax: 0
    display:
      raw: "Experience"
      gui: "&f%price% &#AAFFFFexperience"
      item:
        material: EXPERIENCE_BOTTLE
        name: "&#00DDFFExperience"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  Vault:
    register: true
    tax: 0
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
    tax: 0
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
    tax: 0
    display:
      raw: "RoyaleEconomy"
      gui: "&f%price% &#AAFFFFcoins"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFRoyaleEconomy"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  KingdomsX:
    register: true
    tax: 0
    display:
      raw: "KingdomsX"
      gui: "&f%price% &#AAFFFFnexus points"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFKingdomsX"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  RivalHarvesterHoes:
    register: true
    tax: 0
    display:
      raw: "RivalHarvesterHoes"
      gui: "&f%price% &#AAFFFFessence"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFRivalHarvesterHoes"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  SuperMobCoins:
    register: true
    tax: 0
    display:
      raw: "SuperMobCoins"
      gui: "&f%price% &#AAFFFFmobcoin"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFSuperMobCoins"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  TheOnly-MobCoins:
    register: true
    tax: 0
    display:
      raw: "TheOnly-MobCoins"
      gui: "&f%price% &#AAFFFFmobcoin"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFTheOnly-MobCoins"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  TokenManager:
    register: true
    tax: 0
    display:
      raw: "TokenManager"
      gui: "&f%price% &#AAFFFFtoken"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFTokenManager"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  AxQuestBoard:
    register: true
    tax: 0
    display:
      raw: "AxQuestBoard"
      gui: "&f%price% &#AAFFFFquest points"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFAxQuestBoard"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  BeastTokens:
    register: true
    tax: 0
    display:
      raw: "BeastTokens"
      gui: "&f%price% &#AAFFFFtokens"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFBeastTokens"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  AxMobCoins: # this plugin is unreleased, so don't search for it!
    register: true
    tax: 0
    display:
      raw: "AxMobCoins"
      gui: "&f%price% &#AAFFFFmobcoin"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFAxMobCoins"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  CoinsEngine:
    register: true
    # CoinsEngine supports multiple currencies, so you can also add multiple here
    # "coins" is the name of the currency
    coins:
      tax: 0
      display:
        raw: "CoinsEngine-coins"
        gui: "&f%price% &#AAFFFFcoins"
        item:
          material: GOLD_INGOT
          name: "&#00DDFFCoinsEngine coins"
          lore:
            - " "
            - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  ExcellentEconomy:
    register: true
    # ExcellentEconomy supports multiple currencies, so you can also add multiple here
    # "coins" is the name of the currency
    coins:
      tax: 0
      display:
        raw: "ExcellentEconomy-coins"
        gui: "&f%price% &#AAFFFFcoins"
        item:
          material: GOLD_INGOT
          name: "&#00DDFFExcellentEconomy coins"
          lore:
            - " "
            - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  EcoBits:
    register: true
    # EcoBits supports multiple currencies, so you can also add multiple here
    # "crystals" is the name of the currency
    crystals:
      tax: 0
      display:
        raw: "EcoBits-crystals"
        gui: "&f%price% &#AAFFFFcrystals"
        item:
          material: GOLD_INGOT
          name: "&#00DDFFEcoBits crystals"
          lore:
            - " "
            - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  RedisEconomy:
    register: true
    # RedisEconomy supports multiple currencies, so you can also add multiple here
    # "coins" is the name of the currency
    coins:
      tax: 0
      display:
        raw: "RedisEconomy-coins"
        gui: "&f%price% &#AAFFFFcoins"
        item:
          material: GOLD_INGOT
          name: "&#00DDFFRedisEconomy coins"
          lore:
            - " "
            - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  UltraEconomy:
    register: true
    # UltraEconomy supports multiple currencies, so you can also add multiple here
    # "coins" is the name of the currency
    coins:
      tax: 0
      display:
        raw: "UltraEconomy-coins"
        gui: "&f%price% &#AAFFFFcoins"
        item:
          material: GOLD_INGOT
          name: "&#00DDFFUltraEconomy coins"
          lore:
            - " "
            - "&#00DDFF&l(!) &#00DDFFClick here to select!"
  RivalCredits:
    register: true
    tax: 0
    display:
      raw: "RivalCredits"
      gui: "&f%price% &#AAFFFFcredits"
      item:
        material: GOLD_INGOT
        name: "&#00DDFFRivalCredits"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"

# do not change this
version: 8

]]>
</code-block>
</procedure>

<procedure title="discord.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html

# These are all the options that you can use in the webhook section: (most of them are optional, you can remove them)
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
version: 1

]]>
</code-block>
</procedure>

<procedure title="lang.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html

help:
  - " "
  - "<gradient:#00BBFF:#00DDFF><b>AxAuctions</b></gradient> <#00DDFF>Help"
  - " <#00DDFF>➤ <white>/ah <#DDDDDD>| <#AAFFFF>Open auction menu"
  - " <#00DDFF>➤ <white>/ah open <menu> <#DDDDDD>| <#AAFFFF>Open menu"
  - " <#00DDFF>➤ <white>/ah view <#DDDDDD>| <#AAFFFF>View your auctions"
  - " <#00DDFF>➤ <white>/ah view [player] <#DDDDDD>| <#AAFFFF>View auctions of a player"
  - " <#00DDFF>➤ <white>/ah sell <price> [amount] [currency] <#DDDDDD>| <#AAFFFF>Reload plugin"
  - " <#00DDFF>➤ <white>/ah search [text] <#DDDDDD>| <#AAFFFF>Sell item"
  - " <#00DDFF>➤ <white>/ah history <#DDDDDD>| <#AAFFFF>Check sell and buy history"
  - " <#00DDFF>➤ <#AAFFFF>/ahadmin <#DDDDDD>| <#00DDFF>Admin commands"
  - " "

admin-help:
  - " "
  - "<gradient:#00BBFF:#00DDFF><b>AxAuctions</b></gradient> <#00DDFF>Admin"
  - " <#00DDFF>➤ <white>/ahadmin reload <#DDDDDD>| <#AAFFFF>Reload plugin"
  - " <#00DDFF>➤ <white>/ahadmin forceopon <player> [menu] <#DDDDDD>| <#AAFFFF>Forcefully opens menu"
  - " <#00DDFF>➤ <white>/ahadmin history [player] <#DDDDDD>| <#AAFFFF>Open history GUI"
  - " <#00DDFF>➤ <white>/ahadmin limit give/set/take/reset <player> <amount> <#DDDDDD>| <#AAFFFF>Increase limit of player"
  - " <#00DDFF>➤ <white>/ahadmin convert <plugin> <#DDDDDD>| <#AAFFFF>Convert from another plugin"
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
  - "%container%"

item-lore-own:
  - "%lore%"
  - " "
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
  - " &#999999» &#00DDFFExpires: &#AAFFFF%expires%"
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFCancel Auction"
  - "%container%"

item-lore-expired:
  - "%lore%"
  - " "
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
  - " &#999999» &#00DDFFDeletion: &#AAFFFF%deletion%"
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFTake Back Item"
  - "%container%"

item-lore-staff:
  - "%lore%"
  - " "
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
  - " &#999999» &#00DDFFSeller: &#AAFFFF%seller%"
  - " &#999999» &#00DDFFExpires: &#AAFFFF%expires%"
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFPurchase Item"
  - "%container%"
  - "&#00DDFF&lShift Click &#DDDDDD» &#AAFFFFOpen Removal Menu"

history-item-lore:
  - "%lore%"
  - " "
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - " &#999999» &#00DDFFSeller: &#AAFFFF%seller%"
  - " &#999999» &#00DDFFBuyer: &#AAFFFF%buyer%"
  - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
  - " &#999999» &#00DDFFSold Time: &#AAFFFF%time%"
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - "%container%"

history-admin-item-lore:
  - "%lore%"
  - " "
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - " &#999999» &#00DDFFSeller: &#AAFFFF%seller%"
  - " &#999999» &#00DDFFBuyer: &#AAFFFF%buyer%"
  - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
  - " &#999999» &#00DDFFSold Time: &#AAFFFF%time%"
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFGet Item"
  - "%container%"

deleted-gui-item-lore:
  - "%lore%"
  - " "
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - " &#999999» &#00DDFFSeller: &#AAFFFF%seller%"
  - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
  - " &#999999» &#00DDFFDeleted At: &#AAFFFF%time%"
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - "%container%"

deleted-gui-admin-item-lore:
  - "%lore%"
  - " "
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - " &#999999» &#00DDFFSeller: &#AAFFFF%seller%"
  - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
  - " &#999999» &#00DDFFDeleted At: &#AAFFFF%time%"
  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
  - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFGet Item"
  - "%container%"

# the %container% placeholder is only used when the item is a container (like a shulker)
container: "&#00DDFF&lRight Click &#DDDDDD» &#AAFFFFView Contents"

time:
  second: "s"
  minute: "m"
  hour: "h"
  day: "d"

sorting:
  newest: "Newest to oldest"
  oldest: "Oldest to newest"
  cheapest: "Cheapest to priciest"
  priciest: "Priciest to cheapest"

currency:
  # used for the %selected_currency% placeholder when none is selected
  no-currency: "All"

sell:
  limit-reached: "&#FF0000You have reached the auction limit! &7(%current%/%limit%)"
  no-item: "&#FF0000Hold something in your hand to sell it!"
  no-currency: "&#FF0000You must give a currency parameter!"
  price-too-low: "&#FF0000The price you have set is below the minimum of &f%amount%&#FF0000!"
  price-too-high: "&#FF0000The price you have set is above the maximum of &f%amount%&#FF0000!"
  invalid-price: "&#FF0000The price you have set is not a valid number!"
  success: "&#33FF33You have successfully put &f%amount% &#33FF33items on the auction house for &f%price%&#33FF33!"
  # set to "" to disable
  # these will be shown to all players
  action-bar-broadcast: "&#00DDFF%player% &fhas started selling &#00DDFF%amount% &fof &#00DDFF%item% &ffor &#00DDFF%price%&f! &#DDDDDD/ah"
  chat-broadcast: ""

buy:
  not-enough-money: "&#FF0000You can't afford this item!"
  item-not-found: "&#FF0000The item is not found! Somebody must have bought it or the seller cancelled it!"
  inventory-full: "&#FF0000Your inventory is full!"
  success: "&#33FF33You have purchased &f%amount%x %item% &#33FF33from the auction house for &f%price%&#33FF33!"
  # this will be used when there is 0% tax set for the currency
  notify-seller: "&#00DDFF%player% &fhas purchased your &#00DDFF%amount%x &#00DDFF%item% &ffor &#00DDFF%price% &ffrom the auction house!"
  # this will be used when a tax is set for the currency
  #  %amount% (the original amount)
  #  %tax-amount% (amount after tax)
  #  %tax-percent% (the % of tax on the currency)
  #  %tax-fee% (amount taken because of tax)
  notify-seller-tax: "&#00DDFF%player% &fhas purchased your &#00DDFF%amount%x &#00DDFF%item% &ffor &#00DDFF%price% &#DDDDDD(%tax-amount% &#DDDDDDafter taxes) &ffrom the auction house!"
  # set to "" to disable
  # these will be shown to all players
  action-bar-purchase: "&#00DDFF%player% &fhas purchased &#00DDFF%amount% &fof &#00DDFF%item% &ffrom &#00DDFF%seller% &ffor &#00DDFF%price%&f! &#DDDDDD/ah"
  chat-purchase: ""

admin-action:
  cancelled: "&#00DDFF%staff% &fhas cancelled your &#00DDFF%amount%x &#00DDFF%item% &fin the auction house at &#00DDFF%date%&f!"
  removed: "&#00DDFF%staff% &fhas removed your &#00DDFF%amount%x &#00DDFF%item% &ffrom the auction house at &#00DDFF%date%&f!"
  cancelled-info: "&#FF3333You have successfully cancelled the item in the auction house!"
  removed-info: "&#FF3333You have successfully removed the item from the auction house!"
  failed: "&#FF3333Failed to remove item from the auction house! Somebody might have bought it or cancelled it."
  take-item: "&#33FF33The clicked item has been placed in your inventory!"

my-items:
  removed: "&#FF0000You have successfully removed the item from the auction house!"
  expired: "&fYour &#00DDFF%amount%x &#00DDFF%item% &fhas expired at &#00DDFF%date%&f!"
  deleted: "&fYour &#00DDFF%amount%x &#00DDFF%item% &fhas been deleted at &#00DDFF%date%&f!"
  failed: "&#FF3333Failed to remove item from the auction house! Somebody might have bought it or cancelled it."

limit-changed: "&#33FF33You have changed &f%player%&#33FF33's limit to &f%amount%&#33FF33!"
date-format: "yyyy. MM. dd HH:mm:ss"
limit-bypass-icon: "∞"
expired: "Expired"
blacklisted: "&#FF0000This item is blacklisted and can't be sold in the auction houses!"
oversized: "&#FF0000This item is too large to be sold in the auction house!"
converting: "&#33FF33Started converter, check the console for more information!"

data-not-loaded: "&#FF0000Your data has not been loaded yet, please wait a moment before trying it again!"
data-not-loaded-other: "&#FF0000The data of &#BB0000%player% &#FF0000has not been loaded yet! Please try again in a moment!"

input:
  # keep the first line empty when using sign
  sign:
    - ""
    - "-----------"
    - "Write in the first"
    - "line to search!"
  anvil:
    title: "&0Search Here"
    item:
      material: PAPER
      glow: true
      name: "&fSEARCH HERE"
      lore:
        - "&#00DDFF↑ searching for"
  chat:
    - "&#00DDFFWhat do you want to search for? &#DDDDDD(type &#00DDFFcancel &#DDDDDDto stop)"

commands:
  invalid-value: "&#FF0000Invalid parameter: &#BB0000%value%"
  invalid-command: "&#FF0000Invalid command or subcommand!"
  missing-argument: "&#FF0000Missing argument! You must specify a value for &#BB0000%value%&#FF0000."
  no-permission: "&#FF0000You don't have permission to access this command!"
  out-of-range: "&#FF0000The &#BB0000%number% &#FF0000must be between &#BB0000%min% &#FF0000and &#BB0000%max%&#FF0000!"
  player-only: "&#FF0000You must be a player to use this command!"
  invalid-player: "&#FF0000The player &#BB0000%player% &#FF0000can not be found!"
  invalid-selector: "&#FF0000You can not use this selector in this command!"

update-notifier: "&#88CCFFThere is a new version of AxAuctions available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"
safety: "&#FF0000This feature has been disabled for safety reasons and updating the plugin is required, please contact the server administrators."

# do not change this
version: 15

]]>
</code-block>
</procedure>

- And for example, the main-gui.yml:
<procedure title="guis/main-gui.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html
# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

title: "&0Auction House (%current_page%/%max_page%)"
# a gui can have 1-6 rows
rows: 6
# how many items should be shown on a single page?
page-size: 36
# should the gui auto update?
# in ticks, 20 ticks = 1 second
# set to -1 to disable auto updater
auto-update-ticks: -1

# ----- ITEMS -----

filler:
  slot: ["0-8", "45-53"]
  material: "LIGHT_BLUE_STAINED_GLASS_PANE"
  name: " "

# this will only work if you have the categories enabled!
category-menu:
  slot: 0
  material: "SHULKER_BOX"
  conditions:
    - "%categories_enabled% == true"
  name: "&#00DDFF&lᴄᴀᴛᴇɢᴏʀʏ ꜱᴇʟᴇᴄᴛᴏʀ"
  lore:
    - " "
    - " &fClick here to go"
    - " &fto the category selector!"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFCategory Selector"
  actions:
    - "[MENU] category"
    - "[SOUND] ui.button.click|1|1"

# this will only work if you have the categories enabled!
category-switch:
  slot: 8
  material: "NOTE_BLOCK"
  conditions:
    - "%categories_enabled% == true"
  name: "&#00DDFF&lᴄᴀᴛᴇɢᴏʀʏ"
  lore:
    - " "
    - " &#00DDFFCurrently selected:"
    - "  &#00DDFF❙ &#AAFFFF%selected_category%"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Category"
    - "&#00DDFF&lShift Click &#DDDDDD» &#AAFFFFReset Category"
  actions:
    - "[CATEGORY]"
    - "[SOUND] ui.button.click|1|1"

statistics:
  slot: 4
  material: "BOOK"
  name: "&#00DDFF&lꜱᴛᴀᴛɪꜱᴛɪᴄꜱ"
  lore:
    - " "
    - " &#00DDFFActive Auctions:"
    - "  &#00DDFF❙ &#FFFFFFGlobal Items: &#AAFFFF%total_active_count%"
    - "  &#00DDFF❙ &#FFFFFFMy Items: &#AAFFFF%sell_count%/%sell_limit%"
    - " "
    - " &#00DDFFMy Earnings: &#CCCCCC(ᴀʟʟ ᴛɪᴍᴇ)"
    - "  &#00DDFF❙ &#FFFFFFSold Items: &#AAFFFF%items_sold%"
    - "  &#00DDFF❙ &#FFFFFFMoney Made: &#AAFFFF%money_made%"
    - " "
    - " &#00DDFFMy Spendings: &#CCCCCC(ᴀʟʟ ᴛɪᴍᴇ)"
    - "  &#00DDFF❙ &#FFFFFFPurchased Items: &#AAFFFF%items_purchased%"
    - "  &#00DDFF❙ &#FFFFFFMoney Spent: &#AAFFFF%money_spent%"
    - " "
    - "&#00DDFF&lSell Items &#DDDDDD» &#AAFFFF/ah sell"

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
  actions:
    - "[MENU] my-items"
    - "[SOUND] ui.button.click|1|1"

sorting-newest:
  slot: 46
  material: "GLOWSTONE_DUST"
  conditions:
    - "%selected_sorting_raw% == newest"
  name: "&#00DDFF&lsᴏʀᴛɪɴɢ"
  lore:
    - " "
    - " &#00DDFFCurrently selected:"
    - "  &#00DDFF❙ &#AAFFFFNewest First"
    - "  &#00DDFF❙ &#CCCCCCOldest First"
    - "  &#00DDFF❙ &#CCCCCCLowest Price"
    - "  &#00DDFF❙ &#CCCCCCHighest Price"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Sorting"
    - "&#00DDFF&lShift Click &#DDDDDD» &#AAFFFFReset Sorting"
  actions:
    - "[SORTING] oldest|priciest"
    - "[SOUND] ui.button.click|1|1"

sorting-oldest:
  slot: 46
  material: "REDSTONE"
  conditions:
    - "%selected_sorting_raw% == oldest"
  name: "&#00DDFF&lsᴏʀᴛɪɴɢ"
  lore:
    - " "
    - " &#00DDFFCurrently selected:"
    - "  &#00DDFF❙ &#CCCCCCNewest First"
    - "  &#00DDFF❙ &#AAFFFFOldest First"
    - "  &#00DDFF❙ &#CCCCCCLowest Price"
    - "  &#00DDFF❙ &#CCCCCCHighest Price"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Sorting"
    - "&#00DDFF&lShift Click &#DDDDDD» &#AAFFFFReset Sorting"
  actions:
    - "[SORTING] cheapest|newest"
    - "[SOUND] ui.button.click|1|1"

sorting-cheapest:
  slot: 46
  material: "GLOWSTONE_DUST"
  conditions:
    - "%selected_sorting_raw% == cheapest"
  name: "&#00DDFF&lsᴏʀᴛɪɴɢ"
  lore:
    - " "
    - " &#00DDFFCurrently selected:"
    - "  &#00DDFF❙ &#CCCCCCNewest First"
    - "  &#00DDFF❙ &#CCCCCCOldest First"
    - "  &#00DDFF❙ &#AAFFFFLowest Price"
    - "  &#00DDFF❙ &#CCCCCCHighest Price"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Sorting"
    - "&#00DDFF&lShift Click &#DDDDDD» &#AAFFFFReset Sorting"
  actions:
    - "[SORTING] priciest|oldest"
    - "[SOUND] ui.button.click|1|1"

sorting-priciest:
  slot: 46
  material: "REDSTONE"
  conditions:
    - "%selected_sorting_raw% == priciest"
  name: "&#00DDFF&lsᴏʀᴛɪɴɢ"
  lore:
    - " "
    - " &#00DDFFCurrently selected:"
    - "  &#00DDFF❙ &#CCCCCCNewest First"
    - "  &#00DDFF❙ &#CCCCCCOldest First"
    - "  &#00DDFF❙ &#CCCCCCLowest Price"
    - "  &#00DDFF❙ &#AAFFFFHighest Price"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Sorting"
    - "&#00DDFF&lShift Click &#DDDDDD» &#AAFFFFReset Sorting"
  actions:
    - "[SORTING] newest|cheapest"
    - "[SOUND] ui.button.click|1|1"

previous-page:
  slot: 48
  material: "ARROW"
  conditions:
    - "%current_page% > 1"
  name: "&#00DDFF&lᴘʀᴇᴠɪᴏᴜs ᴘᴀɢᴇ"
  lore:
    - " "
    - " &fClick here to go back"
    - " &fto the previous page!"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFPrevious Page"
  actions:
    - "[PAGE] previous"
    - "[SOUND] ui.button.click|1|1"

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
  actions:
    - "[REFRESH]"
    - "[SOUND] ui.button.click|1|1"

next-page:
  slot: 50
  material: "ARROW"
  conditions:
    - "%current_page% < %max_page%"
  name: "&#00DDFF&lɴᴇxᴛ ᴘᴀɢᴇ"
  lore:
    - " "
    - " &fClick here to go"
    - " &fto the next page!"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFNext Page"
  actions:
    - "[PAGE] next"
    - "[SOUND] ui.button.click|1|1"

currency:
  slot: 52
  material: "HOPPER"
  name: "&#00DDFF&lᴄᴜʀʀᴇɴᴄʏ"
  lore:
    - " "
    - " &#00DDFFCurrently selected:"
    - "  &#00DDFF❙ &#AAFFFF%selected_currency%"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Currency"
    - "&#00DDFF&lShift Click &#DDDDDD» &#AAFFFFReset Currency"
  actions:
    - "[CURRENCY]"
    - "[SOUND] ui.button.click|1|1"

search:
  slot: 53
  material: SPYGLASS
  name: "&#00DDFF&lꜱᴇᴀʀᴄʜ"
  lore:
    - " "
    - " &#00DDFFCurrent search:"
    - "  &#00DDFF❙ &#AAFFFF%search%"
    - " "
    - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFSearch"
    - "&#00DDFF&lShift Click &#DDDDDD» &#AAFFFFClear Search"
  actions:
    - "[SEARCH]"
    - "[SOUND] ui.button.click|1|1"

#decoration-example:
#  slot: 13
#  material: IRON_INGOT
#  name: '&eDECORATION'
#  lore:
#    - ' '
#    - ' &fWoah, what a cool decoration!'

]]>
</code-block>
</procedure>