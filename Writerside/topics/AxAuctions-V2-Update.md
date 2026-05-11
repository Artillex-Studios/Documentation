# V2 Update

- The goal of the update: Improve code quality and performance and add new features without breaking previous configurations.

### Database
- Recoded the entire database system to improve performance.
> There are no changes to the existing structure, so no converter is needed and the database is 100% backwards compatible.

### Cross/Multi Server Support
- The plugin now supports SQL, Proxy, Redis and RabbitMQ messaging.
- The SQL messaging now polls data every second instead of every time people interacted with the auction house, drastically decreasing database network load and it also speeds up the auction house.
- We suggest moving to RabbitMQ or Redis from SQL messaging for the greatest performance.
- Proxy messaging is now also supported, which uses bungeecord messaging channels. We don't recommend using them, however they don't require any setup and they quite lightweight and fast.
> There is a configuration migration process as the config.yml "multi-server-support" has been expanded. The plugin will automatically set the mode to "sql" if you used SQL messaging in v1.
{style=warning}

### Deleted Item Logs
- The plugin now stores if an item gets deleted due to the auction running out of time.
- Players can see their deleted items with /ah deleted (`axauctions.deleted` permission, given by default) or staff can see the global deleted items list with /ahadmin deleted [player] (`axauctions.deleted.admin` permission)

### Auction House Logs
- The plugin now tracks all interactions with the auction house and stores them in a new log viewer gui.
- You can access it with the /ahadmin logs [player] command. (`axauctions.logs.admin` permission)
- This gui can be used to track down player actions or to prevent staff abuse.

### Category Selector
- A new category selector gui has been added, it will only work if categories are enabled.
- Added a new `[MENU] category` gui action that can be used to open the category selector.
- Made it possible to change the default gui, (config.yml → `default-menu`) so you can make it that the /ah opens the category selector by default.

### Statistics Update
- The plugin now tracks and provides placeholders for a bunch of auction related statistics.
- The best part is that all of these statistics were already tracked using the history menu, so even pre update statistics are visible.

### Placeholders
- Added **43** new placeholders.
- Now all numberical placeholders are formatted by default. Added a `<..placeholder>_raw` variant for them that can be used to get the number without formatting.
- See the [placeholders](AxAuctions-Placeholders.md) page for the updated list.

### Improved Search
- Added various input methods (sign, chat, anvil) that can be used search for items.
- The /ah search command now opens the selected input method.
- Added a new `[SEARCH]` gui action that can be used to start the search.

### Quality of Life Improvements
- Now clicking on items in the history and deleted menus gives the staff the item. (requires the new `axauctions.history.admin.take` or `axauctions.deleted.admin.take` permissions)
- Added a line to shulkers and other storage items to all menus that tells the user that they can right-click to view their contents. 
- The item that you are selling is now visible in the currency selector menu.
- Added content limit options into the config, which can be used to limit the maximum size of items that can be placed on the auction house.

### Default Configuration Changes
- Revamped all the default gui configuration files, improved their design and usability.
- The default gui files now come with conditions (with the new `%\categories_enabled%` and `%\expired_items_enabled%` placeholders) for the category and expired item buttons, so people don't need to uncomment anything if they want to use these features.
- Added a Statistics item to the default guis.
- The previous/next page buttons no longer show up when there is no page available.

### Performance Improvements
- The database improvements already give a major performance boost, however there are some further improvements.
- Most configuration values are now cached, which decreases disk usage and can be quite significant on slower drives.
- The history gui has been recoded, and now it works like the other guis, it only loads nearby pages into ram, and it can handle 100s of pages with very little load time.
- The plugin now opens the gui frame before the page items are fully loaded, this gives the illusion that everything loaded faster.
- The auction item expiration and notification system is no longer running useless actions if the multi server mode is not enabled.

### Other Changes
- Dropped the currency system migration which was added in the 1.16.0 version, a year and a half ago.
- The AxAuctionsPreSellEvent api event has changed, because the AuctionItem object no longer exists before the data is inserted into the database.