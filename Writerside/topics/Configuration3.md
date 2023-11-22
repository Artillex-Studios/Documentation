# Configuration

## config.yml

### despawn-time-seconds (default: 180)

* How many seconds should graves stay on the ground?

### drop-items (default: true)

* Should items be dropped on the ground if a grave expires?

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

* true: the head can face in all the 360 degrees
* false: the head can face in only 4 directions (north, east, south, west)

### auto-rotation.enabled (default: false)

* should the heads rotate around like items on the ground?

### auto-rotation.speed (default: 10.0)

* if `auto-rotation` is enabled, how fast should the heads spin?

### blacklisted-items

* Items that match will be removed when the player dies from the grave
* You can also define a material and a name-contains subsection