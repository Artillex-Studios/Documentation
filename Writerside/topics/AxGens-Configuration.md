# Configuration

## config.yml

### default-max-generators: (default: 5)

* The starting generator amount that a player will have.

<warning>Setting an 'axgens.limit.AMOUNT' permission will override this value! It does not add to it!</warning>

### generator-min-distance (default: 0.0)

* The minimum distance that 2 generators can have between each other.

### pickup-to-inv (default: true)

* Should generators be put in your inventory when you break one?

### only-owner-interact (default: false)

* if true: only the generator's owner and people with the permission axgens.admin will be able to interact with generators
* if false: everyone who can break blocks at the generator's location will be able to upgrade or pick up the generator
* you should enable this if aren't using a supported protection plugin

### hologram-update-speed (default: 1)

* How often should the generator's holograms should update?
* Note: this value is in ticks `1 seconds = 20 tick`

### sell-command (default: true)

* Should the `/selldrops` command be enabled?
* You should disable this if you are using another plugin for the prices

### force-register-sell (default: false)

* Forces the /sell command to be the /selldrops
* This is only recommended if you can't disable other plugins' /sell

### level-requirements (default: true)

* Should the level system be active?
* Note: you will also have to delete some lines from the `tiers.yml` if you don't want levels to show up

### right-click-upgrading (default: true)

* Should generators get upgraded when you shift right click on it?

### enable-gui (default: true)

* Should the GUI be opened when you right click a generator?

### timer-format (default: 1)

* This format is used for the `axgens_nextevent` placeholder. There are 3 modes:
  * 1 - HH:MM:SS, for example 01:25:35
  * 2 - short format, for example 20m
  * 3 - text format, for example 01h 25m 35s

### speed-display (default: 1)

* The time shown in generator lores, holograms, etc. There are 3 modes:
  * 1 - ticks
  * 2 - seconds
  * 3 - miliseconds

### offline-generation (default: true)

* Should generators work when the owner is offline?

### prevent-drop-usage (default: false)

* If enabled, it will add an extra NBT tag to all drops, and pevents the dropped items from being placed or crafted.

### generator-limit-hard-cap (default: -1)

* Allows you to set a hard cap to generator slots, that is not bypassable not even with permissions.
* Set to -1 to disable.