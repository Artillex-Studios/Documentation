# Inventory Actions

- All actions support PlaceholderAPI placeholders, and they are parsed as the player (so for example %\player_name% will insert the player's name)

### Console
- Run console command

format:

`[CONSOLE] command without slash`

example:

`[CONSOLE] say Hey, it's the console, %\player%!`

### Player
- Run command as player

format:

`[PLAYER] command without slash`

example:

`[PLAYER] say Hey, it's me, %\player%!`

### Menu
- Open or close menu
- Note: the name of the menu is always the name of the file without the file extension (`cool-gui.yml` -> `cool-gui`)
- Also, not every menu can be opened like this

format:

`[MENU] menu name`

or

`[MENU] close`

example:

`[MENU] main`

### Message
- Send message to the player

`[MESSAGE] message`

example:

`[MESSAGE] &#FF0000Your message`

### Firework
- Spawn a firework at the player's location
- Valid types: [TYPES](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/FireworkEffect.Type.html)

format:

`[SOUND] color|type`

example:

`[SOUND] #FF0000|ball`

### Sound
- Play sound for player
- Valid sounds: [SOUNDS](https://www.digminecraft.com/lists/sound_list_pc.php)

format:

`[SOUND] sound|volume|pitch`

example:

`[SOUND] ui.button.click|1|1`

### Page
- Change page (only works in paginated guis)

format:

`[PAGE] next`

`[PAGE] previous`

`[PAGE] <page number>`

example:

`[PAGE] 3`

### Refresh
- Refresh page

format:

`[REFRESH]`

### Category
- Switch the selected category.
- The &lt;category> value is the lowercase name or id or the category.

format:

`[CATEGORY]` (switches to the next category)

`[CATEGORY] <category>` (switches to the set category by clicking)

`[CATEGORY] <left click category>|<right click category>` (switches to the set category with left/right click - useful for going back and forth)

example:

`[CATEGORY] tools|minerals`

### Currency
- Switch the selected currency
- The &lt;category> value is the lowercase name of the currency. (for multi currency plugins: &lt;plugin>-&lt;currency>)

format:

`[CURRENCY]` (switches to the next currency)

`[CURRENCY] <currency>` (switches to the set currency by clicking)

`[CURRENCY] <left click currency>|<right click currency>` (switches to the set currency with left/right click - useful for going back and forth)

example:

`[CURRENCY] tools|minerals`

### Sorting
- Switch the selected sorting
- The &lt;sorting> value is one of the following: `newest`, `oldest`, `cheapest`, `priciest`

format:

`[SORTING]` (switches to the next sorting)

`[SORTING] <sorting>` (switches to the set sorting by clicking)

`[SORTING] <left click sorting>|<right click sorting>` (switches to the set sorting with left/right click - useful for going back and forth)

example:

`[SORTING] newest|cheapest`