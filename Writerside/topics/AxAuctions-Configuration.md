# Configuration

<procedure title="config.yml" collapsible="true"><step>
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

	# when using mysql, how should data be sent between servers?
	# values: none, sql
	# if you don't need multi server support, set to none to disable
	multi-server-support: "sql"

	# should sellers get their money only when they join?
	# with some currency plugins this option is automatically enabled
	# the sellers will still be notified about sold items even if this is false
	# if you change this while the plugin is used, some players may get their money twice or lose their money
	only-give-money-on-join: false

	# if only-give-money-on-join is enabled, this will delay giving the money by X seconds
	# this can be useful if you're waiting for a plugin to load player data or if the chat is too spammy on join
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

	# how often should people be able to refresh the gui?
	# if you use mysql this is probably a good idea to keep high
	# on local databases, (like h2) you can set this to any number really
	gui-refresh-cooldown-milliseconds: 250

	# in the /ah history gui, how many items should be shown at most?
	# note that this doesn't delete any data, it will just not request more than the selected amount
	# set to -1 to allow unlimited
	max-history-length: -1

	# list of items that CAN'T be sold in the auction house
	# note: the name-contains string shouldn't include any color codes
	blacklisted-items:
	  "1":
		material: "barrier"
		name-contains: "Banned item's name"

	# should be plugin notify you if there is a new update?
	update-notifier:
	  # if enabled, it will display the message in the console
	  enabled: true
	  # if enabled, it will broadcast the update message to all players who have the <plugin-name>.update-notify permission
	  on-join: true

	# prints out a lot of random information about the plugin in the console
	# only use if the developers ask you for this
	debug: false

	# do not change this
	version: 9
	
	]]>
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
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html

	# you can create your own currencies by using placeholders
	# make sure that none of the placeholders have any formatting on them
	# requires PlaceholderAPI
	placeholder-currencies:
	  Example-Currency:
		register: false
		# if the currency uses whole numbers, then disable this
		# 100.5 - true
		# 100 - false
		uses-double: true
		# if the placeholder gets parsed even for offline players, enable this
		works-offline: false
		# in percentage
		# for example set it to 0.9 for 10% tax
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
		# in percentages, set to 0 to disable
		# for example set it to 0.9 for 10% tax
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

	# do not change this
	version: 6
	
	]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html

	help:
	  - " "
	  - "<gradient:#00BBFF:#00DDFF><b>AxAuctions Help</b></gradient> &7»"
	  - " &7- &f/ah &7| &#00DDFFOpen auction menu"
	  - " &7- &f/ah view &7| &#00DDFFView your auctions"
	  - " &7- &f/ah view [player] &7| &#00DDFFView auctions of a player"
	  - " &7- &f/ah sell <price> [amount] [currency] &7| &#00DDFFSell item"
	  - " &7- &f/ah search [text] &7| &#00DDFFSearch for items by type/name/lore"
	  - " &7- &f/ah history &7| &#00DDFFCheck sell and buy history"
	  - " &7- &#00CCFF/ahadmin &7| &#00AAFFAdmin Commands"
	  - " "

	admin-help:
	  - " "
	  - "<gradient:#00BBFF:#00DDFF><b>AxAuctions Admin Help</b></gradient> &7»"
	  - " &7- &f/ahadmin reload &7| &#00DDFFReload plugin"
	  - " &7- &f/ahadmin history [player] &7| &#00DDFFOpen history GUI"
	  - " &7- &f/ahadmin limit give/set/take/reset <player> <amount> &7| &#00DDFFIncrease limit of player"
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

	item-lore-staff:
	  - "%lore%"
	  - " "
	  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
	  - " &#999999» &#00DDFFPrice: &#AAFFFF%price%"
	  - " &#999999» &#00DDFFSeller: &#AAFFFF%seller%"
	  - " &#999999» &#00DDFFExpires: &#AAFFFF%expires%"
	  - "&#999999&m▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬"
	  - "&#00DDFF&lClick &#DDDDDD» &#AAFFFFPurchase Item"
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

	sell:
	  limit-reached: "&#FF0000You have reached the auction limit! &7(%current%/%limit%)"
	  no-item: "&#FF0000Hold something in your hand to sell it!"
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
	  notify-seller: "&#00DDFF%player% &fhave purchased your &#00DDFF%amount%x &#00DDFF%item% &ffor &#00DDFF%price% &ffrom the auction house!"
	  # set to "" to disable
	  # these will be shown to all players
	  action-bar-purchase: "&#00DDFF%player% &fhas purchased &#00DDFF%amount% &fof &#00DDFF%item% &ffrom &#00DDFF%seller% &ffor &#00DDFF%price%&f! &#DDDDDD/ah"
	  chat-purchase: ""

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

	data-not-loaded: "&#FF0000Your data has not been loaded yet, please wait a moment before trying it again!"
	data-not-loaded-other: "&#FF0000The data of &#BB0000%player% &#FF0000has not been loaded yet! Please try again in a moment!"

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

	# do not change this
	version: 6
	
	]]>
</code-block></step>
</procedure>

**There are many GUI configs, here is one:**
<procedure title="guis/main-gui.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axauctions.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	title: "&0Auction House (%current_page%/%max_page%)"
	# a gui can have 1-6 rows
	rows: 6
	# how many items should be shown on a single page?
	page-size: 45
	# auto update the menu?
	# in ticks, 20 ticks = 1 second
	auto-update-ticks: -1

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
	  actions:
		- "[MENU] my-items"
		- "[SOUND] ui.button.click|1|1"

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
	  actions:
		- "[SOUND] ui.button.click|1|1"

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
		- "  &#444444❙ &#AAFFAA%selected_currency%"
		- " "
		- "&#00DDFF&lClick &#DDDDDD» &#AAFFFFChange Currency"
	  # used for the %selected_currency% when none is selected
	  no-currency: "All"
	  actions:
		- "[SOUND] ui.button.click|1|1"

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
		- "&#00DDFF&lSell Items &#DDDDDD» &#AAFFFF/ah sell"

	#decoration-example:
	#  slot: 13
	#  material: IRON_INGOT
	#  name: '&eDECORATION'
	#  lore:
	#    - ' '
	#    - ' &fWoah, what a cool decoration!'
	
	]]>
</code-block></step>
</procedure>