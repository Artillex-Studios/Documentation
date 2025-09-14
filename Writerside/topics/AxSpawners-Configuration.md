# Configuration

<procedure title="config.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axspawners.html

	prefix: "<gradient:#00AAFF:#00CCFF><b>AxSpawners</b></gradient> &7» "

	database:
	  # currently only h2 is supported
	  type: "h2"

	# format: language_COUNTRY
	# after changing this, the server will download the default item names
	language: en_US

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

	# used for showing length of boosters
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

	# aliases for /axspawners shop
	# requires a restart for changes to apply
	shop-command-aliases:
	  - "spawnershop"
	  - "axspawnershop"
	  - "boostershop"

	# aliases for /axspawners myspawners
	# requires a restart for changes to apply
	my-spawners-command-aliases:
	  - "myspawners"
	  - "axmyspawners"

	# should items be generated when the owner of the spawner is offline?
	offline-spawning: true

	# should the spawner only generate loot when the chunk where the spawner is located is loaded?
	require-chunk-loaded: false

	# if true: only the player who placed the spawner can do these actions
	# if false: everyone who can build at the spawner's location (managed by the hooks.yml protection plugins) can do these actions on spawners
	only-owner:
	  # selling/taking generated items and xp
	  interact: false
	  # adding spawners to the stack (if false and players add spawners to someone else's spawner, the original owner will not change)
	  add: true
	  # removing spawners (if false, people will be able to steal each other's spawners if they have permission to build)
	  break: true

	# the minimum distance between spawners (in blocks)
	# set to 0 to disable
	minimum-distance: 0

	# should spawners be put in players' inventory when broken?
	# if false, they will be dropped on the ground
	pickup-to-inventory: true

	# when a spawner is broken, and it has items/xp in it, what to do?
	# 0 - drop or collect (might be a bad idea if you have a lot of spawner slots)
	# 1 - sell or collect
	# 2 - delete
	spawner-inventory-break-mode: 1

	# starting spawner limit (how many different spawners can be placed?)
	# how the limit is calculated?
	# default + database limit (/axspawners limit) + permission limit (axspawners.limit.<amount>)
	# set to -1 to disable spawner limits
	default-spawner-limit: 5

	# starting stack limit (how many spawners can be put together?)
	# how the limit is calculated?
	# default + permission limit (axspawners.stack.<amount>)
	# set to -1 to disable stack limits
	default-stack-limit: 5

	# when using loot tables, the plugin has to roll items to get the percentages
	# if you notice the plugin taking a long time to load, try decreasing this
	loot-table-roll-amount: 3000

	# should items have a stack count?
	# if enabled, you can store big spawner stacks in your hand without being limited to 64 spawners / slot, for example you can have a 10000x spawner
	# if disabled, you can only have 64 of 1 stack size spawners in your hand at once
	allow-spawner-item-stacking: true

	# list of sounds: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Sound.html
	# set to "" to disable
	sounds:
	  place: "ENTITY_EXPERIENCE_ORB_PICKUP"
	  pickup: "BLOCK_NOTE_BLOCK_HAT"
	  boost: "ENTITY_EXPERIENCE_ORB_PICKUP"

	# list of particles: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html
	# set to "" to disable
	particles:
	  pickup: "CRIT"
	  place: "SPELL"
	  upgrade: "VILLAGER_HAPPY"
	  boost: "VILLAGER_HAPPY"

	# can be used in spawner gui, hologram: %xp-bar%, %slots-bar%
	bar-placeholders:
	  length: 10
	  empty: "<color:#DDDDDD>■</color>"
	  full: "■"

	# settings for holograms displays
	holograms:
	  # set to 00000000 to make it invisible
	  # format (hexadecimal): AARRGGBB
	  background-color: 00000000
	  # list: left, right, center
	  alignment: center
	  # list: fixed, vertical, horizontal, center
	  billboard: vertical
	  # should blocks/entities be visible behind the displays?
	  see-through: false

	# how often should the plugin save spawners to the database?
	# requires a restart to change
	# this is in minutes
	auto-save-minutes: 3

	# worlds where you can't place spawners
	blacklisted-worlds:
	  - "example-world"

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
	# DOCUMENTATION: https://docs.artillex-studios.com/axspawners.html

	# what plugin to use?
	# used for calculating spawner drop value
	# if multiple is enabled, the highest sell value will be used
	price-plugins:
	  ShopGUIPlus: true
	  Essentials: true
	  EconomyShopGUI: true
	  CMI: true

	# list of supported plugins: https://docs.artillex-studios.com/axspawners.html
	# used for spawner upgrade prices
	currency-plugins:
	  plugin: Vault
	  # this value is only used when the plugin supports multiple currencies
	  currency: ""

	# what plugin to use?
	protection-plugins:
	  BentoBox: true
	  GriefPrevention: true
	  HuskTowns: true
	  IridiumSkyBlock: true
	  KingdomsX: true
	  Lands: true
	  PlotSquared: true
	  SuperiorSkyBlock2: true
	  WorldGuard: true

	# do not change this
	version: 1
]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axspawners.html

	help:
	  - " "
	  - "<gradient:#00AAFF:#00CCFF><b>AxSpawners</b></gradient> <#00DDFF>Help"
	  - " <#00DDFF>➤ <white>/axspawners reload <#DDDDDD>| <#AAFFFF>Reload plugin"
	  - " <#00DDFF>➤ <white>/axspawners give <player> <spawner> [quantity] [stack size] [level] <#DDDDDD>| <#AAFFFF>Give spawners"
	  - " <#00DDFF>➤ <white>/axspawners booster <player> <booster> <multiplier> <length> [quantity] <#DDDDDD>| <#AAFFFF>Give boosters"
	  - " <#00DDFF>➤ <white>/axspawners shop [player] <#DDDDDD>| <#AAFFFF>Open shop"
	  - " <#00DDFF>➤ <white>/axspawners stats <#DDDDDD>| <#AAFFFF>Plugin statistics"
	  - " <#00DDFF>➤ <white>/axspawners logs [player] <#DDDDDD>| <#AAFFFF>Open log gui"
	  - " <#00DDFF>➤ <white>/axspawners limit give <player> <amount> <#DDDDDD>| <#AAFFFF>Increase spawner limit of player"
	  - " <#00DDFF>➤ <white>/axspawners limit take <player> <amount> <#DDDDDD>| <#AAFFFF>Decrease spawner limit of player"
	  - " <#00DDFF>➤ <white>/axspawners limit set <player> <amount> <#DDDDDD>| <#AAFFFF>Set spawner limit of player"
	  - " <#00DDFF>➤ <white>/axspawners limit reset <player> <#DDDDDD>| <#AAFFFF>Set spawner limit of player to 0"
	  - " <#00DDFF>➤ <white>/myspawners <#DDDDDD>| <#AAFFFF>Open my spawners gui"
	  - " "

	stats:
	  - " "
	  - "<gradient:#00AAFF:#00CCFF><b>AxSpawners</b></gradient> <#00DDFF>Statistics"
	  - " <#00DDFF>➤ <white>Total Spawners: <#AAFFFF>%total-spawners%"
	  - " <#00DDFF>➤ <white>Loaded Spawners: <#AAFFFF>%loaded-spawners%"
	  - " <#00DDFF>➤ <white>Loaded Chunks: <#AAFFFF>%loaded-chunks%"
	  - " "

	time:
	  second: "s"
	  minute: "m"
	  hour: "h"
	  day: "d"

	give:
	  success: "&#00FF00You have given &#FFFFFF%name% &#00FF00to &#FFFFFF%player%&#00FF00!"
	  received: "&#00FF00You have got &#FFFFFF%name%&#00FF00!"
	  stacking-disabled: "&#DDDDDDNote: You have disabled allow-spawner-item-stacking in the config.yml so the stack size option is be ignored!"

	booster:
	  success: "&#00FF00You have given a(n) &#FFFFFF%name% &#00FF00to &#FFFFFF%player%&#00FF00!"
	  received: "&#00FF00You have got a(n) &#FFFFFF%name%&#00FF00!"
	  activated: "&#00FF00You have activated a(n) &#FFFFFF%name% &#00FF00on the spawner!"
	  already-active: "&#FF0000This booster is already active on this spawner."
	  disallowed-spawner: "&#FF0000This booster can't be used on this spawner."
	  not-yours: "&#FF0000This spawner is not yours, so you are not allowed to interact with it!"
	  removed: "&#FF0000You have removed a(n) &#FFFFFF%name% &#FF0000from the spawner!"
	  no-boosters: "&#FF0000There are no active boosters!"

	shop:
	  purchased: "&#00FF00You have purchased &#FFFFFF%name% &#00FF00for &#FFFFFF$%money%&#00FF00!"
	  no-money: "&#FF0000You can't purchase this item because you don't have enough money. You need &#FFFFFF%money% money&#FF0000!"

	spawner-gui:
	  pickup-full: "&#FF0000Can't take item out, because your inventory is full."
	  maxed: "<color:#FF0000>MAXED</color>"
	  disallow: "&#FF0000You are not allowed to interact with the spawner!"
	  not-yours: "&#FF0000This spawner is not yours, so you are not allowed to interact with it!"

	whitelist:
	  adding: "&#00FF00Write the name of the player in the chat! Write &#FFFFFFcancel &#00FF00to stop!"
	  added: "&#00FF00You have successfully whitelisted &#FFFFFF%player%&#00FF00!"
	  removed: "&#00FF00You have successfully removed &#FFFFFF%player% &#00FF00from the whitelist!"
	  unknown: "&#FF0000No player can be found with the name &#FFFFFF%player%&#FF0000!"
	  self: "&#FF0000You can't whitelist yourself!"
	  already-added: "&#FF0000You have already whitelisted &#FFFFFF%player%&#FF0000!"
	  not-yours: "&#FF0000Only the spawner's owner can edit the whitelist!"

	place:
	  success: "&#00FF00You have placed &#FFFFFF%name%&#00FF00! &#DDDDDD(%current-limit%/%max-limit%)"
	  add: "&#00FF00You have added &#FFFFFF%name%&#00FF00! &#00FF00The new stack size is: &#FFFFFF%amount%&#00FF00!"
	  disallow: "&#FF0000You are not allowed to place spawners here!"
	  not-yours: "&#FF0000This spawner is not yours, so you are not allowed to add spawners to it!"
	  too-close: "&#FF0000There must be at least &#FFFFFF%distance% &#FF0000blocks between your spawners!"
	  place-limit: "&#FF0000You can't place more spawners, because you have reached the spawner limit. &#DDDDDD(%current-limit%/%max-limit%)"
	  stack-limit: "&#FF0000You can't add more spawners to this stack, because you have reached the spawner stack limit. &#DDDDDD(%current-limit%/%max-limit%)"

	break:
	  success: "&#00FF00You have broken &#FFFFFF%name%&#00FF00! &#DDDDDD(%current-limit%/%max-limit%)"
	  remove: "&#00FF00You have removed &#FFFFFF%name%&#00FF00! &#00FF00The new stack size is: &#FFFFFF%amount%&#00FF00!"
	  disallow: "&#FF0000You are not allowed to break the spawner!"
	  not-yours: "&#FF0000This spawner is not yours, so you are not allowed to break it!"

	upgrade:
	  success: "&#00FF00You have successfully upgraded the spawner to level &#FFFFFF%level%&#00FF00."
	  maxed: "&#FF0000The spawner has reached the maximum level and it can't be upgraded further."
	  no-money: "&#FF0000You can't upgrade this spawner because you don't have enough money. You need &#FFFFFF%money% money&#FF0000!"

	limit:
	  give: "&#00FF00You have given &#FFFFFF%amount% &#00FF00to the spawner limit of &#FFFFFF%player%&#00FF00! &#00FF00Their new limit is: &#FFFFFF%new-amount%&#00FF00!"
	  take: "&#00FF00You have took &#FFFFFF%amount% &#00FF00from the spawner limit of &#FFFFFF%player%&#00FF00! &#00FF00Their new limit is: &#FFFFFF%new-amount%&#00FF00!"
	  set: "&#00FF00You have set the spawner limit of &#FFFFFF%player% &#00FF00to &#FFFFFF%amount%&#00FF00!"

	withdraw:
	  success: "&#00FF00You have successfully withdrew &#FFFFFF%xp% &#00FF00xp from the spawner."
	  empty: "&#FF0000There is nothing to withdraw from this spawner."

	sell-all:
	  success: "&#00FF00You have successfully sold &#FFFFFF%amount% &#00FF00items for &#FFFFFF$%money%&#00FF00."
	  empty: "&#FF0000There are no drops to sell in this spawner."

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

	update-notifier: "&#00AAFFThere is a new version of AxSpawners available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"

	# do not change this
	version: 1
]]>
</code-block></step>
</procedure>

<procedure title="shop.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axspawners.html

	# format:
	# | pages:
	# | 1: - page number (starts at 1)
	# |     10: - slot in gui (starts at 0)
	pages:
	  1:
		10:
		  # spawner example
		  spawner:
			# name is the file name from the "spawners" folder (without the .yml)
			name: "zombie"
			# spawner level to give
			level: 1
			# amount of spawners to give
			amount: 1
			# stack size of spawner
			stack-size: 1
			# cost of spawner, the currency plugin selected in the hooks.yml will be used
			price: 1000
		  # the item to display
		  display:
			amount: 1
			material: ZOMBIE_HEAD
			name: "<#AAFFAA>%amount% <#00AA00>ᴢᴏᴍʙɪᴇ <white>Spawner"
			lore:
			  - ""
			  - "<#00AA00><bold>></bold> <#AAFFAA>Price: <#00AA00>$%price%"
			  - "<#00AA00><bold>></bold> <#AAFFAA>Level: <#00AA00>%level%"
			  - ""
			  - "<#00AA00>ꜱᴛᴀᴛꜱ"
			  - " <#555555>❙ <#FFFFFF>Speed: <#00AA00>%speed% seconds"
			  - " <#555555>❙ <#FFFFFF>Dropped XP: <#00AA00>%xp%"
			  - " <#555555>❙ <#FFFFFF>XP Storage: <#00AA00>%max-xp%"
			  - " <#555555>❙ <#FFFFFF>Loot Slots: <#00AA00>%max-slots%"
			  - ""
			  - "<#00AA00>ᴅʀᴏᴘꜱ"
			  - " <#555555>❙ <#FFFFFF>%drop% <#AAAAAA>(<#00AA00>%chance%%<#AAAAAA>)" # the line containing %drop% will be duplicated for every possible drop
			  - ""
			  - "<#00AA00><bold>></bold> <#AAFFAA>Click to purchase spawner!"
		11:
		  spawner:
			name: "skeleton"
			level: 1
			amount: 1
			stack-size: 1
			price: 1500
		  display:
			amount: 1
			material: SKELETON_SKULL
			name: "<#DDDDFF>%amount% <#AAAABB><bold>ꜱᴋᴇʟᴇᴛᴏɴ</bold> <white>Spawner"
			lore:
			  - ""
			  - "<#AAAABB><bold>></bold> <#DDDDFF>Price: <#AAAABB>$%price%"
			  - "<#AAAABB><bold>></bold> <#DDDDFF>Level: <#AAAABB>%level%"
			  - ""
			  - "<#AAAABB>ꜱᴛᴀᴛꜱ"
			  - " <#555555>❙ <#FFFFFF>Speed: <#AAAABB>%speed% seconds"
			  - " <#555555>❙ <#FFFFFF>Dropped XP: <#AAAABB>%xp%"
			  - " <#555555>❙ <#FFFFFF>XP Storage: <#AAAABB>%max-xp%"
			  - " <#555555>❙ <#FFFFFF>Loot Slots: <#AAAABB>%max-slots%"
			  - ""
			  - "<#AAAABB>ᴅʀᴏᴘꜱ"
			  - " <#555555>❙ <#FFFFFF>%drop% <#AAAAAA>(<#AAAABB>%chance%%<#AAAAAA>)" # the line containing %drop% will be duplicated for every possible drop
			  - ""
			  - "<#AAAABB><bold>></bold> <#DDDDFF>Click to purchase spawner!"
		12:
		  spawner:
			name: "creeper"
			level: 1
			amount: 1
			stack-size: 1
			price: 2500
		  display:
			amount: 1
			material: CREEPER_HEAD
			name: "<#77FF77>%amount% <#00CC00><bold>ᴄʀᴇᴇᴘᴇʀ</bold> <white>Spawner"
			lore:
			  - ""
			  - "<#00CC00><bold>></bold> <#77FF77>Price: <#00CC00>$%price%"
			  - "<#00CC00><bold>></bold> <#77FF77>Level: <#00CC00>%level%"
			  - ""
			  - "<#00CC00>ꜱᴛᴀᴛꜱ"
			  - " <#555555>❙ <#FFFFFF>Speed: <#00CC00>%speed% seconds"
			  - " <#555555>❙ <#FFFFFF>Dropped XP: <#00CC00>%xp%"
			  - " <#555555>❙ <#FFFFFF>XP Storage: <#00CC00>%max-xp%"
			  - " <#555555>❙ <#FFFFFF>Loot Slots: <#00CC00>%max-slots%"
			  - ""
			  - "<#00CC00>ᴅʀᴏᴘꜱ"
			  - " <#555555>❙ <#FFFFFF>%drop% <#AAAAAA>(<#00CC00>%chance%%<#AAAAAA>)" # the line containing %drop% will be duplicated for every possible drop
			  - ""
			  - "<#00CC00><bold>></bold> <#77FF77>Click to purchase spawner!"
		13:
		  spawner:
			name: "witch"
			level: 1
			amount: 1
			stack-size: 1
			price: 10000
		  display:
			amount: 1
			material: PLAYER_HEAD
			texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMjBlMTNkMTg0NzRmYzk0ZWQ1NWFlYjcwNjk1NjZlNDY4N2Q3NzNkYWMxNmY0YzNmODcyMmZjOTViZjlmMmRmYSJ9fX0=
			name: "<#C95EFF>%amount% <#8844ff><bold>ᴡɪᴛᴄʜ</bold> <white>Spawner"
			lore:
			  - ""
			  - "<#8844ff><bold>></bold> <#C95EFF>Price: <#8844ff>$%price%"
			  - "<#8844ff><bold>></bold> <#C95EFF>Level: <#8844ff>%level%"
			  - ""
			  - "<#8844ff>ꜱᴛᴀᴛꜱ"
			  - " <#555555>❙ <#FFFFFF>Speed: <#8844ff>%speed% seconds"
			  - " <#555555>❙ <#FFFFFF>Dropped XP: <#8844ff>%xp%"
			  - " <#555555>❙ <#FFFFFF>XP Storage: <#8844ff>%max-xp%"
			  - " <#555555>❙ <#FFFFFF>Loot Slots: <#8844ff>%max-slots%"
			  - ""
			  - "<#8844ff>ᴅʀᴏᴘꜱ"
			  - " <#555555>❙ <#FFFFFF>%drop% <#AAAAAA>(<#8844ff>%chance%%<#AAAAAA>)" # the line containing %drop% will be duplicated for every possible drop
			  - ""
			  - "<#8844ff><bold>></bold> <#C95EFF>Click to purchase spawner!"
		14:
		  spawner:
			name: "guardian"
			level: 1
			amount: 1
			stack-size: 1
			price: 50000
		  display:
			amount: 1
			material: PLAYER_HEAD
			texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjhlNzI1Nzc5YzIzNGM1OTBjY2U4NTRkYjVjMTA0ODVlZDhkOGEzM2ZhOWIyYmRjMzQyNGI2OGJiMTM4MGJlZCJ9fX0=
			name: "<#CCFFEE>%amount% <#00FFCC><bold>ɢᴜᴀʀᴅɪᴀɴ</bold> <white>Spawner"
			lore:
			  - ""
			  - "<#00FFCC><bold>></bold> <#CCFFEE>Price: <#00FFCC>$%price%"
			  - "<#00FFCC><bold>></bold> <#CCFFEE>Level: <#00FFCC>%level%"
			  - ""
			  - "<#00FFCC>ꜱᴛᴀᴛꜱ"
			  - " <#555555>❙ <#FFFFFF>Speed: <#00FFCC>%speed% seconds"
			  - " <#555555>❙ <#FFFFFF>Dropped XP: <#00FFCC>%xp%"
			  - " <#555555>❙ <#FFFFFF>XP Storage: <#00FFCC>%max-xp%"
			  - " <#555555>❙ <#FFFFFF>Loot Slots: <#00FFCC>%max-slots%"
			  - ""
			  - "<#00FFCC>ᴅʀᴏᴘꜱ"
			  - " <#555555>❙ <#FFFFFF>%drop% <#AAAAAA>(<#00FFCC>%chance%%<#AAAAAA>)" # the line containing %drop% will be duplicated for every possible drop
			  - ""
			  - "<#00FFCC><bold>></bold> <#CCFFEE>Click to purchase spawner!"
		19:
		  # booster example
		  booster:
			# name is the file name from the "boosters" folder (without the .yml)
			name: "loot-booster"
			# amount of boosters to give
			amount: 1
			# spawner level to give
			multiplier: 2.0
			# how long should the booster last? in milliseconds or string (like 10m5s)
			length: 5m
			# cost of booster, the currency plugin selected in the hooks.yml will be used
			price: 1000
		  # the item to display
		  display:
			amount: 1
			material: PLAYER_HEAD
			texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZWRiNWNlMGQ0NGMzZTgxMzhkYzJlN2U1MmMyODk3YmI4NzhlMWRiYzIyMGQ3MDY4OWM3YjZiMThkMzE3NWUwZiJ9fX0=
			name: "<#FFAAAA>%multiplier%x <#FF0000>ʟᴏᴏᴛ <white>Booster"
			lore:
			  - ""
			  - "<#FF0000><bold>></bold> <#FFAAAA>Price: <#FF0000>$%price%"
			  - "<#FF0000><bold>></bold> <#FFAAAA>Increases the loot generated by the spawner."
			  - ""
			  - "<#FF0000>ꜱᴛᴀᴛꜱ"
			  - " <#555555>❙ <#FFFFFF>Multiplier: <#FF0000>%multiplier%x"
			  - " <#555555>❙ <#FFFFFF>Booster length: <#FF0000>%length%"
			  - " <#555555>❙ <#FFFFFF>Allowed spawners: <#FF0000>all"
			  - ""
			  - "<#FF0000><bold>></bold> <#FFAAAA>Click to purchase booster!"
		20:
		  booster:
			name: "speed-booster"
			amount: 1
			multiplier: 2.0
			length: 5m
			price: 1000
		  display:
			amount: 1
			material: PLAYER_HEAD
			texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNTgwNTU3ZmU2M2YwNmI0YzcwZTJjNWViMmVmNmMwZDhkNWI1NWZkMDljYzVkZTNiY2I2NWY4MzJlMDVkNGMyZSJ9fX0=
			name: "<#AAFFFF>%multiplier%x <#00CCFF>ꜱᴘᴇᴇᴅ <white>Booster"
			lore:
			  - ""
			  - "<#00CCFF><bold>></bold> <#AAFFFF>Price: <#00CCFF>$%price%"
			  - "<#00CCFF><bold>></bold> <#AAFFFF>Increases the generation speed of the spawner."
			  - ""
			  - "<#00CCFF>ꜱᴛᴀᴛꜱ"
			  - " <#555555>❙ <#FFFFFF>Multiplier: <#00CCFF>%multiplier%x"
			  - " <#555555>❙ <#FFFFFF>Booster length: <#00CCFF>%length%"
			  - " <#555555>❙ <#FFFFFF>Allowed spawners: <#00CCFF>all"
			  - ""
			  - "<#00CCFF><bold>></bold> <#AAFFFF>Click to purchase booster!"
		21:
		  booster:
			name: "xp-booster"
			amount: 1
			multiplier: 2.0
			length: 5m
			price: 1000
		  display:
			amount: 1
			material: PLAYER_HEAD
			texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMTNkZDYxZTQ4NDI2M2MzNGYxNzg3ZjY2MGNkNjAwYzI4Y2MyZmIwZGU2NTg5MDI3NDI5NGFjZDJjMzAzMjA2OCJ9fX0=
			name: "<#FFFFAA>%multiplier%x <#FFCC00>xᴘ <white>Booster"
			lore:
			  - ""
			  - "<#FFCC00><bold>></bold> <#FFFFAA>Price: <#FFCC00>$%price%"
			  - "<#FFCC00><bold>></bold> <#FFFFAA>Increases the xp generated by the spawner."
			  - ""
			  - "<#FFCC00>ꜱᴛᴀᴛꜱ"
			  - " <#555555>❙ <#FFFFFF>Multiplier: <#FFCC00>%multiplier%x"
			  - " <#555555>❙ <#FFFFFF>Booster length: <#FFCC00>%length%"
			  - " <#555555>❙ <#FFFFFF>Allowed spawners: <#FFCC00>all"
			  - ""
			  - "<#FFCC00><bold>></bold> <#FFFFAA>Click to purchase booster!"

	# do not change this
	version: 1
]]>
</code-block></step>
</procedure>

Example Booster configuration (the plugin comes with 3 included)
<procedure title="boosters/speed-booster.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axspawners.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	# list of booster types: loot, speed, xp
	type: speed

	item:
	  material: PLAYER_HEAD
	  texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNTgwNTU3ZmU2M2YwNmI0YzcwZTJjNWViMmVmNmMwZDhkNWI1NWZkMDljYzVkZTNiY2I2NWY4MzJlMDVkNGMyZSJ9fX0=
	  name: "<#AAFFFF>%multiplier%x <#00CCFF>ꜱᴘᴇᴇᴅ <white>Booster"
	  lore:
		- ""
		- "<#00CCFF><bold>></bold> <#AAFFFF>Increases the generation speed of the spawner."
		- ""
		- "<#00CCFF>ꜱᴛᴀᴛꜱ"
		- " <#555555>❙ <#FFFFFF>Multiplier: <#00CCFF>%multiplier%x"
		- " <#555555>❙ <#FFFFFF>Booster length: <#00CCFF>%length%"
		- " <#555555>❙ <#FFFFFF>Allowed spawners: <#00CCFF>all"
		- ""
		- "<#00CCFF><bold>></bold> <#AAFFFF>Right click on a spawner while holding to boost."

	# which spawners can this booster be applied on?
	# the spawner names must be the same as the file name in the spawners folder (without the .yml)
	# use * to allow the booster on all spawners
	allowed-spawners:
	  - "*"
]]>
</code-block></step>
</procedure>

Example Wand configuration (the plugin comes with 2 included)
<procedure title="wands/sell-wand.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axspawners.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	# list of wand types: sell, xp
	type: sell

	item:
	  material: STICK
	  name: "<#FFBB77>%multiplier%x <#FF7700>ꜱᴇʟʟ <white>Wand <#AAAAAA>(%uses% uses)"
	  lore:
		- ""
		- "<#FF7700>ꜱᴛᴀᴛꜱ"
		- " <#555555>❙ <#FFFFFF>Multiplier: <#FF7700>%multiplier%x"
		- " <#555555>❙ <#FFFFFF>Uses: <#FF7700>%uses%"
		- " <#555555>❙ <#FFFFFF>Radius: <#FF7700>%radius% blocks"
		- " <#555555>❙ <#FFFFFF>Allowed spawners: <#FF7700>all"
		- ""
		- "<#FF7700>ᴇᴀʀɴɪɴɢꜱ"
		- " <#555555>❙ <#FFFFFF>Items sold: <#FF7700>%items-sold%"
		- " <#555555>❙ <#FFFFFF>Money made: <#FF7700>$%money-made%"
		- ""
		- "<#FF7700><bold>></bold> <#FFBB77>Right click to sell all items from nearby spawners."

	# which spawners can this wand be used on?
	# the spawner names must be the same as the file name in the spawners folder (without the .yml)
	# use * to allow the wand to be used on all spawners
	allowed-spawners:
	  - "*"

	# how often should the sellwand be usable?
	# in milliseconds, set to -1 to disable
	usage-cooldown: 1000

	# when using the wand, what particle color should be used?
	# format: <RED>;<GREEN>;<BLUE>
	particle-color: "255;119;0"
]]>
</code-block></step>
</procedure>

Example Spawner configuration (the plugin comes with 27 included)
<procedure title="spawners/_example.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axspawners.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html
	# THIS IS THE EXAMPLE FILE

	item:
	  material: ZOMBIE_HEAD
	  name: "<#AAFFAA>%amount% <#00AA00><bold>ᴢᴏᴍʙɪᴇ <white>Spawner"
	  lore:
		- ""
		- "<#00AA00><bold>></bold> <#AAFFAA>Level: <#00AA00>%level%"
		- ""
		- "<#00AA00>ꜱᴛᴀᴛꜱ"
		- " <#555555>❙ <#FFFFFF>Speed: <#00AA00>%speed% seconds"
		- " <#555555>❙ <#FFFFFF>Dropped XP: <#00AA00>%xp%"
		- " <#555555>❙ <#FFFFFF>XP Storage: <#00AA00>%max-xp%"
		- " <#555555>❙ <#FFFFFF>Loot Slots: <#00AA00>%max-slots%"
		- ""
		- "<#00AA00>ᴅʀᴏᴘꜱ"
		- " <#555555>❙ <#FFFFFF>%drop% <#AAAAAA>(<#00AA00>%chance%%<#AAAAAA>)" # the line containing %drop% will be duplicated for every possible drop
		- ""
		- "<#00AA00><bold>></bold> <#AAFFAA>This spawner automatically generates items."

	# what type of block should the spawner be?
	# note: this won't be automatically updated, it will only apply to newly placed spawners
	spawner-block:
	  material: SPAWNER

	# the item which will be spinning inside the spawner block
	# remove the section to disable
	spawner-block-item:
	  material: ZOMBIE_HEAD

	# item shown in the /myspawners command
	gui-item:
	  material: ZOMBIE_HEAD
	  name: "<#AAFFAA>%amount% <#00AA00><bold>ᴢᴏᴍʙɪᴇ <white>Spawner <#AAFFAA>(Level %level%)"
	  lore:
		- ""
		- "<#00AA00><bold>></bold> <#AAFFAA>Next Spawn: <#00AA00>%next-spawn% seconds"
		- ""
		- "<#00AA00>ꜱᴛᴏʀᴀɢᴇ"
		- " <#555555>❙ <#FFFFFF>XP Storage: <#00AA00>%xp-bar% &#AAAAAA(%xp-percentage%%)"
		- " <#555555>❙ <#FFFFFF>Loot Slots: <#00AA00>%slots-bar% &#AAAAAA(%slots-percentage%%)"
		- ""
		- "<#00AA00>Left Click <bold>></bold> <#AAFFAA>Open Spawner"
		- "<#00AA00>Right Click <bold>></bold> <#AAFFAA>Sell Loot & Withdraw XP"

	hologram:
	  enabled: true
	  height: 1.3
	  lines:
		  - "<#FFFFFF>%amount% <#00AA00><bold>ᴢᴏᴍʙɪᴇ <white>Spawner <#AAFFAA>(Level %level%)"
		  - ""
		  - "<#FFFFFF>XP Storage: <#AAFFAA>%xp-bar% &#AAAAAA(%xp-percentage%%)"
		  - "<#FFFFFF>Loot Slots: <#AAFFAA>%slots-bar% &#AAAAAA(%slots-percentage%%)"
		  - ""
		  - "<#AAFFAA>Spawning in <bold>></bold> <#FFFFFF>%next-spawn% seconds"

	levels:
	  price-calculation:
		# TYPES
		# - formula (uses the given formula to calculate price of a level)
		# - manual (you can configure the price of levels yourself one-by-one)
		# note: levels start from 1 and these are the cost of upgrading from that level, so to go from level 1 to level 2, the level 1 price will be used
		type: "formula"
		formula: "%level% * 100"
		manual:
		  1: "100"
		  2: "200"
		  3: "300"
		  4: "400"
	  # the list of levels (you can configure any amount of levels)
	  # make sure that you set a price for all levels if you are using manual price-calculation
	  upgrades:
		# level 1 (DEFAULT LEVEL)
		1:
		  # time it takes to generate loot (in seconds)
		  # you can also set a range (like: 5-10) to make generation a bit more random
		  speed: 15-20
		  storage:
			# the max xp that the spawner can store
			xp: 500
			# the amount of slots where loot can go (the plugin support any number of slots)
			slots: 9
		  loot:
			# how much xp should one mob drop? (can be a range, like 5-10)
			experience: 5
			# TYPES
			# - loot-table (uses vanilla minecraft formulas - https://minecraft.wiki/w/Loot_table)
			# - manual (you can configure the price of levels yourself one-by-one)
			type: loot-table
			# if loot-table type is used, name of the loot table (https://mcreator.net/wiki/minecraft-vanilla-loot-tables-list)
			loot-table:
			  value: "entities/zombie"
			  multiplier: 1
			# if manual type is used, the list of drops (can be any amount)
			# chance: the chance in percents for a drop to be chosen
			# drops: the number of items to drop if chosen (if a range is given, a number between will be picked)
			# item: the item to drop
			# xp: the xp to give (if a range is given, a number between will be picked)
			manual:
			  - chance: 100
				drops: 1-3
				item:
				  material: ROTTEN_FLESH
			  - chance: 1
				drops: 1
				item:
				  material: IRON_INGOT
		# level 2
		2:
		  speed: 12-15
		  storage:
			xp: 800
			slots: 18
		  loot:
			experience: 5-10
			type: loot-table
			loot-table:
			  value: "entities/zombie"
			  multiplier: 1.3
			manual:
			  - chance: 100
				drops: 1-3
				item:
				  material: ROTTEN_FLESH
			  - chance: 3
				drops: 1
				item:
				  material: IRON_INGOT
		# level 3
		3:
		  speed: 9-12
		  storage:
			xp: 1100
			slots: 27
		  loot:
			experience: 10-20
			type: loot-table
			loot-table:
			  value: "entities/zombie"
			  multiplier: 1.6
			manual:
			  - chance: 100
				drops: 1-3
				item:
				  material: ROTTEN_FLESH
			  - chance: 5
				drops: 1
				item:
				  material: IRON_INGOT
		# level 4
		4:
		  speed: 6-9
		  storage:
			xp: 2000
			slots: 36
		  loot:
			experience: 20-30
			type: loot-table
			loot-table:
			  value: "entities/zombie"
			  multiplier: 1.9
			manual:
			  - chance: 100
				drops: 1-3
				item:
				  material: ROTTEN_FLESH
			  - chance: 7
				drops: 1
				item:
				  material: IRON_INGOT
		# level 5
		5:
		  speed: 3-6
		  storage:
			xp: 3200
			slots: 45
		  loot:
			experience: 30-50
			type: loot-table
			loot-table:
			  value: "entities/zombie"
			  multiplier: 2.2
			manual:
			  - chance: 100
				drops: 1-3
				item:
				  material: ROTTEN_FLESH
			  - chance: 9
				drops: 1
				item:
				  material: IRON_INGOT
]]>
</code-block></step>
</procedure>

Example GUI configuration (there are 5 diffent configurable guis)
<procedure title="guis/spawner-gui.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axspawners.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	title: "%name% <#404040>(page #%page%)"
	# a gui can have 1-6 rows
	rows: 6
	# how many items should be shown on a single page?
	page-size: 45

	# ----- ITEMS -----

	# used for slots above the spawner's item storage limit
	locked-slot:
	  material: RED_STAINED_GLASS_PANE
	  name: "&#FF0000&lʟᴏᴄᴋᴇᴅ ꜱʟᴏᴛ"
	  lore:
		- " "
		- " &fThis slot is locked."
		- " &fUpgrade the spawner to gain more!"
		- " "
		- "&#FF0000&l> &#FFAAAALocked"

	# the lore to append for all loot items in the spawner gui
	drop-lore:
	  - " "
	  - "&#00AAFFClick &#00AAFF&l> &#00DDFFTake Item"
	  - "&#00AAFFShift Click &#00AAFF&l> &#00DDFFFill Inventory"

	inventory:
	  slot: 45
	  material: "CHEST"
	  name: "&#00AAFF&lɪɴᴠᴇɴᴛᴏʀʏ"
	  lore:
		- " "
		- "&#00DDFFSlots &#00DDFF&l> &#AAFFFF%current-slots%&#00AAFF/&#00DDFF%max-slots% &#AAAAAA(%slots-percentage%%)"
		- "&#00DDFFSell Price &#00DDFF&l> &#AAFFFF%sell-price%$"
		- " "
		- "&#00AAFFClick &#00AAFF&l> &#00DDFFSell All Items"
	  actions:
		- "[SELL-ALL]"
		- "[SOUND] ui.button.click|1|1"

	boosters:
	  slot: 46
	  material: "BEACON"
	  name: "&#00AAFF&lʙᴏᴏꜱᴛᴇʀꜱ"
	  lore:
		- " "
		- "<#00AAFF>ʟɪꜱᴛ"
		- " <#555555>❙ <#FFAAAA>%booster-loot-multiplier%x <#FF0000>ʟᴏᴏᴛ <white>Booster <#AAAAAA>(%booster-loot-time%)"
		- " <#555555>❙ <#AAFFFF>%booster-speed-multiplier%x <#00CCFF>ꜱᴘᴇᴇᴅ <white>Booster <#AAAAAA>(%booster-speed-time%)"
		- " <#555555>❙ <#FFFFAA>%booster-xp-multiplier%x <#FFCC00>xᴘ <white>Booster <#AAAAAA>(%booster-xp-time%)"
		- " "
		- "&#00AAFFClick &#00AAFF&l> &#00DDFFTake Out Boosters"
	  actions:
		- "[TAKE-BOOSTERS]"
		- "[SOUND] ui.button.click|1|1"

	previous-page:
	  slot: 48
	  material: "ARROW"
	  name: "&#00AAFF&lᴘʀᴇᴠɪᴏᴜs ᴘᴀɢᴇ"
	  lore:
		- " "
		- " &fClick here to go back"
		- " &fto the previous page!"
		- " "
		- "&#00AAFFClick &#00AAFF&l> &#00DDFFPrevious Page"
	  actions:
		- "[PAGE] previous"
		- "[SOUND] ui.button.click|1|1"

	upgrade:
	  slot: 49
	  material: "BELL"
	  name: "&#00AAFF&lᴜᴘɢʀᴀᴅᴇ <#AAAAAA>(<#AAFFFF>%level% <#00AAFF>-> <#00DDFF>%upgraded-level%<#AAAAAA>)"
	  lore:
		- " "
		- "&#00DDFFPrice &#00DDFF&l> &#AAFFFF%upgrade-price% &#FFFFFFmoney"
		- " "
		- "<#00AAFF>ᴜᴘɢʀᴀᴅᴇꜱ"
		- " <#555555>❙ <#FFFFFF>Speed: <#AAFFFF>%speed% <#00AAFF>-> <#00DDFF>%upgraded-speed% seconds"
		- " <#555555>❙ <#FFFFFF>Dropped XP: <#AAFFFF>%xp% <#00AAFF>-> <#00DDFF>%upgraded-xp%"
		- " <#555555>❙ <#FFFFFF>XP Storage: <#AAFFFF>%max-xp% <#00AAFF>-> <#00DDFF>%upgraded-max-xp%"
		- " <#555555>❙ <#FFFFFF>Loot Slots: <#AAFFFF>%max-slots% <#00AAFF>-> <#00DDFF>%upgraded-max-slots%"
		- " "
		- "&#00AAFFClick &#00AAFF&l> &#00DDFFUpgrade Spawner"
	  actions:
		- "[UPGRADE]"
		- "[SOUND] ui.button.click|1|1"

	next-page:
	  slot: 50
	  material: "ARROW"
	  name: "&#00AAFF&lɴᴇxᴛ ᴘᴀɢᴇ"
	  lore:
		- " "
		- " &fClick here to go"
		- " &fto the next page!"
		- " "
		- "&#00AAFFClick &#00AAFF&l> &#00DDFFNext Page"
	  actions:
		- "[PAGE] next"
		- "[SOUND] ui.button.click|1|1"

	players:
	  slot: 52
	  material: "WHITE_BANNER"
	  name: "&#00AAFF&lᴘʟᴀʏᴇʀꜱ"
	  lore:
		- " "
		- " &fPlayers who are whitelisted can interact with the"
		- " &fspawner even if they don't have access to the land."
		- " "
		- "&#00DDFFWhitelisted &#00DDFF&l> &#AAFFFF%whitelisted-players% players"
		- " "
		- "&#00AAFFClick &#00AAFF&l> &#00DDFFClick to Open"
	  actions:
		- "[WHITELISTED]"
		- "[SOUND] ui.button.click|1|1"

	xp:
	  slot: 53
	  material: "EXPERIENCE_BOTTLE"
	  name: "&#00AAFF&lxᴘ"
	  lore:
		- " "
		- "&#00DDFFStorage &#00DDFF&l> &#AAFFFF%current-xp%&#00AAFF/&#00DDFF%max-xp% &#AAAAAA(%xp-percentage%%)"
		- " "
		- "&#00AAFFClick &#00AAFF&l> &#00DDFFWithdraw XP"
	  actions:
		- "[WITHDRAW]"
		- "[SOUND] ui.button.click|1|1"

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