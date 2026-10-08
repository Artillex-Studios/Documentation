# Commands

> Command prefixes can be changed in the config.yml. (you can also disable any command)

### Minecraft

| Command                                                 | Permission           | Default | Description                                                   |
|---------------------------------------------------------|----------------------|---------|---------------------------------------------------------------|
| /link [code]                                            | axdiscordlink.link   | true    | Set up link between discord and minecraft                     |
| /unlink                                                 | axdiscordlink.unlink | true    | Remove link between discord and minecraft                     |
| /2fa                                                    | axdiscordlink.2fa    | true    | Toggle two factor authentication                              |
| /axdiscordlink reload                                   | axdiscordlink.admin  | op      | Reload plugin                                                 |
| /axdiscordlink profile [player]                         | axdiscordlink.admin  | op      | Display details about the link of the player                  |
| /axdiscordlink 2fa &lt;player>                          | axdiscordlink.admin  | op      | Forcefully disable the two factor authentication for a player |
| /axdiscordlink link &lt;player> &lt;discord id or name> | axdiscordlink.admin  | op      | Forcefully create a link for the player                       |
| /axdiscordlink unlink &lt;player>                       | axdiscordlink.admin  | op      | Forcefully remove the link of the player                      |

* Permissions on Velocity are not given by default, you must get a permission plugin like LuckPerms and give access manually.

### Discord

| Command               | Description                                                       |
|-----------------------|-------------------------------------------------------------------|
| /profile [member]     | Prints out details about the member's profile                     |
| /userinfo &lt;player> | Prints out details about a minecraft player's discord link        |
| /link [code]          | Creates a linking code or confirms linking to a minecraft profile |
| /unlink               | Removes the link between the user and minecraft profile           |
| /2fa                  | Toggles two factor authentication status                          |

* By default, all discord commands can be run by all members without any permission required. (you can change the requirements in the Server Settings → Integrations tab)