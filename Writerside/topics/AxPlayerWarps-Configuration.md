# Configuration

<procedure title="config.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axplayerwarps.html

	prefix: "<gradient:#33EEBB:#3388BB><b>AxPlayerWarps</b></gradient> &7» "

	database:
	  # options: h2, mysql, postgresql
	  type: "h2"

	  # you only need to touch these when using mysql or postgresql
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

	# you must define at least 1
	# requires a restart to update
	main-command-aliases:
	  - "axplayerwarps"
	  - "axpw"
	  - "pw"
	  - "playerwarps"
	  - "playerwarp"
	  - "pwarp"
	  - "pwarps"

	# requires a restart to update
	admin-command-aliases:
	  - "axplayerwarpsadmin"
	  - "axpwadmin"
	  - "pwadmin"
	  - "playerwarpsadmin"
	  - "playerwarpadmin"
	  - "pwarpadmin"
	  - "pwarpsadmin"

	warp-creation-cost:
	  # should creating warps cost money?
	  enabled: false
	  # ask player for a confirmation to make sure
	  # that they are aware of the price of the warp creation
	  confirm: true
	  # price of creation
	  price: 1000
	  # currencies are defined in the currencies.yml
	  currency: Vault

	warp-naming:
	  # allowing spaces might make it hard to tab complete warps
	  allow-spaces: false
	  length:
		min: 1
		max: 16

	# which material should we use if the player doesn't define an icon for their warp?
	# PLAYER_HEAD will default to the owner's skull (note: sometimes it may not load)
	default-material: "PLAYER_HEAD"

	# how much time do players have to confirm if a warp is unsafe or paid
	confirmation-milliseconds: 10000

	# how many seconds before the player gets teleported?
	# if they move, the teleport will be cancelled
	# you can bypass this with the axplayerwarps.delay-bypass permission
	teleport-delay-seconds: 3

	warp-description:
	  # how many line of description can players write for their pwarp?
	  max-lines: 3
	  default: "No description provided."

	# example values: categories, warps
	# if you want to disable categories, make sure to change this to warps
	default-gui: "categories"

	# commands that will be run when a player teleports to a warp
	# you can use all warp placeholders (like %name%, %x%, %y%, %x%, etc..) and %player% for the player's name
	# example:
	# - "say %player% teleported to the %name% player warp!"
	# make sure to remove the [] to enable this feature
	teleport-commands: []

	# to disable categories you can set this to []
	# also make sure to remove the category selector from the gui
	#
	# you can add/remove categories here
	categories:
	  building:
		name: "Building"
	  shop:
		name: "Shop"
	  farm:
		name: "Farm"
	  pvp:
		name: "PvP"
	  event:
		name: "Event"
	  fun:
		name: "Fun"
	  special:
		name: "Special"
	  other:
		name: "Other"

	# this is all the possible sorting that you can enable/disable
	# forwards: it goes in the original direction, for example forwards rating = it will go from the highest rating to the lowest rating
	# backwards: it goes in the opposite direction, for example backwards rating = it will go from the lowest rating to the highest rating
	# if you disable any of them, it will not show up in the sorting button
	# you can define the default by setting default to true, NOTE that only 1 sorting can be the default!
	sorting:
	  alphabetical:
		forwards:
		  enabled: true
		  default: true
		  name: "A to Z"
		backwards:
		  enabled: true
		  name: "Z to A"
	  visits:
		forwards:
		  enabled: true
		  name: "Most visits"
		backwards:
		  enabled: true
		  name: "Least visits"
	  rating:
		forwards:
		  enabled: true
		  name: "Highest rating"
		backwards:
		  enabled: true
		  name: "Lowest rating"
	  rating_count:
		forwards:
		  enabled: true
		  name: "Most rated"
		backwards:
		  enabled: true
		  name: "Least rated"
	  favorites:
		forwards:
		  enabled: true
		  name: "Most favorited"
		backwards:
		  enabled: true
		  name: "Least favorited"
	  distance:
		forwards:
		  enabled: true
		  name: "Closest"
		backwards:
		  enabled: true
		  name: "Furthest"
	  creation_date:
		forwards:
		  enabled: true
		  name: "Newest"
		backwards:
		  enabled: true
		  name: "Oldest"

	# https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/SimpleDateFormat.html
	# some examples:
	# - day/month/year (most used) format: dd/MM/yyyy hh:mm:ss
	# - month/day/year (usa) format: MM/dd/yyyy h:mm:ss a
	# - year/month/day (default) format: yyyy/MM/dd hh:mm:ss
	date-format: "yyyy/MM/dd HH:mm:ss"

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

	# prints out a lot of random information about the plugin in the console
	# only use if the developers ask you for this
	debug: false

	# do not change this
	version: 3
]]>
</code-block></step>
</procedure>

<procedure title="currencies.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axplayerwarps.html

	# you can create your own currencies by using placeholders
	# make sure that none of the placeholders have any formatting on them
	# requires PlaceholderAPI
	placeholder-currencies:
	  Example-Currency:
		register: false
		name: "money"
		# if the currency uses whole numbers, then disable this
		# 100.5 - true
		# 100 - false
		uses-double: true
		# if the placeholder gets parsed even for offline players, enable this
		works-offline: false
		settings:
		  raw-placeholder: "%vault_eco_balance_fixed%"
		  give-command: "eco give %player% %price%"
		  take-command: "eco take %player% %price%"

	# INFO FOR MULTI CURRENCY PLUGINS: (like: coinsengine, ultraeconomy, rediseconomy)
	# - you can enable as many currencies as you want, just add the sections the same way as in the example
	currencies:
	  Experience:
		register: true
		name: "%price% exp"
	  Vault:
		register: true
		name: "%price% money"
	  PlayerPoints:
		register: true
		name: "%price% points"
	  RoyaleEconomy:
		register: true
		name: "%price% money"
	  CoinsEngine:
		register: true
		enabled:
		  - currency-name: "coins"
			name: "%price% coins"
		  - currency-name: "money"
			name: "%price% money"
	  UltraEconomy:
		register: true
		enabled:
		  - currency-name: "coins"
			name: "%price% coins"
	  KingdomsX:
		register: true
		name: "%price% nexus points"
	  RivalHarvesterHoes:
		register: true
		name: "%price% essence"
	  SuperMobCoins:
		register: true
		name: "%price% mobcoin"
	  TheOnly-MobCoins:
		register: true
		name: "%price% mobcoins"
	  TokenManager:
		register: true
		name: "%price% tokens"
	  AxQuestBoard:
		register: true
		name: "%price% quest points"
	  RedisEconomy:
		register: true
		enabled:
		  - currency-name: "coins"
			name: "%price% coins"
	  BeastTokens:
		register: true
		name: "%price% tokens"
	  EcoBits:
		register: true
		enabled:
		  - currency-name: "crystals"
			name: "%price% crystals"

	# do not change this
	version: 1
]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axplayerwarps.html

	help:
	  - " "
	  - "<gradient:#33EEBB:#3388BB><b>AxPlayerWarps</b></gradient> &7» &#BBFFDDHelp:"
	  - "  &7⋆ &f/axpw [open] [player] &7| &#BBFFDDOpen warp menu"
	  - "  &7⋆ &f/axpw create <name> &7| &#BBFFDDCreate warp"
	  - "  &7⋆ &f/axpw delete <warp> &7| &#BBFFDDDelete warp"
	  - "  &7⋆ &f/axpw edit <warp> &7| &#BBFFDDOpen warp editor"
	  - "  &7⋆ &f/axpw warp <warp> &7| &#BBFFDDTeleport to warp"
	  - "  &7⋆ &f/axpw info <warp> &7| &#BBFFDDWarp information"
	  - " "

	admin-help:
	  - " "
	  - "<gradient:#33EEBB:#3388BB><b>AxPlayerWarps</b></gradient> &7» &#BBFFDDAdmin Help:"
	  - "  &7⋆ &f/axpwadmin reload &7| &#BBFFDDReload plugin"
	  - "  &7⋆ &f/axpwadmin delete <warp> &7| &#BBFFDDDelete warp"
	  - "  &7⋆ &f/axpwadmin setowner <warp> <player> &7| &#BBFFDDSet owner of warp"
	  - " "

	access:
	  private: "&#EE0000Private"
	  whitelisted: "&#EEEE00Whitelisted"
	  public: "&#00EE00Public"

	placeholders:
	  no-category: "---"
	  free: "Free"
	  no-rating: "No Rating"
	  star:
		bright: "&#FFFF00⭐"
		dark: "&#DDDDDD⭐"
	  no-search: "---"
	  warp-not-found: "Warp not found"

	info:
	  - "&#BBFFDD===== &#33EEBB&l%name% &#BBFFDD====="
	  - " "
	  - " &#33EEBBDescription:"
	  - " &#444444❙ &f%description%"
	  - " "
	  - " &#33EEBBInformation"
	  - "   &#444444❙ &#BBFFDDOwner: &f%owner%"
	  - "   &#444444❙ &#BBFFDDCreated: &f%created%"
	  - "   &#444444❙ &#BBFFDDLocation: &f%world%, %x%, %y%, %z%"
	  - "   &#444444❙ &#BBFFDDCategory: &f%category%"
	  - " "
	  - " &#33EEBBStatistics"
	  - "   &#444444❙ &#BBFFDDVisits: &f%visitors_unique%"
	  - "   &#444444❙ &#BBFFDDRating: &#FFDD00%rating_stars%"
	  - "   &#444444❙ &#BBFFDDFavorite of: &f%favorites% players"
	  - " "
	  - " &#33EEBBCost of teleporting: &#BBFFDD%price%"
	  - " &#33EEBBAccess: &#BBFFDD%access%"
	  - " "
	  - "&#BBFFDD===== &#33EEBB&l%name% &#BBFFDD====="

	create:
	  created: "&#BBFFDDYou have successfully created the &#33EEBB%warp% &#BBFFDDwarp!"
	  confirm: "&#BBFFDDCreating a warp will cost you &#33EEBB%price%&#BBFFDD! If you still want to create the warp, type this command again!"

	whitelist:
	  clear: "&#BBFFDDYou have removed all players from the whitelist!"
	  remove: "&#BBFFDDYou have removed &#33EEBB%player% &#BBFFDDfrom the whitelist!"
	  add: "&#BBFFDDYou have added &#33EEBB%player% &#BBFFDDto the whitelist!"

	blacklist:
	  clear: "&#BBFFDDYou have removed all players from the blacklist!"
	  remove: "&#BBFFDDYou have removed &#33EEBB%player% &#BBFFDDfrom the blacklist!"
	  add: "&#BBFFDDYou have added &#33EEBB%player% &#BBFFDDto the blacklist!"

	search:
	  show: "&#BBFFDDShowing search results for &#33EEBB%search%&#BBFFDD!"
	  reset: "&#BBFFDDDisabled search!"

	rate:
	  add: "&#BBFFDDYou have added a &#33EEBB%rating% &#BBFFDDstar review to this warp!"
	  remove: "&#BBFFDDYou have removed your rating of this warp!"

	favorite:
	  add: "&#BBFFDDYou have added the warp to your favorites!"
	  remove: "&#BBFFDDYou have removed this warp from your favorites!"

	editor:
	  update-location: "&#BBFFDDYou have changed the warp's location!"
	  update-name: "&#BBFFDDYou have changed the warp's name!"
	  update-icon: "&#BBFFDDYou have changed the warp's icon!"
	  remove-icon: "&#BBFFDDYou have removed the warp's icon!"
	  transferred: "&#BBFFDDYou have transferred the warp's ownership to &#33EEBB%player%&#BBFFDD!"
	  new-owner: "&#33EEBB%player% &#BBFFDDhas transferred the ownership of the &#33EEBB%warp% &#BBFFDDwarp to you!"

	delete:
	  deleted: "&#BBFFDDYou have deleted the &#33EEBB%warp% &#BBFFDDwarp!"

	teleport:
	  success: "&#BBFFDDYou have successfully teleported to the &#33EEBB%warp% &#BBFFDDwarp!"
	  in: "&#BBFFDDYou will be teleported in &#33EEBB%seconds% &#BBFFDDseconds! Do not move!"

	confirm:
	  unsafe: "&#BBFFDDThe &#33EEBB%warp% &#BBFFDDwarp is &#FF0000&nnot safe&#BBFFDD! Warp again to confirm if you still want to teleport!"
	  paid: "&#BBFFDDTeleporting to the &#33EEBB%warp% &#BBFFDDwarp is going to cost &#33EEBB%price%&#BBFFDD! Warp again to confirm if you still want to teleport!"

	money:
	  take: "&#33EEBB%price% &#BBFFDDwas removed from your balance!"
	  got: "&#BBFFDDYou have withdrawn &#33EEBB%price% &#BBFFDDfrom the warp's bank!"

	admin:
	  deleted: "&#FF4444You have deleted the &#FF0000%warp% &#FF4444warp!"
	  setowner: "&#FF4444You have transferred the &#FF0000%warp% &#FF4444warp to &#FF0000%player%&#FF4444!"

	errors:
	  disallowed-name-space: "&#FF4444The given warp name cannot contain spaces!"
	  disallowed-name-length: "&#FF4444The length of the given warp name is too short or too long!"
	  blacklist-self: "&#FF4444You can't blacklist yourself!"
	  whitelist-self: "&#FF4444You can't whitelist yourself!"
	  player-not-found: "&#FF4444This player has never played on the server!"
	  not-a-number: "&#FF4444The given value is not a valid number!"
	  must-be-positive: "&#FF4444The given value is not a positive number!"
	  invalid-name: "&#FF4444The given name is not valid."
	  name-exists: "&#FF4444A warp with this name already exists."
	  max-lines: "&#FF4444You can not add more lines to the warp's description!"
	  not-enough-balance: "&#FF4444You do not have enough money to teleport to this warp!"
	  create-not-enough-currency: "&#FF4444You need to have &#FF0000%price% &#FF4444to create a warp!"
	  cannot-create-here: "&#FF4444You can't create a warp here, because it is in a protected area."
	  blacklisted: "&#FF4444You can not teleport to the &#FF0000%warp% &#FF4444warp, because you are blacklisted!"
	  whitelisted: "&#FF4444You can not teleport to the &#FF0000%warp% &#FF4444warp, because it is whitelisted and you are not on the whitelist!"
	  private: "&#FF4444The &#FF0000%warp% &#FF4444is currently set to private, only the owner can teleport to it!"
	  invalid-world: "&#FF4444Teleport failed, this warp is in a world that does not exist anymore!"
	  moved: "&#FF4444You have moved, so the teleport was cancelled!"
	  not-found: "&#FF4444Warp with name &#FF0000%warp% &#FF4444not found!"
	  limit-reached: "&#FF4444You have reached the warp limit, you can not create any more warps! &#FF4444(&#FF0000%current%&#FF4444/&#EE0000%limit%&#FF4444)"
	  nothing-withdrawable: "&#FF4444There is no money to be withdrawn!"
	  not-your-warp: "&#FF4444This is not your warp!"

	time:
	  second: "s"
	  minute: "m"
	  hour: "h"
	  day: "d"

	converting: "&#33FF33Started converter, check the console for more information!"

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

	update-notifier: "&#88CCFFThere is a new version of AxPlayerWarps available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"

	# do not change this
	version: 2
]]>
</code-block></step>
</procedure>

<procedure title="input.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axplayerwarps.html
	#
	# valid types:
	#  - sign (sign gui)
	#  - anvil (anvil gui)
	#  - chat (input in chat)
	#
	# note: only the selected type's section will be used, you can even delete the unused ones if you want

	# if the player writes any of these in chat mode, the plugin will cancel the input
	# make sure to change this in the messages as well if you change it here!
	chat-cancel-words:
	  - "cancel"

	rate:
	  type: "anvil"
	  # keep the first line empty when using sign
	  sign:
		- " "
		- "-----------"
		- "Write new rating!"
		- "Valid values: 1-5"
	  anvil:
		title: "&0Rate Warp"
		item:
		  material: PAPER
		  glow: true
		  name: "&fRATING HERE"
		  lore:
			- "&#33EEBBValid values: 1-5"
	  chat:
		- "&#33EEBBWrite your rating in the chat: &#DDDDDD(write &#33EEBBcancel &#DDDDDDto stop)"
		- "&#DDDDDDValid values: 1-5"

	search:
	  type: "chat"
	  # keep the first line empty when using sign
	  sign:
		- " "
		- "-----------"
		- "Search for warp"
		- "in the first line!"
	  anvil:
		title: "&0Search Here"
		item:
		  material: PAPER
		  glow: true
		  name: "&fSEARCH HERE"
		  lore:
			- "&#33EEBB↑ searching for"
	  chat:
		- "&#33EEBBWhat do you want to search for? &#DDDDDD(write &#33EEBBcancel &#DDDDDDto stop)"

	rename:
	  type: "anvil"
	  # keep the first line empty when using sign
	  sign:
		- " "
		- "-----------"
		- "Write new name"
		- "in the first line!"
	  anvil:
		title: "&0Rename Warp"
		item:
		  material: PAPER
		  glow: true
		  name: "&fNEW NAME HERE"
		  lore:
			- "&#33EEBB↑ new name"
	  chat:
		- "&#33EEBBWrite the new warp name in the chat: &#DDDDDD(write &#33EEBBcancel &#DDDDDDto stop)"

	price:
	  type: "anvil"
	  # keep the first line empty when using sign
	  sign:
		- " "
		- "-----------"
		- "Write new price"
		- "in the first line!"
	  anvil:
		title: "&0New Price"
		item:
		  material: PAPER
		  glow: true
		  name: "&fPRICE HERE"
		  lore:
			- "&#33EEBB↑ price"
	  chat:
		- "&#33EEBBWrite the new price in the chat: &#DDDDDD(write &#33EEBBcancel &#DDDDDDto stop)"

	add-line:
	  type: "chat"
	  # keep the first line empty when using sign
	  sign:
		- " "
		- "-----------"
		- "Write new text"
		- "in the first line!"
	  anvil:
		title: "&0Add Line"
		item:
		  material: PAPER
		  glow: true
		  name: "&fNEW LINE HERE"
		  lore:
			- "&#33EEBB↑ new line"
	  chat:
		- "&#33EEBBWrite the new line in the chat: &#DDDDDD(write &#33EEBBcancel &#DDDDDDto stop)"

	add-player:
	  type: "anvil"
	  # keep the first line empty when using sign
	  sign:
		- " "
		- "-----------"
		- "Write the name"
		- "in the first line!"
	  anvil:
		title: "&0Add Player"
		item:
		  material: PAPER
		  glow: true
		  name: "&fPLAYER'S NAME HERE"
		  lore:
			- "&#33EEBB↑ name of player"
	  chat:
		- "&#33EEBBWrite the name of the player in the chat: &#DDDDDD(write &#33EEBBcancel &#DDDDDDto stop)"

	transfer:
	  type: "anvil"
	  # keep the first line empty when using sign
	  sign:
		- " "
		- "-----------"
		- "Write the name"
		- "in the first line!"
	  anvil:
		title: "&0Add Player"
		item:
		  material: PAPER
		  glow: true
		  name: "&fPLAYER'S NAME HERE"
		  lore:
			- "&#33EEBB↑ name of player"
	  chat:
		- "&#33EEBBWrite the name of the player in the chat: &#DDDDDD(write &#33EEBBcancel &#DDDDDDto stop)"

	# do not change this
	version: 1
]]>
</code-block></step>
</procedure>

**There are many GUI configs, here is one:**
<procedure title="guis/warps.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	# DOCUMENTATION: https://docs.artillex-studios.com/axplayerwarps.html
	# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html

	title: "&0&lAxPWarps > &8Warps (%page%/%pages%)"
	# a gui can have 1-6 rows
	rows: 6
	# how many items should be shown on a single page?
	page-size: 45

	# ----- WARP ITEM -----

	warp:
	  name: "&#33EEBB&l%name%"
	  lore:
		- " "
		- "&#33EEBBDescription:"
		- "&#444444❙ &f%description%"
		- " "
		- "&#33EEBBInformation"
		- "  &#444444❙ &#BBFFDDOwner: &f%owner%"
		- "  &#444444❙ &#BBFFDDCreated: &f%created%"
		- "  &#444444❙ &#BBFFDDLocation: &f%world%, %x%, %y%, %z%"
		- "  &#444444❙ &#BBFFDDCategory: &f%category%"
		- " "
		- "&#33EEBBStatistics"
		- "  &#444444❙ &#BBFFDDVisits: &f%visitors_unique%"
		- "  &#444444❙ &#BBFFDDRating: &#FFDD00%rating_stars%"
		- "  &#444444❙ &#BBFFDDFavorite of: &f%favorites% players"
		- " "
		- "&#33EEBBCost of teleporting: &#BBFFDD%price%"
		- "&#33EEBBAccess: &#BBFFDD%access%"
		- " "
		- "&#33EEBB&lLeft Click &#DDDDDD» &#BBFFDDTeleport"
		- "&#33EEBB&lRight Click &#DDDDDD» &#BBFFDDReview & Options"

	# ----- ITEMS -----

	my-warps:
	  slot: 45
	  # this font is called 'small caps'
	  name: "&#33EEBB&lᴍʏ ᴡᴀʀᴘs"
	  type: ENDER_PEARL
	  lore:
		- " "
		- " &fClick here to view/edit/delete"
		- " &fyour &#33EEBB%my_warps% &fwarps!"
		- " "
		- "&#33EEBB&lClick &#DDDDDD» &#BBFFDDOpen My Warps"
	  actions:
		- "[MENU] my-warps"
		- "[SOUND] ui.button.click|1|1"

	sorting:
	  slot: 46
	  material: "GLOWSTONE_DUST"
	  name: "&#33EEBB&lsᴏʀᴛɪɴɢ"
	  lore:
		- " "
		- " &#33EEBBCurrently selected:"
		- "  &#444444❙ &#BBFFDD%sorting_selected%"
		- " "
		- "&#33EEBB&lClick &#DDDDDD» &#BBFFDDChange Sorting"
		- "&#33EEBB&lShift + Click &#DDDDDD» &#BBFFDDReset Sorting"
	  actions:
		- "[SOUND] ui.button.click|1|1"

	previous-page:
	  slot: 48
	  material: "ARROW"
	  name: "&#33EEBB&lᴘʀᴇᴠɪᴏᴜs ᴘᴀɢᴇ"
	  lore:
		- " "
		- " &fClick here to go back"
		- " &fto the previous page!"
		- " "
		- "&#33EEBB&lClick &#DDDDDD» &#BBFFDDPrevious Page"
	  actions:
		- "[SOUND] ui.button.click|1|1"
		- "[PAGE] previous"

	refresh:
	  slot: 49
	  material: "SUNFLOWER"
	  name: "&#33EEBB&lʀᴇғʀᴇsʜ"
	  lore:
		- " "
		- " &fClick here to"
		- " &frefresh the page!"
		- " "
		- "&#33EEBB&lClick &#DDDDDD» &#BBFFDDRefresh Page"
	  actions:
		- "[SOUND] ui.button.click|1|1"
		- "[REFRESH]"

	next-page:
	  slot: 50
	  material: "ARROW"
	  name: "&#33EEBB&lɴᴇxᴛ ᴘᴀɢᴇ"
	  lore:
		- " "
		- " &fClick here to go"
		- " &fto the next page!"
		- " "
		- "&#33EEBB&lClick &#DDDDDD» &#BBFFDDNext Page"
	  actions:
		- "[SOUND] ui.button.click|1|1"
		- "[PAGE] next"

	category:
	  slot: 52
	  material: "HOPPER"
	  name: "&#33EEBB&lᴄᴀᴛᴇɢᴏʀʏ"
	  lore:
		- " "
		- " &#33EEBBCurrently selected:"
		- "  &#444444❙ &#BBFFDD%category_selected%"
		- " "
		- "&#33EEBB&lClick &#DDDDDD» &#BBFFDDChange Category"
		- "&#33EEBB&lShift + Click &#DDDDDD» &#BBFFDDDelete Category Filter"
	  actions:
		- "[SOUND] ui.button.click|1|1"

	search:
	  slot: 53
	  material: "SPYGLASS"
	  name: "&#33EEBB&lsᴇᴀʀᴄʜ ᴡᴀʀᴘs"
	  lore:
		- " "
		- " &fClick here to search for warps by"
		- " &ftheir name or by their owner's name!"
		- " "
		- "&#33EEBBCurrent search: &#BBFFDD%search%"
		- " "
		- "&#33EEBB&lClick &#DDDDDD» &#BBFFDDSearch"
		- "&#33EEBB&lShift + Click &#DDDDDD» &#BBFFDDClear Search"
	  actions:
		- "[SOUND] ui.button.click|1|1"

	#decoration-example:
	#  slot: 10
	#  type: STONE
	#  name: "&eDecoration!"
	#  actions:
	#    - "[MENU] close"
	#    - "[MESSAGE] &#FF0000Message"
]]>
</code-block></step>
</procedure>