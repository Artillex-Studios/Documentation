# Configuration

### auto-save-minutes (default: 5)

* How often should shulkers in memory be saved to the database?

### enable-obsfucation (default: false)

* If enabled: does not save items to the shulker item, this makes it impossible to ever see the items in a shulker box without opening it, may break other plugin's shulker viewers

### open-cooldown-miliseconds (default: 0)

* How long should players have to wait between opening and closing shulkers?
* This is not required to prevent dupes, it is just a feature!
* Set to 0 to disable.

### opening-from-inventory.enabled (default: true)

* Should players have to ability to open shulkers by right clicking on them from their own inventory?

### opening-from-inventory.open-from-enderchest (default: true)

* If `opening-from-inventory.enabled` is true, should this also apply to ender chests?

### disable-shulker-opening (default: false)

* Safety feature, let's you disable shulker opening if needed.

### disable-shulker-placing (default: false)

* Safety feature, let's you disable shulker placing if needed.

### disable-shulker-dispensing (default: false)

* Safety feature, makes it that dispensers and droppers can't dispense shulkers if needed.

### undestoryable-shulkers (default: false)

* If this is true then shulkers will be immune to cactus, lava, fire, etc..

### auto-clear-shulkers (default: false)

* EXPERIMENTAL: This feature may cause issues right now!
* If enabled: when you close a shulker and the plugin validated that it can be saved, then the plugin will save the items from memory to the item just like in vanilla, this makes axshulkers compatibly with everything
* This setting force disables `enable-obsfucation`

### blacklisted-items

* Items that match will be removed when the player dies from the grave
* You can also define a material and a name-contains subsection