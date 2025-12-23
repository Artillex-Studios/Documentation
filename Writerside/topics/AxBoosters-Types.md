# Types of Boosters

- Note: Booster Type is the name of your booster configuration file, that can be found in the AxBoosters/boosters folder.
- Read for more information: **[Explanation of Some Words](AxBoosters-Explanation-of-some-words.md)**

## Activatable Boosters
- They can be given with the _[/axboosteradmin give](AxBoosters-Commands.md)_ command!
- They are added to the player's inventory (/axboosters) and they can activate it any time.

## Permission Boosters
- You need a permission plugin for this (for example LuckPerms)
- They are very simple, you can activate them by setting the following permission: axboosters.boost.&lt;booster type>.&lt;multiplier>
- Example: `axboosters.boost.mybooster.200` - this will give a +200% (or 3x) booster of the `mybooster` type

## Item Boosters
- There are many types of Item Boosters:
  - **Hand**: Activated when the item is in your main hand
  - **Offhand**: Activated when the item is in your second hand
  - **Armor**: Activated when you are wearing the item
  - **Inventory**: Activated when the item is anywhere in your inventory
- You can add them to ANY item with the /axboosteradmin apply command (use /axboosteradmin unapply to remove them)

## API Boosters
- They can be registered by any plugin developer, here is a quick information on how it works: **[Registering API Boosters](AxBoosters-Registering-API-Boosters.md)**