# Requirements

|-|-|
|Requirement|Description|Example|
|[gamemode]|Requires the player to be in a gamemode|[gamemode] survival|
|[!gamemode]|Requires the player to not be in a gamemode|[!gamemode] survival|
|[permission]|Requires the player to have a permission|[permission] cool.permission|
|[!permission]|Requires the player to not have a permission|[!permission] not.cool.permission|
|[world]|Requires the player to be in a world|[world] cool_world|
|[!world]|Requires the player to not be in a world|[!world] not_cool_world|
|[placeholder]|Requires the parsing of a PlaceholderAPI placeholder to be equal to a value|[placeholder] %\player_name%=CoolName|
|[!placeholder]|Requires the parsing of a PlaceholderAPI placeholder to not be equal to a value|[!placeholder] %\player_name%=CoolName|


## You can also do AND and OR operations with these requirements!

### Example 1
`[gamemode] survival|creative` - Requires the player to be in surival OR creative gamemode

### Example 2
`[permission] cool.permission&other.cool.permission` - Requires the player to have BOTH of the permissions