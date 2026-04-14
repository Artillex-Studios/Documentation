# Commands

### Player commands:
*permission: axauctions.use* (given by default)

|-|-|
| Command | Description |
| /ah | Open auction house |
| /ah open [menu] | Open menu |
| /ah sell &lt;price> [amount] | Sell item (opens currency selector) |
| /ah sell &lt;price> [amount] [currency] | Sell item |
| /ah search &lt;input> | Search items (by lore, username, item name, item type) |
| /ah view &lt;player> | Check items of player |
| /ah history | Check transaction history |

### Admin commands:
*permission: axauctions.admin*

|-|-|
| Command | Description | Permission |
| /ahadmin reload | Reload plugin | axauctions.reload |
| /ahadmin forceopen &lt;player> [menu] | Forcefully open menu | axauctions.forceopen |
| /ahadmin history &lt;player> | Check transaction history of player | axauctions.history.admin |
| /ahadmin limit set/give/take/reset | Modify the auction limit of player | axauctions.limit |
| /ahadmin convert &lt;plugin> | Convert data from another plugin, you must have the other plugin loaded as well | axauctions.convert |