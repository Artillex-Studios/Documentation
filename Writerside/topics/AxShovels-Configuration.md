# Configuration

<procedure title="config.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axshovels.html

	prefix: "<gradient:#AA3300:#FF7700><b>AxShovels</b></gradient> &7» "

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
	  # if disabled, broken blocks won't be regenerated after they are broken
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

	# should the block break event be cancelled when a player interacts with an block managed by axshovels?
	# for other plugins this will seem like the player didn't even break the block, this is useful to stop protection plugins from sending messages
	# without having to set up a zone for every block block on the map, however it can also stop useful plugins from working (like stat trackers)
	# disabling this will enable the "fully-remove-blocks" and the "override-drops" settings
	# important: disabling this setting will make packet regenerator setting not work (because they rely on always cancelling the break event)
	cancel-break-event: true

	# how often should statistics be saved? (like blocks broken)
	# it will also be automatically saved when the player leaves
	auto-save-minutes: 3

	# used for auto sell
	# even if an enabled shop plugin in the hooks.yml would allow selling an item
	# if this is enabled, only drops from blocks will be sold (this is to prevent the players' items being sold)
	# incompatible with override-drops being disabled in the crops.yml
	only-sell-drops: true

	# if enabled, the plugins will not allow players to break blocks outside their vision
	# every attempt at breaking an unreachable block will block breaking for 100 milliseconds (stacks up to 3 seconds)
	# this detection is not perfect, so there is a few blocks of leeway to prevent legit players from being delayed
	# some crazy mouse movements can make this falsely detect, however it shouldn't affect normal gameplay
	enable-anti-nuker: true

	# when prestiging a tool, should its statistics (blocks broken, essence gained, etc.) be also reset?
	# if disabled, only enchants, level and xp will be reset
	prestige-reset-tool-stats: false

	# if enabled, a level 1 shovel will be give to the player when they first join
	give-tool-on-first-join: true

	# if enabled, only the tool owner will be able to use the tool
	enforce-tool-ownership: false

	# if enabled, it won't be possible to throw/put away or lose your shovel
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

	# how often should the tool item lblocks update?
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

	# tool enchants that give some currency (like give_essence or give_money) spawn a hologram for a second when they trigger
	# if you disable this setting, it removes this functionality from all enchants (the currency will still be given)
	enable-drop-holograms: true

	disenchanting:
	  # should the ability to remove custom tool enchantments be enabled?
	  enabled: true
	  # if enabled, how much of the enchant cost should be refunded in percentages? (0-100)
	  refund-percent: 70.0

	# command aliases for the /axshovels command
	main-command-aliases:
	  - axshovels
	  - axshovel
	  - shovels
	  - shovel

	# command aliases for the /axshovels essence command
	essence-commands:
	  - essence

	# command aliases for the /axshovels xp command
	player-xp-commands:
	  - level

	# command aliases for the /axshovels shop command
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

<procedure title="blocks.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axshovels.html

	prefix: "<gradient:#AA3300:#FF7700><b>AxShovels</b></gradient> &7» "

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
	  # if disabled, broken blocks won't be regenerated after they are broken
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

	# should the block break event be cancelled when a player interacts with an block managed by axshovels?
	# for other plugins this will seem like the player didn't even break the block, this is useful to stop protection plugins from sending messages
	# without having to set up a zone for every block block on the map, however it can also stop useful plugins from working (like stat trackers)
	# disabling this will enable the "fully-remove-blocks" and the "override-drops" settings
	# important: disabling this setting will make packet regenerator setting not work (because they rely on always cancelling the break event)
	cancel-break-event: true

	# how often should statistics be saved? (like blocks broken)
	# it will also be automatically saved when the player leaves
	auto-save-minutes: 3

	# used for auto sell
	# even if an enabled shop plugin in the hooks.yml would allow selling an item
	# if this is enabled, only drops from blocks will be sold (this is to prevent the players' items being sold)
	# incompatible with override-drops being disabled in the crops.yml
	only-sell-drops: true

	# if enabled, the plugins will not allow players to break blocks outside their vision
	# every attempt at breaking an unreachable block will block breaking for 100 milliseconds (stacks up to 3 seconds)
	# this detection is not perfect, so there is a few blocks of leeway to prevent legit players from being delayed
	# some crazy mouse movements can make this falsely detect, however it shouldn't affect normal gameplay
	enable-anti-nuker: true

	# when prestiging a tool, should its statistics (blocks broken, essence gained, etc.) be also reset?
	# if disabled, only enchants, level and xp will be reset
	prestige-reset-tool-stats: false

	# if enabled, a level 1 shovel will be give to the player when they first join
	give-tool-on-first-join: true

	# if enabled, only the tool owner will be able to use the tool
	enforce-tool-ownership: false

	# if enabled, it won't be possible to throw/put away or lose your shovel
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

	# how often should the tool item lblocks update?
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

	# tool enchants that give some currency (like give_essence or give_money) spawn a hologram for a second when they trigger
	# if you disable this setting, it removes this functionality from all enchants (the currency will still be given)
	enable-drop-holograms: true

	disenchanting:
	  # should the ability to remove custom tool enchantments be enabled?
	  enabled: true
	  # if enabled, how much of the enchant cost should be refunded in percentages? (0-100)
	  refund-percent: 70.0

	# command aliases for the /axshovels command
	main-command-aliases:
	  - axshovels
	  - axshovel
	  - shovels
	  - shovel

	# command aliases for the /axshovels essence command
	essence-commands:
	  - essence

	# command aliases for the /axshovels xp command
	player-xp-commands:
	  - level

	# command aliases for the /axshovels shop command
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

<procedure title="hooks.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axshovels.html

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

	# list of supported plugins: https://docs.artillex-studios.com/axshovels-supported-plugins.html#currency
	# what plugin should handle the money currency?
	money-plugin:
	  plugin: Vault
	  # this value is only used when the plugin supports multiple currencies
	  currency: ""

	# list of supported plugins: https://docs.artillex-studios.com/axshovels-supported-plugins.html#currency
	# what plugin should handle the essence currency?
	# axshovels comes with a builtin essence system
	essence-plugin:
	  plugin: builtin
	  # this value is only used when the plugin supports multiple currencies
	  currency: ""

	# list of supported plugins: https://docs.artillex-studios.com/axshovels-supported-plugins.html#player-xp
	# what plugin should handle the player xp?
	# axshovels comes with a builtin player xp system
	player-xp-plugin: builtin

	# do not change this
	version: 1
	
    ]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axshovels.html

	help:
	  - " "
	  - "<gradient:#AA3300:#FF7700><b>AxShovels</b></gradient> <#FFAA44>Help"
	  - " <#FFAA44>➤ <white>/axshovels reload <#DDDDDD>| <#FFAA88>Reload plugin"
	  - " <#FFAA44>➤ <white>/axshovels give <player> [level] <#DDDDDD>| <#FFAA88>Give tool to player"
	  - " <#FFAA44>➤ <white>/axshovels tool setlevel <amount> <#DDDDDD>| <#FFAA88>Set shovel level"
	  - " <#FFAA44>➤ <white>/axshovels tool setxp <amount> <#DDDDDD>| <#FFAA88>Set shovel XP"
	  - " <#FFAA44>➤ <white>/axshovels tool setprestige <amount> <#DDDDDD>| <#FFAA88>Set shovel prestiges"
	  - " <#FFAA44>➤ <white>/axshovels tool setowner <player> <#DDDDDD>| <#FFAA88>Set shovel owner"
	  - " <#FFAA44>➤ <white>/axshovels leaderboard [player] <#DDDDDD>| <#FFAA88>Open leaderboard menu"
	  - " <#FFAA44>➤ <white>/axshovels shop [player] <#DDDDDD>| <#FFAA88>Open essence shop"
	  - " <#FFAA44>➤ <white>/axshovels reload <#DDDDDD>| <#FFAA88>Reload configuration"
	  - " <#FFAA44>➤ <white>/axshovels essence view [player] <#DDDDDD>| <#FFAA88>View essence"
	  - " <#FFAA44>➤ <white>/axshovels essence give/take/set/pay <player> <amount> <#DDDDDD>| <#FFAA88>Modify essence"
	  - " <#FFAA44>➤ <white>/axshovels essence reset <player> <#DDDDDD>| <#FFAA88>Reset essence"
	  - " <#FFAA44>➤ <white>/axshovels xp view [player] <#DDDDDD>| <#FFAA88>View player XP"
	  - " <#FFAA44>➤ <white>/axshovels xp givelevel/givexp <player> <amount or X%> <#DDDDDD>| <#FFAA88>Give player level/XP"
	  - " <#FFAA44>➤ <white>/axshovels xp takelevel/takexp <player> <amount> <#DDDDDD>| <#FFAA88>Take player level/XP"
	  - " <#FFAA44>➤ <white>/axshovels xp setlevel/setxp <player> <amount> <#DDDDDD>| <#FFAA88>Set player level/XP"
	  - " <#FFAA44>➤ <white>/axshovels xp reset <player> <#DDDDDD>| <#FFAA88>Reset player XP"
	  - " <#FFAA44>➤ <white>/axshovels event start <#DDDDDD>| <#FFAA88>Start digging event"
	  - " <#FFAA44>➤ <white>/axshovels event stop <#DDDDDD>| <#FFAA88>Stop digging event"
	  - " "

	action-bar: "&#AA3300%last_money_gained% &#FFAA88money &#D55500| &#AA3300%last_essence_gained% &#FFAA88essence &#D55500| &#AA3300%last_tool_xp_gained% &#FFAA88tool XP &#D55500| &#AA3300%last_player_xp_gained% &#FFAA88player XP"

	inventory-full:
	  title: "&#FF4400⚠ &#FF0000Inventory Full &#FF4400⚠"
	  subtitle: "&#FFAAAASell drops to make space!"

	tool:
	  level-up: "&#00FF00Level Up! Your tool has reached level &#FFFFFF%level%&#00FF00!"
	  low-level: "&#FF0000A level &#FFFFFF%required-level% &#FF0000tool is required for this block! Your tool is only level &#FFFFFF%tool-level%&#FF0000."
	  not-tool: "&#FF0000You must hold a shovel in your hand!"
	  not-your-tool: "&#FF0000You can't use this shovel, because it is not yours!"
	  set-level: "&#00FF00You have successfully set the shovel's level to &#FFFFFF%level%&#00FF00!"
	  set-xp: "&#00FF00You have successfully set the shovel's XP to &#FFFFFF%amount%&#00FF00!"
	  set-prestiges: "&#00FF00You have successfully set the shovel's prestiges to &#FFFFFF%amount%&#00FF00!"
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
		- "&#AA3300⭐ &#D55500&lDigging Event &#AA3300⭐"
		- "&#FFAA88The event has started! The players who break the most blocks will be rewarded! &#AA3300Ends in &#FFFFFF%event_time_left%&#AA3300."
		- " "
	  end:
		- " "
		- "&#AA3300⭐ &#D55500&lDigging Event &#AA3300⭐"
		- "&#FFAA88The event has ended! The top collectors were:"
		- " &#DDDDDD- &#FF00001# %event_top_1_name% - %event_top_1_value%"
		- " &#DDDDDD- &#AA33002# %event_top_2_name% - %event_top_2_value%"
		- " &#DDDDDD- &#AA33003# %event_top_3_name% - %event_top_3_value%"
		- " "
		- "&#AA3300Players have broken a total of &#FFFFFF%event_statistic% &#AA3300blocks."
		- " "
	  progress:
		- " "
		- "&#AA3300⭐ &#D55500&lDigging Event &#AA3300⭐"
		- "&#FFAA88The event is still active! The current leaderboard:"
		- " &#DDDDDD- &#AA33001# %event_top_1_name% - %event_top_1_value%"
		- " &#DDDDDD- &#AA33002# %event_top_2_name% - %event_top_2_value%"
		- " &#DDDDDD- &#AA33003# %event_top_3_name% - %event_top_3_value%"
		- " "
		- "&#FFAA88The event will end in &#FFFFFF%event_time_left%&#FFAA88."
		- " "
	  not-enough-players:
		- " "
		- "&#AA3300⭐ &#D55500&lDigging Event &#AA3300⭐"
		- "&#FFAA88The event will not start, because there are too few players online!"
		- " "
	  stop:
		- " "
		- "&#AA3300⭐ &#D55500&lDigging Event &#AA3300⭐"
		- "&#FFAA88The event has been stopped by an admin!"
		- " "
	  started: "&#00FF00You have successfully started the digging event!"
	  stopped: "&#FF0000You have successfully stopped the digging event!"
	  running: "&#FF0000The digging event is already running!"
	  inactive: "&#FF0000The digging event is not running!"

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

	update-notifier: "&#AA3300There is a new version of AxShovels available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"

# do not change this
version: 1
	
    ]]>
</code-block></step>
</procedure>

<procedure title="shop.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axshovels.html
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
			  name: "&#AA3300Shiny diamond"
			  glow: true
		  # the item to display
		  display:
			amount: 1
			material: DIAMOND
			glow: true
			name: "&#AA3300Shiny diamond"
			lore:
			  - ""
			  - "&#AA3300&lClick &l> &#FF7700Purchase for &#FFFFFF%price% &#FF7700essence!"
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
			name: "&#AA3300A warm welcome message"
			lore:
			  - ""
			  - "&#AA3300&lClick &l> &#FF7700Purchase for &#FFFFFF%price% &#FF7700essence!"

	# do not change this
	version: 1
	
    ]]>
</code-block></step>
</procedure>

<procedure title="tool.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[

	# DOCUMENTATION: https://docs.artillex-studios.com/axshovels.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html
	# note: upgrades are currently is only for customizing the shovel item (+ to unlock new blocks)

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
		material: WOODEN_SHOVEL
		name: "&#AA3300&lꜱʜᴏᴠᴇʟ"
		glow: true
		lore:
		  - ""
		  - "<#AA3300><b>></b> <#FFAA88>Level: <#AA3300>%tool-level%"
		  - "<#AA3300><b>></b> <#FFAA88>Progress: <#AA3300>%tool-progress-bar% &#DDDDDD(%tool-progress-percentage%%)"
		  - ""
		  - "<#AA3300>ɪɴꜰᴏʀᴍᴀᴛɪᴏɴ"
		  - " <#555555>❙ <#FFFFFF>Owner: <#AA3300>%owner%"
		  - " <#555555>❙ <#FFFFFF>Prestiges: <#AA3300>%prestiges%"
		  - ""
		  - "<#AA3300>ꜱᴛᴀᴛꜱ"
		  - " <#555555>❙ <#FFFFFF>Ores: <#AA3300>%broken-blocks% <#FFAA88>broken"
		  - " <#555555>❙ <#FFFFFF>Money: <#AA3300>$%collected-money% <#FFAA88>collected"
		  - " <#555555>❙ <#FFFFFF>Essence: <#AA3300>%collected-essence% <#FFAA88>collected"
		  - ""
		  - "<#AA3300>ᴇɴᴄʜᴀɴᴛꜱ"
		  - "%enchants%" # go to the lang.yml -> enchant -> lore to customize this
		  - ""
		  - "<#AA3300><b>></b> <#FFAA88>Break blocks to level up."
	  # level 2
	  3:
		material: STONE_SHOVEL
	  5:
		material: IRON_SHOVEL
	  10:
		material: GOLDEN_SHOVEL
	  15:
		material: DIAMOND_SHOVEL
	  20:
		material: NETHERITE_SHOVEL

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
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axshovels.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	title: "&0ꜱʜᴏᴠᴇʟ"
	# a gui can have 1-6 rows
	rows: 5

	# ----- ITEMS -----

	border-decoration:
	  material: "BROWN_STAINED_GLASS_PANE"
	  slot: "border"
	  name: " "

	stats:
	  slot: 20
	  material: "BOOK"
	  name: "&#AA3300&lᴛᴏᴏʟ ꜱᴛᴀᴛɪꜱᴛɪᴄꜱ"
	  lore:
		- " "
		- "<#AA3300>ɢᴇɴᴇʀᴀʟ"
		- " <#555555>❙ <#FFFFFF>Level: <#AA3300>%tool-level%"
		- " <#555555>❙ <#FFFFFF>Progress: <#AA3300>%tool-progress-bar% &#DDDDDD(%tool-progress-percentage%%)"
		- " <#555555>❙ <#FFFFFF>Prestiges: <#AA3300>%prestiges%"
		- " <#555555>❙ <#FFFFFF>Ores: <#AA3300>%broken-blocks% <#FFAA88>broken"
		- " <#555555>❙ <#FFFFFF>Money: <#AA3300>$%collected-money% <#FFAA88>collected"
		- " <#555555>❙ <#FFFFFF>Essence: <#AA3300>%collected-essence% <#FFAA88>collected"
		- " "
		- "<#AA3300>ᴄʀᴏᴘꜱ"
		- " <#555555>❙ <#dfa06f>Dirt: <#AA3300>%broken-dirt% <#FFAA88>broken"
		- " <#555555>❙ <#e3dbb0>Sand: <#AA3300>%broken-sand% <#FFAA88>broken"
		- " <#555555>❙ <#e2d6d6>Gravel: <#AA3300>%broken-gravel% <#FFAA88>broken"
		- " <#555555>❙ <#c59e85>Soul Sand: <#AA3300>%broken-soulsand% <#FFAA88>broken"
		- " <#555555>❙ <#d97b30>Red Sand: <#AA3300>%broken-redsand% <#FFAA88>broken"
		- " <#555555>❙ <#8a7d78>Mud: <#AA3300>%broken-mud% <#FFAA88>broken"
		- " <#555555>❙ <#b68d75>Soul Soil: <#AA3300>%broken-soulsoil% <#FFAA88>broken"
		- " "

	enchants:
	  slot: 13
	  material: "ENCHANTED_BOOK"
	  name: "&#AA3300&lᴛᴏᴏʟ ᴇɴᴄʜᴀɴᴛᴍᴇɴᴛꜱ"
	  lore:
		- " "
		- "<#AA3300>ᴇɴᴄʜᴀɴᴛꜱ"
		- "%enchants%" # go to the lang.yml -> enchant -> lore to customize this
		- ""
		- "&#AA3300&lClick &l> &#FF7700View enchantments"
	  actions:
		- "[MENU] enchant"
		- "[SOUND] ui.button.click|1|1"

	leaderboards:
	  slot: 24
	  material: "GOLD_INGOT"
	  name: "&#AA3300&lʟᴇᴀᴅᴇʀʙᴏᴀʀᴅꜱ"
	  lore:
		- " "
		- "&#AA3300&lClick &l> &#FF7700View leaderboards"
	  actions:
		- "[MENU] leaderboards"
		- "[SOUND] ui.button.click|1|1"

	prestige:
	  slot: 31
	  material: "BEACON"
	  name: "&#AA3300&lᴘʀᴇꜱᴛɪɢᴇ"
	  lore:
		- " "
		- "<#AA3300><b>></b> <#FFAA88>Prestiges: <#AA3300>%prestiges%"
		- " "
		- "&#AA3300&lClick &l> &#FF7700Go to prestige menu"
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
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axshovels.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	# should the enchantment be enabled?
	enabled: true

	name: "&#FF7700Speed &#AA3300%level%"
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