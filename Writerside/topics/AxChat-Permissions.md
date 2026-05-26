# Permissions

| Permission                   | Description                                                                          | Default |
|------------------------------|--------------------------------------------------------------------------------------|---------|
| axchat.staff                 | Grants the ability for players to see moderation alerts                              | op      |
| axchat.format.colors         | Allows the player to use color codes (like red, blue or gradients) in their messages | op      |
| axchat.format.decorations    | Allows the player to use decorations (like bold, italic) in their messages           | op      |
| axchat.format.unsafe         | Allows the player to use click and hover actions in their messages                   | op      |
| axchat.format.placeholders   | Allows the player to use placeholderapi placeholders in their messages               | op      |
| axchat.format.all            | Allows the player to use anything in their messages                                  | op      |
| axchat.messagecolor.#RRGGBB* | The message color of the player (used for the %\message_color% placeholder)          | -       |
| axchat.namecolor.#RRGGBB*    | The name color of the player (used for the %\name_color% placeholder)                | -       |
| axchat.mention.player        | Ability to mention players (by default: @name)                                       | true    |
| axchat.mention.here          | Ability to mention all players on the current server (by default: @here)             | op      |
| axchat.mention.everyone      | Ability to mention all players on the entire network (by default: @everyone)         | op      |
| axchat.mention.bypass        | Players with this permission can't be mentioned by anyone                            | false   |
| axchat.cooldown.bypass       | Let's players to skip the wait time for the report/helpop/alert commands.            | op      |
| axchat.moderation.bypass     | Makes players immune to the moderation system.                                       | op      |

\* The #RRGGBB must be replaced with a real hexadecimal color code, like #FF0000

- The command permission can be found on the [Commands](AxChat-Commands.md) page!