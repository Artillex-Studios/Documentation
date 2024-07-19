# Inventory Actions

- All actions support PlaceholderAPI placeholders, and they are parsed as the player (so for example %\player_name% will insert the player's name)

### Console
- Run console command

format:

`[CONSOLE] command without slash`

example:

`[CONSOLE] say I am the console!`

### Player
- Run command as player

format:

`[PLAYER] command without slash`

example:

`[PLAYER] me Hey, it's me!`

### Menu
- Open or close menu

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
`[PAGE] page number`

example:

`[PAGE] 3`