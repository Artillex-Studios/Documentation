# Configuration

<procedure title="auctions/example.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axdarkauctions.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	name: "&#7700FFExample Auction"

	locations:
	  spawn: null
	  display: null

	npcs:
	  entrance:
		enabled: true
		location: null
		skin-base64: ""
		name:
		  - "&#D200FFDark Auction Guard"
		  - "&#DDDDDDᴄʟɪᴄᴋ ᴛᴏ ᴇɴᴛᴇʀ"
	  exit:
		enabled: true
		location: null
		skin-base64: ""
		name:
		  - "&#D200FFDark Auction Guard"
		  - "&#DDDDDDᴄʟɪᴄᴋ ᴛᴏ ʟᴇᴀᴠᴇ"
	  auctioneer:
		enabled: true
		location: null
		skin-base64: ""
		name:
		  - "&#D200FFAuctioneer"

	# how many players are needed for a dark auction to start & what is the limit?
	players:
	  minimum: 0
	  # set to -1 to make it unlimited
	  maximum: -1

	display:
	  enabled: true
	  block:
		material: GLASS
		glow: false
	  preview-lines:
		- "%item%"
		- "&fꜱᴛᴀʀᴛɪɴɢ ʙɪᴅ: &#D200FF%bid%"
		- "&fʙɪᴅᴅɪɴɢ ꜱᴛᴀʀᴛꜱ: &#D200FF%time% ⌚"
		- "&#D200FFClick to view bidding!"
	  bidding-lines:
		- "%item%"
		- "&fʜɪɢʜᴇꜱᴛ ʙɪᴅ: &#D200FF%bid%"
		- "&fʙɪᴅᴅɪɴɢ ᴇɴᴅꜱ: &#D200FF%time% ⌚"
		- "&#D200FFClick to view bidding!"

	# how many items should be sold at a single dark auction?
	# this can be a single number or a range (= the item amount will be randomly selected between the 2 numbers)
	sell-item-amount: "3-5"

	# what items should be sold at the dark auction?
	# chances can go over 100%
	# you can add as many items as you would like
	items:
	  - chance: 50.0
		starting-price:
		  currency: "Vault"
		  amount: 100.0
		display:
		  name: "&#AAAAAA1x Iron Ingot"
		  material: iron_ingot
		commands:
		  - "give %player% iron_ingot 1"
	  - chance: 25.0
		starting-price:
		  currency: "Vault"
		  amount: 100.0
		display:
		  name: "&#88FFFF1x Diamond"
		  material: diamond
		items:
		  - amount: 1
			material: diamond
	]]>
</code-block></step>
</procedure>

<procedure title="guis/main.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axdarkauctions.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	title: "&0&lDark Auction > &0Bidding"
	# a gui can have 1-6 rows
	rows: 6

	# ----- ITEMS -----

	filler:
	  material: BLACK_STAINED_GLASS_PANE
	  name: " "
	  slot:
		- "0-53"

	item:
	  slot: 3

	clock:
	  slot: 5
	  material: CLOCK
	  name: "&#D200FF&lBidding"
	  lore:
		- " "
		- " &#DDDDDD- &fEnds in: &#D200FF%time% seconds"
		- " "

	# it is important to put these slots in the order that you want them to go!
	# X|Y - vertical range, for example 18|45 selects slots: 18, 27, 36, 45
	# X-Y - horizontal range, for example 45-47 selects slots: 45, 46, 47
	bid-slots:
	  - "18|45"
	  - "46"
	  - "47|20"
	  - "21"
	  - "22|49"
	  - "50"
	  - "51|24"
	  - "25"
	  - "26|53"

	bidding:
	  already-higher:
		# by default, player head will use the bidder player's head
		material: BARRIER
		name: "&#D200FFBid &#7700FF%amount%"
		lore:
		  - " "
		  - "&#D200FF&l> &#D200FFSomebody already bid more than this amount!"
	  current-bid:
		# by default, player head will use the bidder player's head
		material: PLAYER_HEAD
		name: "&#D200FFBid &#7700FF%amount%"
		lore:
		  - " "
		  - " &#DDDDDD- &#D200FF%player% &falready bid this amount!"
		  - " "
		  - "&#D200FF&l> &#D200FFYou can't bid because there is already a bid at this amount!"
	  bid:
		# by default, the material will be used from the config.yml (check 'bidding' section) based on the money amount
		name: "&#D200FFBid &#7700FF%amount%"
		lore:
		  - " "
		  - "&#D200FF&l> &#D200FFClick here to place your bid!"
	]]>
</code-block></step>
</procedure>

<procedure title="guis/preview.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axdarkauctions.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	title: "&0&lDark Auction > &0Next Bid"
	# a gui can have 1-6 rows
	rows: 3

	# ----- ITEMS -----

	filler:
	  material: BLACK_STAINED_GLASS_PANE
	  name: " "
	  slot:
		- "0-26"

	gray:
	  material: GRAY_STAINED_GLASS_PANE
	  name: " "
	  slot:
		- "10-12"
		- "14-16"

	item:
	  slot: 11

	clock:
	  slot: 15
	  material: CLOCK
	  name: "&#D200FF&lBidding"
	  lore:
		- " "
		- " &#DDDDDD- &fStarts in: &#D200FF%time% seconds"
		- " "
		- "&#D200FF&l> &#D200FFGet ready!"
	]]>
</code-block></step>
</procedure>

<procedure title="config.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axdarkauctions.html

	prefix: "<gradient:#7700FF:#FF00FF><b>AxDarkAuctions</b></gradient> &7» "

	# format: language_COUNTRY
	# after changing this, the server will download the default item names
	language: en_US

	# should you be able to put more money on the auction, even if you are already winning?
	allow-increasing-own-bid: true

	# should the bidding gui open when a new item is ready to be bid on?
	automatically-open-bidding: true

	# should the item preview gui open?
	automatically-open-preview: true

	# if this is disabled, you will not be able to join the auction while it is running
	allow-joining-after-start: true

	# you must define at least 1
	# requires a restart to update
	command-aliases:
	  - "axdarkauctions"
	  - "axda"
	  - "da"
	  - "darkauctions"
	  - "darkauction"

	# these are all in seconds
	times:
	  # the time before the first item is being shown
	  start-wait-time: 60
	  # when the item gets shown, but it is not yet biddable
	  show-time: 5
	  # the length that the item can be bid on
	  bid-time: 15
	  # if the bid would end in is less than X seconds, but somebody
	  # outbids the leader, should the timer be increased back to X seconds?
	  extend-bid-time: true
	  # if someone bids under this many seconds, the timer will jump back to this amount
	  extend-time: 8
	  # after a bid winner is announced, how long of a wait should there be until the next bid?
	  time-between-bids: 5
	  # the time after the last bid ends before players get kicked out
	  end-wait-time: 30

	# the number is the bid amount where this will start to get used
	# increase is how much the money amount will grow between 2 bids
	bidding:
	  0:
		material: IRON_INGOT
		increase: 100
	  10000:
		material: GOLD_INGOT
		increase: 1000
	  100000:
		material: DIAMOND
		increase: 10000
	  1000000:
		material: EMERALD
		increase: 100000
	  10000000:
		material: NETHERITE_INGOT
		increase: 1000000

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

	# should be plugin notify you if there is a new update?
	update-notifier:
	  # if enabled, it will display the message in the console
	  enabled: true
	  # if enabled, it will broadcast the update message to all players who have the <plugin-name>.update-notify permission
	  on-join: true

	# do not change
	version: 1
	]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axdarkauctions.html

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
		name: "&f%price% &#AAFFFFmoney"
		settings:
		  raw-placeholder: "%vault_eco_balance_fixed%"
		  give-command: "eco give %player% %amount%"
		  take-command: "eco take %player% %amount%"

	# supported currencies
	currencies:
	  Experience:
		register: true
		name: "&f%price% &#AAFFFFexperience"
	  Vault:
		register: true
		name: "&f%price% &#AAFFFFcoins"
	  PlayerPoints:
		register: true
		name: "&f%price% &#AAFFFFpoints"
	  RoyaleEconomy:
		register: true
		name: "&f%price% &#AAFFFFcoins"
	  KingdomsX:
		register: true
		name: "&f%price% &#AAFFFFnexus points"
	  RivalHarvesterHoes:
		register: true
		name: "&f%price% &#AAFFFFessence"
	  SuperMobCoins:
		register: true
		name: "&f%price% &#AAFFFFmobcoin"
	  TheOnly-MobCoins:
		register: true
		name: "&f%price% &#AAFFFFmobcoin"
	  TokenManager:
		register: true
		name: "&f%price% &#AAFFFFtoken"
	  AxQuestBoard:
		register: true
		name: "&f%price% &#AAFFFFquest points"
	  BeastTokens:
		register: true
		name: "&f%price% &#AAFFFFtokens"
	  AxMobCoins: # this plugin is unreleased, so don't search for it!
		register: true
		name: "&f%price% &#AAFFFFmobcoin"
	  CoinsEngine:
		register: true
		# CoinsEngine supports multiple currencies, so you can also add multiple here
		# "coins" is the name of the currency
		coins:
		  name: "&f%price% &#AAFFFFcoins"
	  EcoBits:
		register: true
		# EcoBits supports multiple currencies, so you can also add multiple here
		# "crystals" is the name of the currency
		crystals:
		  name: "&f%price% &#AAFFFFcrystals"
	  RedisEconomy:
		register: true
		# RedisEconomy supports multiple currencies, so you can also add multiple here
		# "coins" is the name of the currency
		coins:
		  name: "&f%price% &#AAFFFFcoins"
	  UltraEconomy:
		register: true
		# UltraEconomy supports multiple currencies, so you can also add multiple here
		# "coins" is the name of the currency
		coins:
		  name: "&f%price% &#AAFFFFcoins"

	# do not change this
	version: 1
	]]>
</code-block></step>
</procedure>

<procedure title="schedulers.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axdarkauctions.html

	admin-help:
	  - " "
	  - "<gradient:#7700FF:#FF00FF><b>AxDarkAuctions</b></gradient> &7»"
	  - " &7- &f/axda join [auction] &7| &#D200FFJoin dark auction!"
	  - " &7- &f/axda leave &7| &#D200FFLeave dark auction!"
	  - " &7- &f/axda reload &7| &#D200FFReload plugin"
	  - " &7- &f/axda create <name> &7| &#D200FFCreate new dark auction"
	  - " &7- &f/axda delete <auction> &7| &#D200FFDelete dark auction"
	  - " &7- &f/axda editor <auction> &7| &#D200FFOpen editor"
	  - " &7- &f/axda schedulers &7| &#D200FFEdit schedulers"
	  - " &7- &f/axda start <auction> &7| &#D200FFStart dark auction"
	  - " &7- &f/axda stop <auction> &7| &#D200FFStop dark auction"
	  - " &7- &f/axda forcejoin <auction> <player> &7| &#D200FFMake player join dark auction"
	  - " "

	player-help:
	  - " "
	  - "<gradient:#7700FF:#FF00FF><b>AxDarkAuctions</b></gradient> &7»"
	  - " &7- &f/axda join [auction] &7| &#D200FFJoin dark auction!"
	  - " &7- &f/axda leave &7| &#D200FFLeave dark auction!"
	  - " &7- &f/axda info [auction] &7| &#D200FFShow when the dark auction starts!"
	  - " "

	time:
	  second: "s"
	  minute: "m"
	  hour: "h"
	  day: "d"

	reload:
	  success: "&#33FF33Plugin successfully reloaded!"
	  failed: "&#FF3333Failed to reload the plugin! Something is wrong in the &f%file%&#FF3333 file, look in the console or use a yaml validator to fix the errors!"

	start: "&#00FF00You have started the &f%auction% &#00FF00dark auction!"
	stop: "&#00FF00You have stopped the &f%auction% &#00FF00dark auction!"

	created: "&#00FF00You have successfully created the &f%auction% &#00FF00dark auction! &#DDDDDDUse the &f/axda editor %auction% &#DDDDDDto edit!"
	deleted: "&#FF0000You have deleted the &f%auction% &#FF0000dark auction!"

	joined: "&#D200FFYou have joined the &f%auction% &#D200FFdark auction!"
	left: "&#D200FFYou have left the &f%auction% &#D200FFdark auction!"

	info: "&#D200FFThe next dark auction will be in &f%time%&#D200FF!"

	starting:
	  - " "
	  - "&#D200FFThe &f%display-name% &#D200FFdark auction is starting in &f%time% &#D200FFseconds!"
	  - "&#DDDDDDJoin with /darkauctions join %name% or find the NPC!"
	  - " "

	broadcasts:
	  starting: "&#7700FF&lAuctioneer &7» &#D200FFThe dark auction is starting in &f%time% &#D200FFseconds!"
	  started: "&#7700FF&lAuctioneer &7» &#D200FFThe dark auction is starting! Get ready!"
	  ended: "&#7700FF&lAuctioneer &7» &#D200FFThere are no more items to be auctioned! Today's dark auction is over, come back next time! Leave or you will be teleported out in &f%time% &#D200FFseconds!"
	  waiting: "&#7700FF&lAuctioneer &7» &#D200FFThe next item will be announced in &f%time% &#D200FFseconds!"
	  showing: "&#7700FF&lAuctioneer &7» &#D200FFThe next item that you can bid for is: &f%item%&#D200FF, the starting price is: &f%amount%&#D200FF! The bidding will start in &f%time% &#D200FFseconds!"
	  bidding: "&#7700FF&lAuctioneer &7» &#D200FFThe bidding has started for the following item: &f%item%&#D200FF, at the starting price of &f%amount%&#D200FF! The winner will be announced in &f%time% &#D200FFseconds!"
	  bid: "&#7700FF&lAuctioneer &7» &f%player% &#D200FFhas bid &f%amount%&#D200FF! There are still &f%time% &#D200FFseconds left!"
	  no-bidders: "&#7700FF&lAuctioneer &7» &#D200FFNobody has bid on the item &f%item%&#D200FF!"
	  winner: "&#7700FF&lAuctioneer &7» &f%player% &#D200FFhas won the &f%item% &#D200FFfor &f%amount%&#D200FF!"
	  cheater: "&#7700FF&lAuctioneer &7» &f%player% &#D200FFtried to cheat the auction, so the bidding will be restarted!"
	  join: "&#00FF00+ &#DDDDDD%player% joined!"
	  leave: "&#FF0000- &#DDDDDD%player% left!"

	errors:
	  disallowed: "&#FF0000You can't do that while you are in a dark auction!"
	  already-in: "&#FF0000You are already in a dark auction!"
	  not-in: "&#FF0000You are not in a dark auction!"
	  not-found: "&#FF0000The auction does not exist!"
	  already-running: "&#FF0000The dark auction is already running!"
	  not-running: "&#FF0000The dark auction is not running!"
	  already-exists: "&#FF0000There is already an auction with the name &f%auction%&#FF0000!"
	  full: "&#FF0000The &f%auction% &#FF0000dark auction is full! &#DDDDDD(%players%/%max%)"
	  banned: "&#FF0000You have been banned from this dark auction for not having enough money to pay the bid!"
	  started: "&#FF0000You can't join because the dark auction has already started!"
	  already-higher: "&#FF0000The current highest bid is already higher than &f%amount%&#FF0000!"
	  already-winning: "&#FF0000You are already the top bidder!"
	  not-enough-balance: "&#FF0000You can afford to bid &f%amount%&#FF0000, you only have &f%balance%&#FF0000!"

	commands:
	  invalid-value: "&#FF0000Invalid parameter: &#BB0000%value%"
	  invalid-command: "&#FF0000Invalid command or subcommand!"
	  missing-argument: "&#FF0000Missing argument! You must specify a value for &#BB0000%value%&#FF0000."
	  no-permission: "&#FF0000You don't have permission to access this command!"
	  out-of-range: "&#FF0000The &#BB0000%number% &#FF0000must be between &#BB0000%min% &#FF0000and &#BB0000%max%&#FF0000!"
	  player-only: "&#FF0000You must be a player to use this command!"
	  invalid-player: "&#FF0000The player &#BB0000%player% &#FF0000can not be found!"
	  invalid-selector: "&#FF0000You can not use this selector in this command!"

	update-notifier: "&#D200FFThere is a new version of AxDarkAuctions available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"

	# do not change
	version: 1
	]]>
</code-block></step>
</procedure>

<procedure title="currencies.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axdarkauctions.html

	# list of timezones: https://docs.oracle.com/cd/E72987_01/wcs/tag-ref/MISC/TimeZones.html
	# keep on 'server' to use the server machine's timezone
	# some examples: Europe/Paris, America/New_York
	timezone: "server"

	# this uses the usual CRON format
	# generator: https://crontab.guru/
	# the format is:
	# <minute> <hour> <day> <month> <day of week>
	# you can use '*'-s to make it run all the time when the other rules also match

	# you can make as many scheduler as you would like
	example:
	  times:
		- "0 18 * * *" # this will run at hour 18 (6pm), minute 0, every day
	  # if 'random' is enabled, a random auction will start from the list
	  # otherwise, all the auctions listed will be started
	  # note: random scheduler will be ignored in placeholders
	  random: false
	  # list of dark auctions that will be activated
	  auctions:
		- "example"

	# do not change
	version: 1
	]]>
</code-block></step>
</procedure>