# Sell wands

Sell wands are used to sell items from a container. You can add sell wands in the `config.yml`, look for a `sellwands` section!

`multiplier: 1.5`
* The multiplier will increase the money that the sell wand will make, this is a simple calculation: `price * multiplier`

`uses: 100`
* The amount of times a single sell wand can be used. If the uses go below 0, then the next use will break the sell wand.
* Setting uses to `-1` will make the sell wand unbreakable.

`cooldown-miliseconds`
* You can set delay between sell wand uses. This is stored ON the sell wand item, so it is not per player, you can set it to multiple hours or days and the plugin will remember even after a restart.
* Note: this is in miliseconds, `1 second = 1000 miliseconds`