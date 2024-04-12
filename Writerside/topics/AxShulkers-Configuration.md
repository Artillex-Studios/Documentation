# Configuration

### auto-save-minutes (default: 5)

* How often should shulkers in memory be saved to the database?

### enable-obfuscation (default: false)

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

* Lets you disable shulker opening if needed.

### disable-shulker-placing (default: false)

* Lets you disable shulker placing if needed.

### disable-shulker-dispensing (default: false)

* Makes it that dispensers and droppers can't dispense shulkers if needed.

### disable-moving-while-open (default: false)

* If this is true, the shulker will be closed if the player moves

### undestoryable-shulkers (default: false)

* If this is true then shulkers will be immune to cactus, lava, fire, etc..

### auto-clear-shulkers (default: false)

* EXPERIMENTAL: This feature may cause issues
* If enabled: when you close a shulker and the plugin validated that it can be saved, then the plugin will save the items from memory to the item just like in vanilla, this makes axshulkers compatibly with everything
* This setting force disables `enable-obfuscation`

### auto-clear-in-creative (default: true)

* The same as auto-clear-shulkers, however this is only for creative mode players!
* This is highly recommended to keep enabled to avoid confusion.

### delete-invalid-items (default: true)

* If enabled and somehow a shulker has a uuid, but it is not in the database, the contents of that shulker will be removed
* This also required to prevent incompatibility with third party plugins
* The only reason you should disable this is if you decided to delete the axshulkers database without resetting players' shulkers

### nbt-tag (default: AxShulkers-UUID)

* What should the nbt that the plugin places on shulkers be named?
* Note that the plugin will not clean up old ones, so changing this is not recommended
* Changing this while the server is running can lead to dupes
* If you have deleted the axshulkers database without deleting the items, it is recommended to change this to avoid item loss

### blacklisted-items

* Disallowed/Blacklisted items
* You can also define a material and a name-contains subsection