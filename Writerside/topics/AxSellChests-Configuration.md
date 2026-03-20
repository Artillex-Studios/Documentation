# Configuration

### Layout
<code-block lang="text">
AxSellChests/
├── boosters/
│   ├── money-booster.yml
│   ├── speed-booster.yml
│   └── ... you can create more
├── chests/
│   ├── basic.yml
│   ├── legendary.yml
│   ├── mythical.yml
│   └── ... you can create more
├── guis/
│   ├── logs-gui.yml
│   ├── mychests-gui.yml
│   └── whitelist-gui.yml
├── config.yml
├── hooks.yml
└── lang.yml
</code-block>

### Default Contents
<procedure title="config.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

	# DOCUMENTATION: https://docs.artillex-studios.com/axsellchests.html

	prefix: "<gradient:#FF8800:#FFCC00><b>AxSellChests</b></gradient> &7» "

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

	# used for showing time
	# 1 - HH:MM:SS, for example 01:25:35
	# 2 - short format, for example 20m
	# 3 - text format, for example 01h 25m 35s
	timer-format: 3

	# https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/SimpleDateFormat.html
	# some examples:
	# - day/month/year (most used) format: dd/MM/yyyy hh:mm:ss
	# - month/day/year (usa) format: MM/dd/yyyy h:mm:ss a
	# - year/month/day (default) format: yyyy/MM/dd hh:mm:ss
	date-format: "yyyy/MM/dd HH:mm:ss"

	# aliases for /axsellchests mychests
	# requires a restart for changes to apply
	my-chests-command-aliases:
	  - "mychests"
	  - "axmychests"
	  - "mysellchests"
	  - "axmysellchests"

	# should items be sold when the owner of the sell chest is offline?
	# note that the sell chest will still require the chunk to be loaded
	# if the currency plugin doesn't support offline giving, the currency will be given right on the next join
	offline-selling: true

	# if true: only the player who placed the sell chest can do these actions
	# if false: everyone who can build at the sell chest's location (managed by the hooks.yml protection plugins) can do these actions on sell chests
	only-owner:
	  # changing sell chest settings, charging
	  interact: false
	  # removing sell chests (if false, people will be able to steal each other's sell chests if they have permission to build)
	  break: true

	# should money made and items sold be tracked for every player and sent to players into the chat periodically?
	# set to -1 to disable
	sell-summary-seconds: 180

	# how often should it be possible to click in the gui?
	gui-cooldown-milliseconds: 100

	# the minimum distance between sell chests (in blocks)
	# set to 0 to disable
	minimum-distance: 0

	# should sell chests be put in players' inventory when broken?
	# if false, they will be dropped on the ground
	pickup-to-inventory: true

	# starting sell chest limit (how many different sell chests can be placed?)
	# how the limit is calculated?
	# default + database limit (/axsell chests limit) + permission limit (axsell chests.limit.<amount>)
	# set to -1 to disable sell chest limits
	default-chest-limit: 5

	# if the "delete unsellable" setting is enabled, should the deleted items be counted as "items sold"?
	count-deleted-items: false

	# if disabled, the sell chest charge will only be used when the chest is in a loaded chunk
	# if enabled, the charge counter will decrease even if the chest is not functional
	# note that the charge will not decrease when the server is offline
	always-deplete-charge: false

	# if enabled, when an item is dropped in a chunk that is affected by a
	# sell chest's chunk collector, it will be instantly sold without waiting for the sell timer
	# it will not work if an item goes into the chunk, it must spawn within
	chunk-collect-instant-sell-drops:
	  enabled: true
	  # can be 0, as well, this is just to make it feel less confusing for players
	  # 1 second = 20 ticks
	  delay-ticks: 10

	# if enabled, when a speed booster is active on a sell chest, the charge timer decrease will be multiplied by the booster
	# so the charge will run out much faster when boosted
	speed-booster-affect-charge: false

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
	  boost: "VILLAGER_HAPPY"

	# settings for optimization, don't change these unless you know what they are used for
	cache:
	  # how often should currencies be paid out to the user?
	  payout-seconds: 3
	  # how long should shop prices should be stored per player? (you can increase this if you don't have shop price modifiers, and you don't change prices often)
	  shop-seconds: 60

	# what kind of sell chests protections should be enabled?
	# this is needed to protect sell chests from being broken by game mechanics
	# disabling ones you don't need can improve performance (especially the physics setting)
	# don't disable ones that you don't know what they do as they can lead to sell chests blocks being dupe-able
	enable-protection:
	  # when a block fades, melts or disappears (example: snow, ice, coral)
	  fade: true
	  # when a block is formed or spreads (example: obsidian, concrete)
	  form: true
	  # when a block is destroyed by a fire (example: woods)
	  burn: true
	  # when an entity changes a block
	  change: true
	  # when a tnt or creeper explodes
	  explode: true
	  # when the block is moved by a piston
	  piston: true
	  # when a block is damaged
	  damage: true
	  # when a block decays (example: leaves)
	  decay: true
	  # when a block grows (example: crops)
	  grow: true
	  # when a block changes due to physics (example: sand, gravel)
	  physics: true

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
	  # should text have an outline?
	  shadow: true

	# how often should the plugin save sell chests to the database?
	# requires a restart to change
	# this is in minutes
	auto-save-minutes: 3

	# worlds where you can't place sell chests
	blacklisted-worlds:
	  - "example-world"

	# should be plugin notify you if there is a new update?
	update-notifier:
	  # if enabled, it will display the message in the console
	  enabled: true
	  # if enabled, it will broadcast the update message to all players who have the <plugin-name>.update-notify permission
	  on-join: true

	# prints information about the plugin
	# this can cause a lot of spam, only use if a developer asks you to
	debug: false

	# do not change this
	version: 1

]]>
</code-block>
</procedure>

<procedure title="hooks.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

	# DOCUMENTATION: https://docs.artillex-studios.com/axsellchests.html

	# what plugin to use?
	# used for calculating spawner drop value
	# if multiple is enabled, the highest sell value will be used
	price-plugins:
	  ShopGUIPlus: true
	  Essentials: true
	  EconomyShopGUI: true
	  CMI: true
	  ExcellentShop: true

	# list of supported plugins: https://docs.artillex-studios.com/axsellchests-supported-plugins.html#currency
	currency-plugin:
	  plugin: Vault
	  # this value is only used when the plugin supports multiple currencies
	  currency: ""

	# what plugin should be used for the bank setting?
	# list of supported plugins: https://docs.artillex-studios.com/axsellchests-supported-plugins.html#bank
	bank-plugin: ""

	# what item stacking plugins should we use?
	stacker-plugins:
	  AxStacker: true
	  RoseStacker: true
	  WildStacker: true

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
	  Towny: true
	  Residence: true

	other-plugins:
	  # https://docs.artillex-studios.com/axsellchests-shopguiplus-support.html
	  ShopGUIPlus: true

	# do not change this
	version: 1

]]>
</code-block>
</procedure>

<procedure title="lang.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

	# DOCUMENTATION: https://docs.artillex-studios.com/axsellchests.html

	help:
	  - " "
	  - "<gradient:#FF8800:#FFCC00><b>AxSellChests</b></gradient> <#FFAA00>Help"
	  - " <#FFAA00>➤ <white>/axsellchests reload <#DDDDDD>| <#FFDDAA>Reload plugin"
	  - " <#FFAA00>➤ <white>/axsellchests give <player> <sell chest> [quantity] <#DDDDDD>| <#FFDDAA>Give sell chests"
	  - " <#FFAA00>➤ <white>/axsellchests booster <player> <booster> <multiplier> <length> [quantity] <#DDDDDD>| <#FFDDAA>Give boosters"
	  - " <#FFAA00>➤ <white>/axsellchests stats <#DDDDDD>| <#FFDDAA>Plugin statistics"
	  - " <#FFAA00>➤ <white>/axsellchests logs [player] <#DDDDDD>| <#FFDDAA>Open log gui"
	  - " <#FFAA00>➤ <white>/axsellchests limit give <player> <amount> <#DDDDDD>| <#FFDDAA>Increase sell chest limit of player"
	  - " <#FFAA00>➤ <white>/axsellchests limit take <player> <amount> <#DDDDDD>| <#FFDDAA>Decrease sell chest limit of player"
	  - " <#FFAA00>➤ <white>/axsellchests limit set <player> <amount> <#DDDDDD>| <#FFDDAA>Set sell chest limit of player"
	  - " <#FFAA00>➤ <white>/axsellchests limit reset <player> <#DDDDDD>| <#FFDDAA>Set sell chest limit of player to 0"
	  - " <#FFAA00>➤ <white>/mysellchests <#DDDDDD>| <#FFDDAA>Open my sell chests gui"
	  - " "

	stats:
	  - " "
	  - "<gradient:#FF8800:#FFCC00><b>AxSellChests</b></gradient> <#FFAA00>Statistics"
	  - " <#FFAA00>➤ <white>Total Sell Chests: <#FFDDAA>%total-chests%"
	  - " <#FFAA00>➤ <white>Loaded Sell Chests: <#FFDDAA>%loaded-chests%"
	  - " <#FFAA00>➤ <white>Loaded Chunks: <#FFDDAA>%loaded-chunks%"
	  - " "

	time:
	  second: "s"
	  minute: "m"
	  hour: "h"
	  day: "d"

	give:
	  success: "&#00FF00You have given &#FFFFFF%amount%x %name% &#00FF00to &#FFFFFF%player%&#00FF00!"
	  received: "&#00FF00You have got &#FFFFFF%amount%x %name%&#00FF00!"

	booster:
	  success: "&#00FF00You have given a(n) &#FFFFFF%name% &#00FF00to &#FFFFFF%player%&#00FF00!"
	  received: "&#00FF00You have got a(n) &#FFFFFF%name%&#00FF00!"
	  activated: "&#00FF00You have activated a(n) &#FFFFFF%name% &#00FF00on the sell chest!"
	  already-active: "&#FF0000This booster is already active on this sell chest."
	  disallowed-chest: "&#FF0000This booster can't be used on this sell chest."
	  not-yours: "&#FF0000This sell chest is not yours, so you are not allowed to interact with it!"
	  removed: "&#FF0000You have removed a(n) &#FFFFFF%name% &#FF0000from the sell chest!"
	  no-boosters: "&#FF0000There are no active boosters!"

	chest-gui:
	  enabled: "&#00FF00Enabled"
	  disabled: "&#FF0000Disabled"
	  disallow: "&#FF0000You are not allowed to interact with the sell chest!"
	  not-yours: "&#FF0000This sell chest is not yours, so you are not allowed to interact with it!"
	  not-loaded: "&#FF0000This sell chest is not in a loaded chunk, so it can't be accessed right now!"
	  toggle-on: "&#00FF00You have turned the &#FFFFFF%setting-name% &#00FF00setting on!"
	  toggle-off: "&#FF0000You have turned the &#FFFFFF%setting-name% &#FF0000setting off!"

	settings:
	  auto-sell: "Auto Sell"
	  chunk-collect: "Chunk Collect"
	  delete-unsellable: "Delete Unsellable"
	  bank: "Bank"
	  hologram: "Hologram"

	whitelist:
	  adding: "&#00FF00Write the name of the player in the chat! Write &#FFFFFFcancel &#00FF00to stop!"
	  added: "&#00FF00You have successfully whitelisted &#FFFFFF%player%&#00FF00!"
	  removed: "&#00FF00You have successfully removed &#FFFFFF%player% &#00FF00from the whitelist!"
	  unknown: "&#FF0000No player can be found with the name &#FFFFFF%player%&#FF0000!"
	  self: "&#FF0000You can't whitelist yourself!"
	  already-added: "&#FF0000You have already whitelisted &#FFFFFF%player%&#FF0000!"
	  not-yours: "&#FF0000Only the sell chest's owner can edit the whitelist!"

	place:
	  success: "&#00FF00You have placed &#FFFFFF%name%&#00FF00! &#DDDDDD(%current-limit%/%max-limit%)"
	  add: "&#00FF00You have added &#FFFFFF%name%&#00FF00! &#00FF00The new stack size is: &#FFFFFF%amount%&#00FF00!"
	  disallow: "&#FF0000You are not allowed to place sell chest here!"
	  too-close: "&#FF0000There must be at least &#FFFFFF%distance% &#FF0000blocks between sell chests!"
	  place-limit: "&#FF0000You can't place more sell chest chests, because you have reached the limit. &#DDDDDD(%current-limit%/%max-limit%)"

	break:
	  success: "&#00FF00You have broken &#FFFFFF%name%&#00FF00! &#DDDDDD(%current-limit%/%max-limit%)"
	  disallow: "&#FF0000You are not allowed to break the sell chest!"
	  not-yours: "&#FF0000This sell chest is not yours, so you are not allowed to break it!"

	charge:
	  # used for the %charge-left% placeholder
	  out-of-charge: "Out Of Charge"
	  success: "&#00FF00You have successfully bought &#FFFFFF%charge-buy-time% &#00FF00of charge for &#FFFFFF$%charge-buy-price%&#00FF00!"
	  full: "&#FF0000You can't purchase more charge as the sell chest is already fully charged!"
	  not-enough-money: "&#FF0000You need at least &#FFFFFF$%charge-buy-price% &#FF0000money to charge the sell chest!"

	sell-summary: "&#FFDDAAYour &#FFAA00%chest-count% &#FFDDAAsell chests have sold &#FFAA00%items-sold% &#FFDDAAitems worth &#FFAA00$%money-made% &#FFDDAAin the last &#FFAA00%summary-interval%&#FFDDAA!"

	limit:
	  give: "&#00FF00You have given &#FFFFFF%amount% &#00FF00to the sell chest limit of &#FFFFFF%player%&#00FF00! &#00FF00Their new limit is: &#FFFFFF%new-amount%&#00FF00!"
	  take: "&#00FF00You have took &#FFFFFF%amount% &#00FF00from the sell chest limit of &#FFFFFF%player%&#00FF00! &#00FF00Their new limit is: &#FFFFFF%new-amount%&#00FF00!"
	  set: "&#00FF00You have set the sell chest limit of &#FFFFFF%player% &#00FF00to &#FFFFFF%amount%&#00FF00!"

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

	update-notifier: "&#FFAA00There is a new version of AxSellChests available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"

	# do not change this
	version: 1

]]>
</code-block>
</procedure>

Example Booster configuration (the plugin comes with 2 included)
<procedure title="boosters/money-booster.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

	# DOCUMENTATION: https://docs.artillex-studios.com/axsellchests.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	# list of booster types: money, speed
	type: money

	item:
	  material: PLAYER_HEAD
	  texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZWRiNWNlMGQ0NGMzZTgxMzhkYzJlN2U1MmMyODk3YmI4NzhlMWRiYzIyMGQ3MDY4OWM3YjZiMThkMzE3NWUwZiJ9fX0=
	  name: "<#FFAAAA>%multiplier%x <#FF0000>ᴍᴏɴᴇʏ <white>Booster"
	  lore:
		- ""
		- "<#FF0000><bold>></bold> <#FFAAAA>Increases the money generated by the sell chest."
		- ""
		- "<#FF0000>ꜱᴛᴀᴛꜱ"
		- " <#555555>❙ <#FFFFFF>Multiplier: <#FF0000>%multiplier%x"
		- " <#555555>❙ <#FFFFFF>Booster length: <#FF0000>%length%"
		- " <#555555>❙ <#FFFFFF>Allowed chests: <#FF0000>all"
		- ""
		- "<#FF0000><bold>></bold> <#FFAAAA>Right click on a sell chest while holding to boost."

	# which chests can this booster be applied on?
	# the sell chest's name must be the same as the file name in the chests folder (without the .yml)
	# use * to allow the booster on all chests
	allowed-chests:
	  - "*"

]]>
</code-block>
</procedure>

Example Sell Chest configuration (the plugin comes with 1 included)
<procedure title="chests/basic.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

	# DOCUMENTATION: https://docs.artillex-studios.com/axsellchests.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	# name of the chest, used in place of the %name% placeholder
	name: "<#AAAAAA>(<#FF8800><b>ʙᴀꜱɪᴄ</b><#AAAAAA>) <#FF8800>Sell Chest"

	# what should the material of the chest block be?
	# it must be a container type block, like CHEST, BARREL, SHULKER, etc.
	block: CHEST

	# the sell money multiplier of the chest
	multiplier: 1.0

	# how often should the chest sell its contents?
	# in seconds
	sell-interval-seconds: 10

	# the chest item
	item:
	  material: "CHEST"
	  name: "%name%"
	  lore:
		- ""
		- "<#FF8800>ꜱᴛᴀᴛꜱ"
		- " <#555555>❙ <#FFFFFF>Multiplier: <#FFCC00>%multiplier%x"
		- " <#555555>❙ <#FFFFFF>Charge Left: <#FFCC00>%charge-left%"
		- " <#555555>❙ <#FFFFFF>Items Sold: <#FFCC00>%items-sold%"
		- " <#555555>❙ <#FFFFFF>Money Made: <#FFCC00>$%money-made%"
		- ""
		- "<#FF8800><bold>></bold> <#FFCCAA>Automatically collects and sells items."

	# the text to use in the /mysellchests menu for the sell chest
	gui-lines:
	  - "%name%"
	  - ""
	  - "<#FF8800>ꜱᴛᴀᴛꜱ"
	  - " <#555555>❙ <#FFFFFF>Multiplier: <#FFCC00>%multiplier%x"
	  - " <#555555>❙ <#FFFFFF>Charge Left: <#FFCC00>%charge-left%"
	  - " <#555555>❙ <#FFFFFF>Items Sold: <#FFCC00>%items-sold%"
	  - " <#555555>❙ <#FFFFFF>Money Made: <#FFCC00>$%money-made%"
	  - ""
	  - "<#FF8800>Click <bold>></bold> <#FFCCAA>Open Settings"
	  - "<#FF8800>Shift Click <bold>></bold> <#FFCCAA>Open Inventory"

	# the hologram above the chest
	hologram:
	  enabled: true
	  # how high should the hologram be (the default point is the block itself)
	  height: 1.3
	  lines:
		- "%name%"
		- ""
		- "<#FFFFFF>Owner: <#FFCC00>%owner%"
		- "<#FFFFFF>Multiplier: <#FFCC00>%multiplier%x"
		- "<#FFFFFF>Charge Left: <#FFCC00>%charge-left%"
		- "<#FFFFFF>Items Sold: <#FFCC00>%items-sold%"
		- "<#FFFFFF>Money Made: <#FFCC00>$%money-made%"
		- ""
		- "<#FF8800>Selling in <bold>></bold> <#FFCCAA>%next-sell%"

	# if enabled, sell chests will require charging, which costs money (you can set the currency in the hooks.yml)
	# if a sell chest is not charged, it won't sell items (or it will sell them for less if the uncharged-multiplier is not 0)
	charge:
	  enabled: true
	  # when a new sell chest is created using /give, how much charge should it have?
	  # set to 0 to disable
	  default-charge-seconds: 3600
	  # the maximum charge time that is possible to have
	  # set this to -1 to make it unlimited
	  max-charge-seconds: 3600
	  # how much should it cost to buy charge and how many seconds should 1 purchase add?
	  charging-cost:
		amount: 500
		time-seconds: 60
	  # if the sell chest is not charged, items will be sold at a lower multiplier (this overrides the multiplier if the chest is not charged)
	  # set the multiplier to 0 to make the sell chest stop selling items if it is not charged
	  uncharged-multiplier: 0

	# note: these settings can be modified by players in the chest's gui and these are only the default settings!
	# if you want to make them not editable, remove the button from the gui below!
	settings:
	  # should the chest sell items contents automatically? (see sell-interval-seconds to check how often)
	  auto-sell: true
	  # should the chest pick up all items from the chunk where it is placed?
	  chunk-collect: true
	  # if enabled and an item can't be sold in the enabled shop plugin, (check the hooks.yml for those) the chest will just delete the item
	  delete-unsellable: false
	  # if enabled, money will go to the player's bank (important: you must set a bank plugin up in the hooks.yml for this!)
	  bank: false
	  # should the chest have a hologram above it?
	  hologram: true

	# inventory of the chest where the settings can be tweaked by the player
	inventory:
	  title: "%name% <black>(%owner%)"
	  # inventory rows (1-6)
	  rows: 4
	  # in the items section you can use any part of our gui system, you can add as many items as you want
	  items:
		example-filler:
		  slot: "0-35"
		  material: "ORANGE_STAINED_GLASS_PANE"
		  name: " "
		inventory:
		  slot: 0
		  material: "CHEST"
		  name: "&#FF8800&lꜱᴛᴏʀᴀɢᴇ"
		  lore:
			- "&#DDDDDDOpens the inventory of the chest."
			- "&#DDDDDDNote that all items put in there will be sold."
			- " "
			- "<#FFFFFF>Storage: <#FFCC00>%storage-current%/%storage-full%"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FFCCAAOpen Inventory"
		  actions:
			- "[INVENTORY]"
			- "[SOUND] ui.button.click|1|1"
		statistics:
		  slot: 4
		  material: "BOOK"
		  name: "&#FF8800&lꜱᴛᴀᴛꜱ"
		  lore:
			- " <#555555>❙ <#FFFFFF>Owner: <#FFCC00>%owner%"
			- " <#555555>❙ <#FFFFFF>Multiplier: <#FFCC00>%multiplier%x"
			- " <#555555>❙ <#FFFFFF>Charge Left: <#FFCC00>%charge-left%"
			- " <#555555>❙ <#FFFFFF>Items Sold: <#FFCC00>%items-sold%"
			- " <#555555>❙ <#FFFFFF>Money Made: <#FFCC00>$%money-made%"
			- " "
			- "&#FF8800Selling in &#FF8800&l> &#FFCCAA%next-sell%"
		players:
		  slot: 8
		  material: "WHITE_BANNER"
		  name: "&#FF8800&lᴘʟᴀʏᴇʀꜱ"
		  lore:
			- "&#DDDDDDPlayers who are whitelisted can interact with the"
			- "&#DDDDDDsell chest even if they don't have access to the land."
			- " "
			- "<#FFFFFF>Whitelisted: <#FFCC00>%whitelisted-players% players"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FFCCAAToggle"
		  actions:
			- "[WHITELISTED]"
			- "[SOUND] ui.button.click|1|1"
		auto-sell:
		  slot: 19
		  material: "AMETHYST_SHARD"
		  name: "&#FF8800&lᴀᴜᴛᴏ ꜱᴇʟʟ"
		  lore:
			- "&#DDDDDDAutomatically sells the contents"
			- "&#DDDDDDof the chest every %sell-interval%."
			- " "
			- "<#FFFFFF>Status: <#FFCC00>%auto-sell%"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FFCCAAToggle"
		  actions:
			- "[TOGGLE] auto-sell"
			- "[SOUND] ui.button.click|1|1"
		chunk-collect:
		  slot: 20
		  material: "HOPPER"
		  name: "&#FF8800&lᴄʜᴜɴᴋ ᴄᴏʟʟᴇᴄᴛ"
		  lore:
			- "&#DDDDDDCollects all the items which are"
			- "&#DDDDDDin the same chunk as the chest. &#AAAAAA(F3 + G)"
			- " "
			- "<#FFFFFF>Status: <#FFCC00>%chunk-collect%"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FFCCAAToggle"
		  actions:
			- "[TOGGLE] chunk-collect"
			- "[SOUND] ui.button.click|1|1"
		delete-unsellable:
		  slot: 21
		  material: "FLINT_AND_STEEL"
		  name: "&#FF8800&lᴅᴇʟᴇᴛᴇ ᴜɴꜱᴇʟʟᴀʙʟᴇ"
		  lore:
			- "&#DDDDDDDeletes the items which can"
			- "&#DDDDDDnot be sold in the shop."
			- " "
			- "<#FFFFFF>Status: <#FFCC00>%delete-unsellable%"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FFCCAAToggle"
		  actions:
			- "[TOGGLE] delete-unsellable"
			- "[SOUND] ui.button.click|1|1"
		charge:
		  slot: 22
		  material: "LAVA_BUCKET"
		  name: "&#FF8800&lᴄʜᴀʀɢᴇ"
		  lore:
			- "&#DDDDDDIf the chest is not charged,"
			- "&#DDDDDDit will not sell items."
			- " "
			- "<#FFFFFF>Current charge: <#FFCC00>%charge-left%"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FFCCAABuy &#FF8800+%charge-buy-time% &#FFCCAAfor &#FF8800$%charge-buy-price%"
		  actions:
			- "[CHARGE]"
			- "[SOUND] ui.button.click|1|1"
		bank:
		  slot: 23
		  material: "RAW_GOLD"
		  name: "&#FF8800&lʙᴀɴᴋ"
		  lore:
			- "&#DDDDDDThe auto sell automatically"
			- "&#DDDDDDdeposits the money into the bank."
			- " "
			- "<#FFFFFF>Status: <#FFCC00>%bank%"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FFCCAAToggle"
		  actions:
			- "[TOGGLE] bank"
			- "[SOUND] ui.button.click|1|1"
		hologram:
		  slot: 24
		  material: "ARMOR_STAND"
		  name: "&#FF8800&lʜᴏʟᴏɢʀᴀᴍ"
		  lore:
			- "&#DDDDDDSpawns a hologram with useful"
			- "&#DDDDDDstatistics above the chest block."
			- " "
			- "<#FFFFFF>Status: <#FFCC00>%hologram%"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FFCCAAToggle"
		  actions:
			- "[TOGGLE] hologram"
			- "[SOUND] ui.button.click|1|1"
		boosters:
		  slot: 25
		  material: "BEACON"
		  name: "&#FF8800&lʙᴏᴏꜱᴛᴇʀꜱ"
		  lore:
			- " "
			- "<#FF8800>ʟɪꜱᴛ"
			- " <#555555>❙ <#FFAAAA>%booster-money-multiplier%x <#FF0000>ᴍᴏɴᴇʏ <white>Booster <#AAAAAA>(%booster-money-time%)"
			- " <#555555>❙ <#AAFFFF>%booster-speed-multiplier%x <#00CCFF>ꜱᴘᴇᴇᴅ <white>Booster <#AAAAAA>(%booster-speed-time%)"
			- " "
			- "&#FF8800Click &#FF8800&l> &#FF8800Take Out Boosters"
		  actions:
			- "[TAKE-BOOSTERS]"
			- "[SOUND] ui.button.click|1|1"

]]>
</code-block>
</procedure>

Example GUI configuration (there are 3 different configurable guis)
<procedure title="guis/mychests-gui.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

	# DOCUMENTATION: https://docs.artillex-studios.com/axsellchests.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	title: "%player%'s Sell Chests <#404040>(page #%page%)"
	# a gui can have 1-6 rows
	rows: 5
	# this mustn't be more than the amount of air slots
	page-size: 21

	# ----- ITEMS -----

	example-decoration-blue:
	  slot: [0, 2, 4, 6, 8, 18, 26, 36, 38, 40, 42, 44]
	  material: LIGHT_BLUE_STAINED_GLASS_PANE
	  name: " "

	example-decoration-white:
	  slot: [1, 3, 5, 7, 9, 17, 27, 35, 37, 43]
	  material: WHITE_STAINED_GLASS_PANE
	  name: " "

	previous-page:
	  slot: 39
	  material: "ARROW"
	  name: "&#FF8800&lᴘʀᴇᴠɪᴏᴜs ᴘᴀɢᴇ"
	  lore:
		- " "
		- "&#DDDDDDClick here to go back"
		- "&#DDDDDDto the previous page!"
		- " "
		- "&#FF8800Click &#FF8800&l> &#FFCCAAPrevious Page"
	  actions:
		- "[PAGE] previous"
		- "[SOUND] ui.button.click|1|1"

	next-page:
	  slot: 41
	  material: "ARROW"
	  name: "&#FF8800&lɴᴇxᴛ ᴘᴀɢᴇ"
	  lore:
		- " "
		- "&#DDDDDDClick here to go"
		- "&#DDDDDDto the next page!"
		- " "
		- "&#FF8800Click &#FF8800&l> &#FFCCAANext Page"
	  actions:
		- "[PAGE] next"
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