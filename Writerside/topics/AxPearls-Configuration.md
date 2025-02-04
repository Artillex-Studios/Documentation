# Configuration

<procedure title="config.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axpearls.html

	prefix: "<gradient:#00FFAA:#00CCAA><b>AxPearls</b></gradient> &7» "

	# if enabled and a team plugin is installed, (check hooks.yml)
	# pearls will go through your teammates
	teammate-pearl-passthrough: true

	# allow players to squeeze themselves into places with ender pearls where they can only fit in swimming mode?
	allow-swimming-mode: true

	# how likely should it be that after a pearl teleport, an endermite will spawn?
	# 0 to 100 (in percents)
	# in vanilla, this is set to 5.0
	# set to 0 to disable
	endermite-spawn-chance: 0.0

	# how much damage should the player take when their ender pearl lands
	# in vanilla, this is set to 5.0
	# set to 0 to disable
	ender-pearl-damage: 5.0

	# how much damage should players take when they get hit by an ender pearl?
	# in vanilla, this is set to 0.0
	# set to 0 to disable
	ender-pearl-hit-damage: 0.0

	# should pearls be able to go through open gates?
	open-gate-passthrough: true

	# pearl cooldown in milliseconds
	# you can give per player cooldown with the "axpearls.cooldown.<milliseconds>" permission
	# set to -1 to disable
	pearl-cooldown-milliseconds: 5000

	# should the plugin override the vanilla ender pearl cooldown display?
	show-cooldown-on-item: true

	# if no safe location can be found, should the pearl be refunded?
	refund-on-fail: true

	# syntax: https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html
	# some examples:
	# '0.0' (decimal separator: .)
	# '0,0' (decimal separator: ,)
	# '0' (only show seconds)
	# '0.00' (multiple decimals)
	timer-number-format: "0.0"

	# how far/fast should the ender pearl go?
	# 0.5 will be half speed, 2.0 will be double speed
	# the default/vanilla value is 1.0
	pearl-throw-strength: 1.0

	particle:
	  enabled: true
	  # list of particles: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html
	  type: PORTAL
	  # amount of particles to spawn
	  amount: 32

	# do not change this
	version: 1
	
	]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
	
	# DOCUMENTATION: https://docs.artillex-studios.com/axpearls.html

	help:
	  - " "
	  - "<gradient:#00FFAA:#00CCAA><b>AxPearls</b></gradient> &7» "
	  - " &7- &f/axpearls reload &7| &#AAFFCCReload configuration"
	  - " &7- &f/axpearls reset-cooldown [player] &7| &#AAFFCCReset pearl cooldown of player"
	  - " "

	cooldown: "&#AAFFCCYou can't throw an ender pearl for another &#00CCAA%seconds% &#AAFFCCseconds!"

	# disable message by setting it to pearl-refunded: ""
	pearl-refunded: "&#AAFFCCThere is no safe location, so your ender pearl was refunded!"

	cooldown-removed: "&#AAFFCCYou have removed the ender pearl cooldown of &#00CCAA%player%&#AAFFCC!"

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

	# do not change this
	version: 1
	
	]]>
</code-block></step>
</procedure>