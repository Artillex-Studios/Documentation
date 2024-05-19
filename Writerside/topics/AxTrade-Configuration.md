# Configuration

## config.yml

### language (default: en_US)

* Format: language_COUNTRY
* After changing this, the server will download the default item names of the set language

### command-aliases

* You can add or edit the command aliases here
* The first element of the list will be used as the "main" command

### trade-confirm-seconds (default: 10)

* The time after clicking the trade confirm button before the trade finishes

### trade-request-expire-seconds (default: 10)

* How fast should trade requests expire?

### trade-max-distance (default: 10)

* How far apart the two players can be from each other?
* Set to -1 to disable

### shift-click-send-request (default: true)

* Should shift + right clicking on another player send them a trade request?

### number-formatting.mode (default: 0)

* 0 - formatted (customizable, look at the formatted part)
* 1 - short (1K)
* 2 - raw (1000.4242421412)

### number-formatting.formatted (default: #,###.##)

* [https://docs.oracle.com/javase/tutorial/i18n/format/decimalFormat.html](https://docs.oracle.com/javase/tutorial/i18n/format/decimalFormat.html)

### number-formatting.short (default: en_US)

* format: language_COUNTRY

### disallowed-gamemodes (default: SPECTATOR)

* List of gamemodes: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/GameMode.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/GameMode.html)
* You can't trade in these gamemodes

### blacklisted-worlds (default: example_world)

* Worlds where trades will not work

### blacklisted-items

* Disallowed/Blacklisted items
* You can also define a material and a name-contains subsection