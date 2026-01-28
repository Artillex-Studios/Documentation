# Configuration

<procedure title="config.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axpickaxes.html

	prefix: "<gradient:#0099FF:#00CCFF><b>AxPickaxes</b></gradient> &7» "

	database:
	  # currently only h2 is supported
	  type: "h2"
	  # don't touch these unless you know what they mean
	  pool:
		maximum-pool-size: 10
		minimum-idle: 10
		maximum-lifetime: 1800000
		keepalive-time: 0
		connection-timeout: 5000

	# how should blocks be reset?
	regenerator-mode:
	  # if disabled, crops won't be regenerated after they are broken
	  # this can be useful if you want to use vanilla random-tick-speed
	  enabled: true
	  # if enabled, blocks will be replaced using packets, which is more efficient
	  # if packet mode is enabled, the blocks won't actually be changed serverside
	  # enabling this will improve performance, however note that if enabled, blocks will regrow after a server restart
	  # and also blocks with a high respawn time (above 30 seconds) might desync if players teleport away and back quickly
	  packet: false
	  # only works if packet mode is enabled
	  # if enabled, if players break a block, it will only show for them and others can still break it
	  # this can be great if you have small farming zones with a lot of players
	  per-player: false

	drops:
	  # should drops be put right in the player's inventory?
	  to-inventory: true
	  # if the player's inventory is full, should extra items be dropped on the ground?
	  allow-overflow: false

	# when broken, what should replace blocks?
	# if false, ageable blocks will be visually set back to growth stage 1
	# if true, ageable blocks will be set to air
	# doesn't actually change the block regeneration method/time, this is purely for cosmetic reasons
	fully-remove-blocks: false

	# if false, all drops are normal items
	# if true, the plugin will add an NBT to block drops and prevents them from being crafted/placed
	# note that this isn't applied to previously generated drops, only to ones generated after this is changed
	prevent-drop-usage: false

	# should the block break event be cancelled when a player interacts with a block managed by axpickaxes?
	# for other plugins this will seem like the player didn't even break the block, this is useful to stop protection plugins from sending messages
	# without having to set up a zone for every block on the map, however it can also stop useful plugins from working (like stat trackers)
	# important: disabling this setting will make packet regenerator setting not work (because they rely on always cancelling the break event)
	cancel-break-event: true

	# how often should statistics be saved? (like blocks broken)
	# it will also be automatically saved when the player leaves
	auto-save-minutes: 3

	# used for auto sell
	# even if an enabled shop plugin in the hooks.yml would allow selling an item
	# if this is enabled, only drops from blocks will be sold (this is to prevent the players' items being sold)
	only-sell-drops: true

	# if enabled, the plugins will not allow players to break blocks outside their vision
	# every attempt at breaking an unreachable block will block breaking for 100 miliseconds (stacks up to 3 seconds)
	# this detection is not perfect, so there is a few blocks of leeway to prevent legit players from being delayed
	# some crazy mouse movements can make this falsely detect, however it shouldn't affect normal gameplay
	enable-anti-nuker: true

	# when prestiging a tool, should its statistics (blocks broken, essence gained, etc.) be also reset?
	# if disabled, only enchants, level and xp will be reset
	prestige-reset-tool-stats: false

	# if enabled, a level 1 pickaxe will be give to the player when they first join
	give-tool-on-first-join: true

	# if enabled, only the tool owner will be able to use the tool
	enforce-tool-ownership: false

	# if enabled, it won't be possible to throw/put away or lose your pickaxe
	# note that other plugins (for example auction house plugins) can still allow you to lose it
	bound-tool-to-inventory: true

	# should there be a confirmation message if somebody attempts to throw their tool out?
	drop-confirmation: true

	# the cooldown (in milliseconds) between successful /essence pay commands
	# note that this doesn't save between server restarts
	# set to -1 to disable
	pay-cooldown-millis: 10000

	# every how many milliseconds should we check to regenerate blocks?
	# this is not the regeneration time, decreasing this value will make regeneration smoother
	regeneration-check-millis: 500

	# by default the plugin collects farmed money/essence/xp, and it only gives it to players every X seconds to improve performance
	# this is how often does this collected money is actually given to the player
	# this setting can save a lot of server resources with some economy plugins
	currency-give-seconds: 1

	# how often should the tool item lores update?
	# setting this value too low could cause high ping
	lore-cache-milliseconds: 1000

	# if enabled, the auto sell prices will be cached for a few minutes
	# this improves performance with most shop plugins
	# however note that if you enable this, external price modifiers/boosts for the shop item prices will be ignored
	enable-global-price-caching: false

	# how should the action bar work?
	# modes:
	# 0 - shows the amount of currencies you have collected in a row without stopping
	# 1 - shows the currencies which you have collected in the previous second
	action-bar-mode: 0

	disenchanting:
	  # should the ability to remove custom tool enchantments be enabled?
	  enabled: true
	  # if enabled, how much of the enchant cost should be refunded in percentages? (0-100)
	  refund-percent: 70.0

	# command aliases for the /axpickaxes command
	main-command-aliases:
	  - axpickaxes
	  - axpickaxe
	  - pickaxes
	  - pickaxe

	# command aliases for the /axpickaxes essence command
	essence-commands:
	  - essence

	# command aliases for the /axpickaxes xp command
	player-xp-commands:
	  - level

	# command aliases for the /axpickaxes shop command
	shop-commands:
	  - essenceshop

	# how much xp is required to level up?
	# note: this is only used when the "player-xp-plugin" is set to "builtin" in the hooks.yml
	player-levelling:
	  # TYPES
	  # - formula (uses the given formula)
	  # - manual (set every level manually)
	  # note: levels start from 1
	  type: "formula"
	  formula: "%level% ^ 2 * 1000"
	  manual:
		1: "100"
		2: "500"
		3: "1500"
		4: "5000"
	  # level up rewards
	  rewards:
		# there is no level 1 reward as it is the default level
		# this is just an example of what can be done for other levels
		1:
		  # the message to send to the user (can be multiline)
		  message:
			- "&#AAFFAAYour rewards are: &#FFFFFF1500 essence and 1 Fancy Iron"
		  # you can add multiple commands, use %player% instead of the player's name
		  commands:
			- "essence give %player% 1500"
		  # you can add multiple items, all ItemBuilder (https://docs.artillex-studios.com/item-builder.html) options are supported
		  items:
			- material: IRON_INGOT
			  amount: 1
			  glow: true
			  name: "&#DDDDDDFancy Iron"

	leaderboard:
	  # how often should leaderboards be updated?
	  refresh-minutes: 3
	  # how many placements should be kept in ram? for example with 30 only the first 30 placement placeholders will work
	  loaded-placements: 30

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

	# format used for bar placeholders
	bar-placeholders:
	  length: 10
	  empty: "<color:#DDDDDD>■</color>"
	  full: "■"

	# should be plugin notify you if there is a new update?
	update-notifier:
	  # if enabled, it will display the message in the console
	  enabled: true
	  # if enabled, it will broadcast the update message to all players who have the <plugin-name>.update-notify permission
	  on-join: true

	# do not change this
	version: 1
	
    ]]>
</code-block></step>
</procedure>

<procedure title="ores.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axpickaxes.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	# list of worlds where the plugin should regenerate blocks
	# some supported regex: (optional)
	# - 'name' #  only 'name' is disallowed
	# - 'name*' #  disallows text starting with 'name'
	# - '*name' #  disallows text ending with 'name'
	# - '*name*' #  disallows text containing 'name'
	worlds:
	  - "*"

	# the block to put in place of the ore when broken
	# you can set this to air to disable this
	replacement-block: BEDROCK

	# how many drops should each fortune enchantment level give?
	# this is only used when the override-drops setting is enabled
	fortune:
	  # TYPES
	  # - formula (uses the given formula)
	  # - manual (set every level manually)
	  type: "formula"
	  formula: "0.2 + %level% * 0.8"
	  manual:
		1: "1"
		2: "2"
		3: "3"

	# list of blocks which are currently supported by the plugin
	# note: adding extra blocks to this is possible, however you must restart the server to prevent errors
	ores:
	  COAL_ORE:
		# the tool level required to break this block
		minimum-tool-level: 1
		# tool xp to give (can be a range like: 1-5)
		tool-xp: 3-7
		# player xp to give (can be a range like: 1-5)
		player-xp: 3-7
		# essence to give (can be a range like: 1-5)
		essence: 1-5
		# money to give (can be a range like: 1-5)
		# note: money is given when blocks are broken, to give money when selling, change the money in the drops section
		money: 0
		# how many milliseconds for the block to regrow?
		regenerate-millis: 10000
		# should the drops be handled by the plugin? if yes, the drops section below will be used
		# important: if you disable this, you will also have to set the cancel-break-event and only-sell-drops settings to false in the config
		override-drops: true
		# one of these drops will be picked, chances don't have to add up to 100%
		drops:
		  - chance: 90
			# sell price (can be a range like: 1-5)
			# this is only used when the "builtin" price plugin is enabled in the hooks.yml!
			sell-price: 5-10
			item:
			  amount: 1
			  material: COAL
			  name: "<#444444>Coal"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"
		  - chance: 10
			sell-price: 10
			item:
			  amount: 1
			  material: COAL_BLOCK
			  name: "<#444444>Coal Block"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"
	  COPPER_ORE:
		minimum-tool-level: 5
		tool-xp: 7-13
		player-xp: 7-13
		essence: 3-8
		money: 0
		regenerate-millis: 10000
		override-drops: true
		drops:
		  - chance: 100
			sell-price: 10-15
			item:
			  amount: 1
			  material: RAW_COPPER
			  name: "<#f68369>Raw Copper"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"
	  IRON_ORE:
		minimum-tool-level: 10
		tool-xp: 16-24
		player-xp: 16-24
		essence: 5-12
		money: 0
		regenerate-millis: 10000
		override-drops: true
		drops:
		  - chance: 100
			sell-price: 25-35
			item:
			  amount: 1
			  material: RAW_IRON
			  name: "<#e6c4ad>Raw Iron"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"
	  GOLD_ORE:
		minimum-tool-level: 15
		tool-xp: 40-50
		player-xp: 40-50
		essence: 10-18
		money: 0
		regenerate-millis: 10000
		override-drops: true
		drops:
		  - chance: 100
			sell-price: 40-55
			item:
			  amount: 1
			  material: RAW_GOLD
			  name: "<#f6a30e>Raw Gold"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"
	  LAPIS_ORE:
		minimum-tool-level: 20
		tool-xp: 72-88
		player-xp: 72-88
		essence: 15-25
		money: 0
		regenerate-millis: 10000
		override-drops: true
		drops:
		  - chance: 100
			sell-price: 70-85
			item:
			  amount: 1
			  material: LAPIS_LAZULI
			  name: "<#4470df>Lapis Lazuli"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"
	  REDSTONE_ORE:
		minimum-tool-level: 25
		tool-xp: 110-140
		player-xp: 110-140
		essence: 20-30
		money: 0
		regenerate-millis: 10000
		override-drops: true
		drops:
		  - chance: 100
			sell-price: 100-120
			item:
			  amount: 1
			  material: REDSTONE
			  name: "<#fb0000>Redstone"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"
	  DIAMOND_ORE:
		minimum-tool-level: 30
		tool-xp: 180-220
		player-xp: 180-220
		essence: 25-35
		money: 0
		regenerate-millis: 10000
		override-drops: true
		drops:
		  - chance: 100
			sell-price: 130-175
			item:
			  amount: 1
			  material: DIAMOND
			  name: "<#83fff7>Diamond"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"
	  EMERALD_ORE:
		minimum-tool-level: 35
		tool-xp: 290-340
		player-xp: 290-340
		essence: 30-40
		money: 0
		regenerate-millis: 10000
		override-drops: true
		drops:
		  - chance: 100
			sell-price: 200-250
			item:
			  amount: 1
			  material: EMERALD
			  name: "<#3fec80>Emerald"
			  lore:
				- "&#DDDDDDᴍᴀᴛᴇʀɪᴀʟ"

	# do not change this
	version: 1
	
    ]]>
</code-block></step>
</procedure>

<procedure title="hooks.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axpickaxes.html

	# what plugin to use?
	# used for calculating drop value
	# if multiple is enabled, the highest sell value will be used
	price-plugins:
	  # builtin is for using sell prices from the blocks.yml
	  builtin: true
	  # external plugins
	  ShopGUIPlus: false
	  Essentials: false
	  EconomyShopGUI: false
	  CMI: false

	# list of supported plugins: https://docs.artillex-studios.com/axpickaxes-supported-plugins.html#currency
	# what plugin should handle the money currency?
	money-plugin:
	  plugin: Vault
	  # this value is only used when the plugin supports multiple currencies
	  currency: ""

	# list of supported plugins: https://docs.artillex-studios.com/axpickaxes-supported-plugins.html#currency
	# what plugin should handle the essence currency?
	# axpickaxes comes with a builtin essence system
	essence-plugin:
	  plugin: builtin
	  # this value is only used when the plugin supports multiple currencies
	  currency: ""

	# list of supported plugins: https://docs.artillex-studios.com/axpickaxes-supported-plugins.html#player-xp
	# what plugin should handle the player xp?
	# axpickaxes comes with a builtin player xp system
	player-xp-plugin: builtin

	# do not change this
	version: 1
	
    ]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axpickaxes.html

	help:
	  - " "
	  - "<gradient:#0077FF:#00AAFF><b>AxPickaxes</b></gradient> <#55EEFF>Help"
	  - " <#55EEFF>➤ <white>/axpickaxes reload <#DDDDDD>| <#AAFFFF>Reload plugin"
	  - " <#55EEFF>➤ <white>/axpickaxes give <player> [level] <#DDDDDD>| <#AAFFFF>Give tool to player"
	  - " <#55EEFF>➤ <white>/axpickaxes tool setlevel <amount> <#DDDDDD>| <#AAFFFF>Set pickaxe level"
	  - " <#55EEFF>➤ <white>/axpickaxes tool setxp <amount> <#DDDDDD>| <#AAFFFF>Set pickaxe XP"
	  - " <#55EEFF>➤ <white>/axpickaxes tool setprestige <amount> <#DDDDDD>| <#AAFFFF>Set pickaxe prestiges"
	  - " <#55EEFF>➤ <white>/axpickaxes tool setowner <player> <#DDDDDD>| <#AAFFFF>Set pickaxe owner"
	  - " <#55EEFF>➤ <white>/axpickaxes leaderboard [player] <#DDDDDD>| <#AAFFFF>Open leaderboard menu"
	  - " <#55EEFF>➤ <white>/axpickaxes shop [player] <#DDDDDD>| <#AAFFFF>Open essence shop"
	  - " <#55EEFF>➤ <white>/axpickaxes reload <#DDDDDD>| <#AAFFFF>Reload configuration"
	  - " <#55EEFF>➤ <white>/axpickaxes essence view [player] <#DDDDDD>| <#AAFFFF>View essence"
	  - " <#55EEFF>➤ <white>/axpickaxes essence give/take/set/pay <player> <amount> <#DDDDDD>| <#AAFFFF>Modify essence"
	  - " <#55EEFF>➤ <white>/axpickaxes essence reset <player> <#DDDDDD>| <#AAFFFF>Reset essence"
	  - " <#55EEFF>➤ <white>/axpickaxes xp view [player] <#DDDDDD>| <#AAFFFF>View player XP"
	  - " <#55EEFF>➤ <white>/axpickaxes xp givelevel/givexp <player> <amount or X%> <#DDDDDD>| <#AAFFFF>Give player level/XP"
	  - " <#55EEFF>➤ <white>/axpickaxes xp takelevel/takexp <player> <amount> <#DDDDDD>| <#AAFFFF>Take player level/XP"
	  - " <#55EEFF>➤ <white>/axpickaxes xp setlevel/setxp <player> <amount> <#DDDDDD>| <#AAFFFF>Set player level/XP"
	  - " <#55EEFF>➤ <white>/axpickaxes xp reset <player> <#DDDDDD>| <#AAFFFF>Reset player XP"
	  - " <#55EEFF>➤ <white>/axpickaxes event start <#DDDDDD>| <#AAFFFF>Start miner event"
	  - " <#55EEFF>➤ <white>/axpickaxes event stop <#DDDDDD>| <#AAFFFF>Stop miner event"
	  - " "

	action-bar: "&#00AAFF%last_money_gained% &#AAFFFFmoney &#0077FF| &#00AAFF%last_essence_gained% &#AAFFFFessence &#0077FF| &#00AAFF%last_tool_xp_gained% &#AAFFFFtool XP &#0077FF| &#00AAFF%last_player_xp_gained% &#AAFFFFplayer XP"

	inventory-full:
	  title: "&#FF4400⚠ &#FF0000Inventory Full &#FF4400⚠"
	  subtitle: "&#FFAAAASell drops to make space!"

	tool:
	  level-up: "&#00FF00Level Up! Your tool has reached level &#FFFFFF%level%&#00FF00!"
	  low-level: "&#FF0000A level &#FFFFFF%required-level% &#FF0000tool is required for this block! Your tool is only level &#FFFFFF%tool-level%&#FF0000."
	  not-tool: "&#FF0000You must hold a pickaxe in your hand!"
	  not-your-tool: "&#FF0000You can't use this pickaxe, because it is not yours!"
	  set-level: "&#00FF00You have successfully set the pickaxe's level to &#FFFFFF%level%&#00FF00!"
	  set-xp: "&#00FF00You have successfully set the pickaxe's XP to &#FFFFFF%amount%&#00FF00!"
	  set-prestiges: "&#00FF00You have successfully set the pickaxe's prestiges to &#FFFFFF%amount%&#00FF00!"
	  set-owner: "&#00FF00You have successfully made &#FFFFFF%player% &#00FF00the new owner of this tool!"
	  keep-in-inventory: "&#FF0000You must always keep the tool in your inventory."
	  drop-confirm: "&#FF0000Please press the drop button again if you want to throw your tool out."

	essence:
	  balance: "&#00FF00You have &#FFFFFF%amount% &#00FF00essence!"
	  balance-other: "&#FFFFFF%player% &#00FF00has &#FFFFFF%amount% &#00FF00essence!"
	  give: "&#00FF00You have given &#FFFFFF%amount% &#00FF00essence to &#FFFFFF%player%&#00FF00!"
	  take: "&#00FF00You have taken &#FFFFFF%amount% &#00FF00essence from &#FFFFFF%player%&#00FF00!"
	  set: "&#00FF00You have set the essences of &#FFFFFF%player% &#00FF00to &#FFFFFF%amount%&#00FF00!"
	  pay-not-enough: "&#FF0000You don't have &#FFFFFF%amount% &#FF0000essence!"
	  pay-success: "&#00FF00You have successfully paid &#FFFFFF%amount% &#00FF00essence to &#FFFFFF%player%&#00FF00!"
	  pay-received: "&#00FF00You have received &#FFFFFF%amount% &#00FF00essence from &#FFFFFF%player%&#00FF00!"
	  pay-self: "&#FF0000You can't send essence to yourself!"
	  pay-cooldown: "&#FF0000You must wait another &#FFFFFF%time% &#FF0000seconds before sending essence again!"

	player-xp:
	  balance: "&#00FF00You are level &#FFFFFF%level% &#00FF00and you need &#FFFFFF%amount% &#00FF00xp to level up!"
	  balance-other: "&#FFFFFF%player% &#00FF00is level &#FFFFFF%level% &#00FF00and needs &#FFFFFF%amount% &#00FF00xp to level up!"
	  give-xp: "&#00FF00You have given &#FFFFFF%amount% &#00FF00player XP to &#FFFFFF%player%&#00FF00!"
	  take-xp: "&#00FF00You have taken &#FFFFFF%amount% &#00FF00player XP from &#FFFFFF%player%&#00FF00!"
	  set-xp: "&#00FF00You have set the player xp of &#FFFFFF%player% &#00FF00to &#FFFFFF%amount%&#00FF00!"
	  give-level: "&#00FF00You have given &#FFFFFF%amount% &#00FF00player levels to &#FFFFFF%player%&#00FF00!"
	  take-level: "&#00FF00You have taken &#FFFFFF%amount% &#00FF00player levels from &#FFFFFF%player%&#00FF00!"
	  set-level: "&#00FF00You have set the player level of &#FFFFFF%player% &#00FF00to &#FFFFFF%amount%&#00FF00!"
	  level-up: "&#00FF00Level Up! Your player level has reached level &#FFFFFF%level%&#00FF00!"

	shop:
	  purchased: "&#00FF00You have purchased &#FFFFFF%name% &#00FF00for &#FFFFFF%amount% &#00FF00essence!"
	  no-essence: "&#FF0000You can't purchase this item, because you don't have enough essence. You need &#FFFFFF%amount%&#FF0000!"

	enchant:
	  no-essence: "&#FF0000You can't purchase this enchant, because you don't have enough essence. You need &#FFFFFF%amount%&#FF0000!"
	  no-permission: "&#FF0000You don't have permission to purchase this enchant!"
	  maxed: "&#FF0000You have reached the maximum level of the &#FFFFFF%enchant% &#FF0000enchant!"
	  success: "&#00FF00The %enchant% &#00FF00enchant has been successfully purchased!"
	  disenchant: "&#00FF00You have successfully refunded &#FFFFFF%levels% &#00FF00enchant levels and got &#FFFFFF%amount% &#00FF00essence!"
	  no-enchant: "&#FF0000You can't refund this enchant, because the level is too low!"
	  low-player-level: "&#FF0000Your player level must be at least &#FFFFFF%level% &#FF0000to purchase the &#FFFFFF%enchant% &#FF0000enchant!"
	  low-tool-level: "&#FF0000Your tool level must be at least &#FFFFFF%level% &#FF0000to purchase the &#FFFFFF%enchant% &#FF0000enchant!"
	  # this will be used for the %enchants% placeholder, repeated for all enchants
	  lore:
		enchant: " <#555555>❙ <#FFFFFF>%enchant-name%<br>"
		none: " <#555555>❙ <#FFFFFF>No enchantments"
	  placeholder:
		enabled: "&#00FF00enabled"
		disabled: "&#FF0000disabled"
	  enabled: "&#00FF00The %enchant% &#00FF00enchant has been enabled!"
	  disabled: "&#FF0000The %enchant% &#FF0000enchant has been disabled!"

	prestige:
	  no-essence: "&#FF0000You can't prestige, because you don't have enough essence. You need &#FFFFFF%amount% &#FF0000essence!"
	  no-money: "&#FF0000You can't prestige, because you don't have enough money. You need &#FFFFFF%amount% &#FF0000money!"
	  no-level: "&#FF0000You can't prestige, because you don't have enough tool levels. You need level &#FFFFFF%amount%&#FF0000!"
	  maxed: "&#FF0000You have reached the maximum prestige level!"
	  success: "&#00FF00You have successfully prestiged your tool to level &#FFFFFF%prestige%&#00FF00!"

	event:
	  start:
		- " "
		- "&#00FFFF⭐ &#00AAFF&lMiner Event &#00FFFF⭐"
		- "&#00DDFFThe event has started! The players who break the most ores will be rewarded! &#00FFFFEnds in &#FFFFFF%event_time_left%&#00FFFF."
		- " "
	  end:
		- " "
		- "&#00FFFF⭐ &#00AAFF&lMiner Event &#00FFFF⭐"
		- "&#00DDFFThe event has ended! The top collectors were:"
		- " &#DDDDDD- &#FF00001# %event_top_1_name% - %event_top_1_value%"
		- " &#DDDDDD- &#00AAFF2# %event_top_2_name% - %event_top_2_value%"
		- " &#DDDDDD- &#00FFFF3# %event_top_3_name% - %event_top_3_value%"
		- " "
		- "&#00FFFFPlayers have broken a total of &#FFFFFF%event_statistic% &#00FFFFores."
		- " "
	  progress:
		- " "
		- "&#00FFFF⭐ &#00AAFF&lMiner Event &#00FFFF⭐"
		- "&#00DDFFThe event is still active! The current leaderboard:"
		- " &#DDDDDD- &#00FFFF1# %event_top_1_name% - %event_top_1_value%"
		- " &#DDDDDD- &#00FFFF2# %event_top_2_name% - %event_top_2_value%"
		- " &#DDDDDD- &#00FFFF3# %event_top_3_name% - %event_top_3_value%"
		- " "
		- "&#00FFFFThe event will end in &#FFFFFF%event_time_left%&#00FFFF."
		- " "
	  not-enough-players:
		- " "
		- "&#00FFFF⭐ &#00AAFF&lMiner Event &#00FFFF⭐"
		- "&#00DDFFThe event will not start, because there are too few players online!"
		- " "
	  stop:
		- " "
		- "&#00FFFF⭐ &#00AAFF&lMiner Event &#00FFFF⭐"
		- "&#00DDFFThe event has been stopped by an admin!"
		- " "
	  started: "&#00FF00You have successfully started the miner event!"
	  stopped: "&#FF0000You have successfully stopped the miner event!"
	  running: "&#FF0000The miner event is already running!"
	  inactive: "&#FF0000The miner event is not running!"

	reload:
	  success: "&#33FF33Plugin successfully reloaded!"
	  failed: "&#FF3333Failed to reload the plugin! Something is wrong in the &f%file%&#FF3333 file, look in the console or use a yaml validator to fix the errors!"

	commands:
	  invalid-value: "&#FF0000Invalid parameter: &#BB0000%value%"
	  invalid-command: "&#FF0000Invalid command or subcommand!"
	  missing-argument: "&#FF0000Missing argument! You must specify a value for &#BB0000%value%&#FF0000."
	  no-permission: "&#FF0000You don't have permission to access this command!"
	  out-of-range: "&#FF0000The &#BB0000%number% &#FF0000must be between &#BB0000%min% &#FF0000and &#BB0000%max%&#FF0000!"
	  player-only: "&#FF0000You must be a player to use this command!"
	  invalid-player: "&#FF0000The player &#BB0000%player% &#FF0000can not be found!"
	  invalid-selector: "&#FF0000You can not use this selector in this command!"

	update-notifier: "&#00AAFFThere is a new version of AxPickaxes available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"

	# do not change this
	version: 1
	
    ]]>
</code-block></step>
</procedure>

<procedure title="shop.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axhoes.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	# format:
	# | pages:
	# | 1: - page number (starts at 1)
	# |     10: - slot in gui (starts at 0)
	pages:
	  1:
		# ITEM EXAMPLE
		10:
		  # the cost of the item
		  price: 1000
		  # the items to give when purchased
		  items:
			- material: DIAMOND
			  amount: 1
			  name: "&#00FFFFShiny diamond"
			  glow: true
		  # the item to display
		  display:
			amount: 1
			material: DIAMOND
			glow: true
			name: "&#00FFFFShiny diamond"
			lore:
			  - ""
			  - "&#FF7700&lClick &l> &#FFCC00Purchase for &#FFFFFF%price% &#FFCC00essence!"
		# COMMAND EXAMPLE
		11:
		  # the cost of the item
		  price: 1000
		  # these commands will be run when somebody purchases this
		  commands:
			- "say Welcome %player%!"
		  # the item to display
		  display:
			amount: 1
			material: BOOK
			name: "&#FFFF00A warm welcome message"
			lore:
			  - ""
			  - "&#FF7700&lClick &l> &#FFCC00Purchase for &#FFFFFF%price% &#FFCC00essence!"

	# do not change this
	version: 1
	
    ]]>
</code-block></step>
</procedure>

<procedure title="tool.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[

	# DOCUMENTATION: https://docs.artillex-studios.com/axpickaxes.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html
	# note: upgrades are currently is only for customizing the pickaxe item (+ to unlock new blocks)

	xp-calculation:
	  # TYPES
	  # - formula (uses the given formula to calculate xp needed for a level)
	  # - manual (you can configure the xp needed for levels yourself one-by-one)
	  # note: levels start from 1
	  type: "formula"
	  formula: "%level% ^ 2 * 1000"
	  manual:
		1: "100"
		2: "500"
		3: "1500"
		4: "5000"

	# the list of levels (you can configure any amount of levels)
	# make sure that you set a price for all levels if you are using manual price-calculation
	# note: the higher levels will override the lower ones, so for example if you want the level 50 tool
	# to have a custom model data, you only need to set that value and the rest will be used from the lower levels
	upgrades:
	  # level 1 (DEFAULT LEVEL)
	  1:
		material: WOODEN_PICKAXE
		name: "&#0099FF&lᴘɪᴄᴋᴀxᴇ"
		glow: true
		lore:
		  - ""
		  - "<#0099FF><b>></b> <#44CCFF>Level: <#0099FF>%tool-level%"
		  - "<#0099FF><b>></b> <#44CCFF>Progress: <#0099FF>%tool-progress-bar% &#DDDDDD(%tool-progress-percentage%%)"
		  - ""
		  - "<#0099FF>ɪɴꜰᴏʀᴍᴀᴛɪᴏɴ"
		  - " <#555555>❙ <#FFFFFF>Owner: <#0099FF>%owner%"
		  - " <#555555>❙ <#FFFFFF>Prestiges: <#0099FF>%prestiges%"
		  - ""
		  - "<#0099FF>ꜱᴛᴀᴛꜱ"
		  - " <#555555>❙ <#FFFFFF>Ores: <#0099FF>%broken-blocks% <#44CCFF>broken"
		  - " <#555555>❙ <#FFFFFF>Money: <#0099FF>$%collected-money% <#44CCFF>collected"
		  - " <#555555>❙ <#FFFFFF>Essence: <#0099FF>%collected-essence% <#44CCFF>collected"
		  - ""
		  - "<#0099FF>ᴇɴᴄʜᴀɴᴛꜱ"
		  - "%enchants%" # go to the lang.yml -> enchant -> lore to customize this
		  - ""
		  - "<#0099FF><b>></b> <#44CCFF>Break blocks to level up."
	  # level 2
	  3:
		material: STONE_PICKAXE
	  5:
		material: IRON_PICKAXE
	  10:
		material: GOLDEN_PICKAXE
	  15:
		material: DIAMOND_PICKAXE
	  20:
		material: NETHERITE_PICKAXE

	# after reaching a certain tool level, tools can be prestiged, permanently increasing the gained resources
	# prestige resets tool XP, level, enchants
	prestige:
	  # the maximum possible prestige level
	  max-prestige: 100
	  # minimum level/money/essence required to prestige
	  required:
		level:
		  # TYPES
		  # - formula (uses the given formula)
		  # - manual (set every level manually)
		  # note: by default the player has 0 prestiges
		  type: "formula"
		  formula: "%prestige% * 5 + 30"
		  manual:
			1: "30"
			2: "35"
			3: "40"
			4: "45"
			5: "50"
		money:
		  type: "manual"
		  manual:
			1: "0"
		essence:
		  type: "formula"
		  formula: "%prestige% ^ 2 * 1000000"
	  # the statistics which will be boosted when prestiging
	  essence-boost:
		type: "formula"
		formula: "%prestige% * 0.1 + 1"
	  money-boost:
		type: "formula"
		formula: "%prestige% * 0.1 + 1"
	  tool-xp-boost:
		type: "formula"
		formula: "%prestige% * 0.1 + 1"
	  player-xp-boost:
		type: "formula"
		formula: "%prestige% * 0.1 + 1"
	  drop-boost:
		type: "formula"
		formula: "%prestige% * 0.1 + 1"

	# do not change this
	version: 1
	
    ]]>
</code-block></step>
</procedure>

Example gui configuration: (there are 7 gui files that come with the plugin)
<procedure title="guis/main-gui.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axpickaxes.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	title: "&0ᴘɪᴄᴋᴀxᴇ"
	# a gui can have 1-6 rows
	rows: 5

	# ----- ITEMS -----

	border-decoration:
	  material: "BLUE_STAINED_GLASS_PANE"
	  slot: "border"
	  name: " "

	stats:
	  slot: 20
	  material: "BOOK"
	  name: "&#0099FF&lᴛᴏᴏʟ ꜱᴛᴀᴛɪꜱᴛɪᴄꜱ"
	  lore:
		- " "
		- "<#0099FF>ɢᴇɴᴇʀᴀʟ"
		- " <#555555>❙ <#FFFFFF>Level: <#0099FF>%tool-level%"
		- " <#555555>❙ <#FFFFFF>Progress: <#0099FF>%tool-progress-bar% &#DDDDDD(%tool-progress-percentage%%)"
		- " <#555555>❙ <#FFFFFF>Prestiges: <#0099FF>%prestiges%"
		- " <#555555>❙ <#FFFFFF>Ores: <#0099FF>%broken-blocks% <#44CCFF>broken"
		- " <#555555>❙ <#FFFFFF>Money: <#0099FF>$%collected-money% <#44CCFF>collected"
		- " <#555555>❙ <#FFFFFF>Essence: <#0099FF>%collected-essence% <#44CCFF>collected"
		- " "
		- "<#0099FF>ᴄʀᴏᴘꜱ"
		- " <#555555>❙ <#444444>Coal Ore: <#0099FF>%broken-coalore% <#44CCFF>broken"
		- " <#555555>❙ <#f68369>Copper Ore: <#0099FF>%broken-copperore% <#44CCFF>broken"
		- " <#555555>❙ <#e6c4ad>Iron Ore: <#0099FF>%broken-ironore% <#44CCFF>broken"
		- " <#555555>❙ <#f6a30e>Gold Ore: <#0099FF>%broken-goldore% <#44CCFF>broken"
		- " <#555555>❙ <#4470df>Lapis Ore: <#0099FF>%broken-lapisore% <#44CCFF>broken"
		- " <#555555>❙ <#fb0000>Redstone Ore: <#0099FF>%broken-redstoneore% <#44CCFF>broken"
		- " <#555555>❙ <#83fff7>Diamond Ore: <#0099FF>%broken-diamondore% <#44CCFF>broken"
		- " <#555555>❙ <#3fec80>Emerald Ore: <#0099FF>%broken-emeraldore% <#44CCFF>broken"
		- " "

	enchants:
	  slot: 13
	  material: "ENCHANTED_BOOK"
	  name: "&#0099FF&lᴛᴏᴏʟ ᴇɴᴄʜᴀɴᴛᴍᴇɴᴛꜱ"
	  lore:
		- " "
		- "<#0099FF>ᴇɴᴄʜᴀɴᴛꜱ"
		- "%enchants%" # go to the lang.yml -> enchant -> lore to customize this
		- ""
		- "&#0099FF&lClick &l> &#00CCFFView enchantments"
	  actions:
		- "[MENU] enchant"
		- "[SOUND] ui.button.click|1|1"

	leaderboards:
	  slot: 24
	  material: "GOLD_INGOT"
	  name: "&#0099FF&lʟᴇᴀᴅᴇʀʙᴏᴀʀᴅꜱ"
	  lore:
		- " "
		- "&#0099FF&lClick &l> &#00CCFFView leaderboards"
	  actions:
		- "[MENU] leaderboards"
		- "[SOUND] ui.button.click|1|1"

	prestige:
	  slot: 31
	  material: "BEACON"
	  name: "&#0099FF&lᴘʀᴇꜱᴛɪɢᴇ"
	  lore:
		- " "
		- "<#0099FF><b>></b> <#44CCFF>Prestiges: <#0099FF>%prestiges%"
		- " "
		- "&#0099FF&lClick &l> &#00CCFFGo to prestige menu"
	  actions:
		- "[MENU] prestige"
		- "[SOUND] ui.button.click|1|1"
	
    ]]>
</code-block></step>
</procedure>

Example enchant file, the default configuration comes with more than a dozen premade enchants. You can always create more.
<procedure title="enchants/speed-effect.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axpickaxes.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	# should the enchantment be enabled?
	enabled: true

	name: "&#00CCFFSpeed &#00FFFF%level%"
	# what type of enchantment is this? check the wiki for the list
	type: "give_effect"
	# the enchant's max possible level
	max-level: 100
	# optional, required levels to be able to upgrade this enchant
	required-player-level: 0
	required-tool-level: 0
	# optional, what permission is required to upgrade this enchant?
	required-permission: ""
	# should the enchant get reset when the tool is prestiged?
	reset-on-prestige: true

	# the amount of essence required to upgrade the enchantment
	price:
	  # TYPES
	  # - formula (uses the given formula)
	  # - manual (set every level manually)
	  # note: levels start from 0
	  type: "formula"
	  formula: "%level% ^ 2 * 10000"
	  manual:
		1: "100"
		2: "500"
		3: "1500"
		4: "5000"

	# chance for this enchantment to trigger when a block is broken (0-100%)
	chance:
	  # TYPES
	  # - formula (uses the given formula)
	  # - manual (set every level manually)
	  # note: levels start from 1
	  type: "formula"
	  formula: "%level%"
	  manual:
		1: "200"
		2: "500"
		3: "800"
		4: "1200"

	# levelling up changes the effects given
	# list of potion effect types: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html
	# format: <type>:<strength starting at 1>:<time in seconds>
	effect:
	  1:
		- "SPEED:1:5"
	  25:
		- "SPEED:2:5"
	  50:
		- "SPEED:3:5"
	  75:
		- "SPEED:4:5"
	  100:
		- "SPEED:5:5"
	
    ]]>
</code-block></step>
</procedure>