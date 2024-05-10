# Configuration

## config.yml

### include-global-permissions (default: false)

* if false: The plugin will display ONLY the permissions that have the same server [context](https://luckperms.net/wiki/Context) as the server where the meunu is opened.
* if true: The plugin will also display ALL the permissions that does not have a [context](https://luckperms.net/wiki/Context) (so GLOBAL permissions).

so for example:
* `auction.sell.5` with a `server=survival` context will be shown as long as you are on the survival no matter the setting
* `auction.sell.5` without context will only be shown if you set it to true

### prevent-downgrading (default: true)

* The plugin will stop players from buying worse ranks than their current one
* You must set every rank a WEIGHT (weight.&lt;VALUE> permission) to enable

### discount-ranks (default: false)

* If true: every rank's price will be calculated like this: new rank's price - current rank's price 
* NOTE: unless prevent-downgrading is true this will mean what players can freely downgrade their ranks

### force-buy-order.enabled (default: false)

* The plugin will not let the player buy ranks out of order
* This uses the builtin track system of luckperms, you must define one to use it

### command-aliases

* You can add or edit the command aliases here
* The first element of the list will be used as the "main" command

## lang.yml

You can define translations for the permissions with the `permissions` section. Examples:

`exampleplugin.simple: ""`
* This is how you can translate a simple permission

`exampleplugin.uses.#: ""`
* Replace numbers with a # and the plugin will automatically translate all the related permissions
* for example: `"auction.sell.#": "You can have # auctions!"` will work for the `auction.sell.5` and `auction.sell.10` without having to add them both!

`exampleplugin.admin": ""`
* Setting a permission to "" will make it not show up in the rank menu