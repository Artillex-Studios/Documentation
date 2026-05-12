# Commands

### Player Commands:
- Permission: `axauctions.use` (given by default)

| Command                                 | Description                                            | Permission         | Given by Default |
|-----------------------------------------|--------------------------------------------------------|--------------------|------------------|
| /ah                                     | Open auction house                                     | axauctions.open    | true             |
| /ah open [menu]                         | Open menu                                              | axauctions.open    | true             |
| /ah sell &lt;price> [amount]            | Sell item (opens currency selector)                    | axauctions.sell    | true             |
| /ah sell &lt;price> [amount] [currency] | Sell item                                              | axauctions.sell    | true             |
| /ah search [input]                      | Search items (by lore, username, item name, item type) | axauctions.search  | true             |
| /ah view [player]                       | Check items of player                                  | axauctions.view    | true             |
| /ah history                             | Open history viewer                                    | axauctions.history | true             |
| /ah deleted                             | Open deleted item viewer                               | axauctions.deleted | true             |


### Admin Commands:
- Permission: `axauctions.admin`

| Command                               | Description                                                                     | Permission               |
|---------------------------------------|---------------------------------------------------------------------------------|--------------------------|
| /ahadmin reload                       | Reload plugin                                                                   | axauctions.reload        |
| /ahadmin forceopen &lt;player> [menu] | Forcefully open menu                                                            | axauctions.forceopen     |
| /ahadmin history &lt;player>          | Check transaction history of player                                             | axauctions.history.admin |
| /ahadmin limit set/give/take/reset    | Modify the auction limit of player                                              | axauctions.limit         |
| /ahadmin history [player]             | Open history viewer                                                             | axauctions.history.admin |
| /ahadmin deleted [player]             | Open deleted item viewer                                                        | axauctions.deleted.admin |
| /ahadmin logs [player]                | Open log viewer                                                                 | axauctions.logs.admin    |
| /ahadmin convert &lt;plugin>          | Convert data from another plugin, you must have the other plugin loaded as well | axauctions.convert       |