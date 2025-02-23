# Configuration

## config.yml

### despawn-time-seconds (default: 180)

* How many seconds should graves stay on the ground?
* Set to -1 to make it only despawn after a server restart

### drop-items (default: true)

* Should items be dropped on the ground if a grave expires?

### dropped-item-velocity (default: true)

* If set to false, all items will stay on the same block, they will not fly around when a grave expires.
* This setting only works if `drop-items` is set to true

### enable-instant-pickup (default: true)

* Should any player have the ability to instantly clear all items from the grave?

### instant-pickup-only-own (default: false)

* Should ONLY the player who died should be able to instantly clear all items from the grave?

### override-keep-inventory (default: true)

* Should we also spawn graves for players who have keep inventory?
* if false, the plugin will ignore these players

### hologram-height (default: 0.75)

* The height of the hologram above the grave

### head-height (default: -1.2)

* The height of the grave (player head)
* If for some reason a few client would see the grave in the ground you should try to either change this or check out viaversion's `hologram-y` setting

### disabled-worlds

* Worlds where players won't spawn a grave and the vanilla behavior will be active

### rotate-head-360 (default: true)

* True: the head can face in all the 360 degrees
* False: the head can face in only 4 directions (north, east, south, west)

### auto-rotation.enabled (default: false)

* Should the heads rotate around like items on the ground?

### auto-rotation.speed (default: 10.0)

* If `auto-rotation` is enabled, how fast should the heads spin?

### interact-only-own (default: false)

* If true: only the person who died and people with axgraves.admin can open the grave
* If false: everyone can open the grave

### xp-keep-percentage (default: 1.0)

* How much XP should the player keep on death?
* This is a percentage, so setting this to 0.5 will half the xp kept.

### store-xp (default: true)

* Should the plugin store XP in graves?
* If disabled, XP will be dropped on the ground

### grave-item-order (values: ARMOR, HAND, OFFHAND)

* What order should items go in the grave?
* Some players prefer if they get the armor first and not the sword.

### auto-equip-armor (default: true)

* Should the armor be equipped when collecting the grave?

### grave-limit (default: -1)

* How many graves can a player have at once?
* If the player hits the limit, the oldest grave will be removed.
* You can override this by giving players the axgraves.limit.<amount> permissions

### spawn-height-limits

* Allows you to define the maximum and minimum Y coordinate that a grave can spawn at in a specific world.

### blacklisted-death-causes

* If players die from any of the following, no graves will be spawned
* [Link to the list of death causes. Note that some of them don't exist in older versions](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html)
* Case sensitive

### despawn-when-empty (default: true)
* Should the grave despawn when all the items & xp is removed from it?

### blacklisted-items

* Items that match will be removed when the player dies from the grave
* You can also define a material and a name-contains subsection