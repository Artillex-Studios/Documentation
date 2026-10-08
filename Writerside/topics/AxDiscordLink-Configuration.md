# Configuration

### Directory Structure
<code-block lang="text">
AxDiscordLink/
├── embeds/
│   ├── link.yml
│   ├── profile.yml
│   ├── two-factor.yml
│   ├── unlink.yml
│   └── user-info.yml
├── webhooks/
│   └── join.yml
├── config.yml
├── lang.yml
├── rewards.yml
└── token.secret
</code-block>

### Default Contents
<procedure title="config.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axdiscordlink.html
# READ THE SETUP GUIDE: https://docs.artillex-studios.com/axdiscordlink-first-time-setup.html

prefix: "<gradient:#0088FF:#00EEFF><b>AxDiscordLink</b></gradient> &7» "

# note: the bot token must be put in the token.secret file
bot:
  # your discord server's id, enable discord developer mode, and right-click on the server icon and "Copy Server ID" to get this
  guild-id: "SET-GUILD(server)-ID-HERE"
  # the bot's online status
  # valid values: DO_NOT_DISTURB, IDLE, INVISIBLE, OFFLINE, ONLINE
  status: "ONLINE"
  # what kind of activity should be displayed under the bot's name?
  # set the activity type to an empty "" to disable this
  activity:
    # valid values: CUSTOM_STATUS, PLAYING, STREAMING, LISTENING, WATCHING, COMPETING
    type: "PLAYING"
    value: "Minecraft"

database:
  # h2, mysql
  type: "h2"
  # database table prefix
  prefix: "axdiscordlink"
  # you only need to touch these when using mysql
  address: 127.0.0.1
  port: 3306
  database: admin
  username: admin
  password: 'admin'
  # advanced settings
  pool:
    maximum-pool-size: 10
    minimum-idle: 10
    maximum-lifetime: 1800000
    keepalive-time: 0
    connection-timeout: 5000

link:
  # for how many minutes should link codes be valid?
  expiry-time-minutes: 5

# syncs data between minecraft and discord
# requires LuckPerms (https://luckperms.net/)
sync:
  # if enabled, automatically updates the user's discord role to their minecraft rank
  minecraft-to-discord-roles: true
  # if enabled, automatically updates the user's minecraft rank to their discord role
  discord-to-minecraft-roles: false
  # if enabled, automatically renames the user's discord nickname to their minecraft name
  minecraft-to-discord-names: false
  # if enabled, only highest priority role/rank will be added to the user
  # if disabled, all the user's roles/ranks will be synced
  only-sync-primary: false
  # when should the roles and nicknames get updated?
  update:
    # update when the user joins
    join: true
    # update when the user quits
    quit: true
    # update when the user's ranks change
    minecraft-rank-update: true
    # update when the user's role changes
    discord-role-update: true
    # automatically check and updates online players if there are any changes
    # set to -1 to disable
    every-x-minutes: 30
  # list of roles to sync (roles not included will be skipped and the plugin won't touch them)
  # format: <minecraft rank name>: <discord role id>
  #
  # SAFETY NOTE: we suggest not setting up sync for roles with destructive powers (like discord administrator or minecraft *)
  # as if either the discord or minecraft server gets compromised, the attackers can get access to the other as well
  #
  # - the minecraft rank name must be case-sensitive (/lp group <rank> info - and see the "Group Info")
  # - the discord role's id must be used, which you can get by enabling developer mode and going to Server Settings -> Roles -> (right-click on the one you want) Copy Role ID
  #
  # note: if you are planning on using the "only-sync-primary" option, make sure to put roles here in order from highest to lowest priority
  roles:
    "example-rank": "1000000000000000000"

# requires a restart to update
minecraft-command-aliases:
  admin:
    - "axdiscordlink"
    - "discordlink"
    - "axdclink"
    - "dclink"
  link:
    - "link"
  unlink:
    - "unlink"
  2fa:
    - "2fa"

# requires a restart to update
discord-command-aliases:
  profile:
    - "profile"
  userinfo:
    - "userinfo"
  link:
    - "link"
  unlink:
    - "unlink"
  2fa:
    - "2fa"

# should be plugin notify you if there is a new update?
update-notifier:
  # if enabled, it will display the message in the console
  enabled: true
  # if enabled, it will broadcast the update message to all players who have the <plugin-name>.update-notify permission
  on-join: true

# prints out a lot of information about the plugin in the console
# this can cause a lot of spam, only use if a developer asks you to
debug: false

# do not change this
version: 1

]]>
</code-block>
</procedure>

<procedure title="lang.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axdiscordlink.html

help:
  - " "
  - "<gradient:#0088FF:#00EEFF><b>AxDiscordLink</b></gradient> <#00BBFF>Help"
  - " <#00BBFF>➤ <white>/axdiscordlink reload <#DDDDDD>| <#88BBFF>Reload plugin"
  - " <#00BBFF>➤ <white>/axdiscordlink profile [player] <#DDDDDD>| <#88BBFF>View user's profile"
  - " <#00BBFF>➤ <white>/axdiscordlink link <player> <discord id or tag> <#DDDDDD>| <#88BBFF>Force link user"
  - " <#00BBFF>➤ <white>/axdiscordlink unlink <player> <#DDDDDD>| <#88BBFF>Force unlink user"
  - " <#00BBFF>➤ <white>/axdiscordlink 2fa <user> <#DDDDDD>| <#88BBFF>Force disable 2FA of user"
  - " "

link:
  success: "&#00FF00You have successfully linked your discord account to the user &#FFFFFF@%name%&#00FF00."
  invalid-code: "&#FF0000The given code is not valid or it has expired."
  code: "&#AAFFFFStarted linking process! &#00FF00Run the &#FFFFFF<click:suggest_command:'/link %code%'>/link %code%</click> &#00FF00command on the discord server to confirm."
  already-linked-minecraft: "&#FF0000This Minecraft account is already linked to a Discord account. Try removing the link with the &#FFFFFF/unlink &#FF0000command first."
  already-linked-discord: "&#FF0000This Discord account already linked to a Minecraft account. Try removing the link with the &#FFFFFF/unlink &#FF0000command first."

unlink:
  success: "&#00FF00You have successfully unlinked your discord account."
  not-linked: "&#FF0000Your account is not linked to any discord user."

2fa:
  testing: "&#DDDDDDWe are testing if your Discord account can receive private messages, please wait a moment..."
  enabled: "&#00FF00You have successfully <u>enabled</u> two factor authentication. You will receive a confirmation request a discord message after joining."
  disabled: "&#FF0000You have successfully <u>disabled</u> two factor authentication."
  not-linked: "&#FF0000Your account is not linked to any discord user."
  disabled-messaging: "&#FF0000You have discord direct messages disabled from the server's members, which is required to enable 2FA. Please enable it and try again."
  requested: "&#AAFFFFLogin confirmation required, check your private messages on Discord and accept the request."
  accepted: "&#00FF00Your login request has been accepted, you can now access your account!"
  declined: "&#FF0000You have been kicked, because your login request has been declined."

profile:
  self:
    - ""
    - "%prefix <#00EEFF><b>My Profile"
    - ""
    - "<#00EEFF>Discord account"
    - "<#00BBFF>➤ <#FFFFFF>@%discord-name% <#DDDDDD>(id: %discord-id%)"
    - ""
    - "<#00EEFF>Two factor authentication"
    - "<#00BBFF>➤ <#FFFFFF>%2fa-enabled%"
    - ""
  others:
    - ""
    - "%prefix <#00EEFF><b>%minecraft-name%'s Profile"
    - ""
    - "<#00EEFF>Discord account"
    - "<#00BBFF>➤ <#FFFFFF>@%discord-name% <#DDDDDD>(id: %discord-id%)"
    - ""
    - "<#00EEFF>Two factor authentication"
    - "<#00BBFF>➤ <#FFFFFF>%2fa-enabled%"
    - ""
  not-linked:
    - "%prefix %&#FF0000This user does not have a linked Discord account."

force:
  link:
    success: "&#00FF00You have successfully linked &#FFFFFF%minecraft-name% &#00FF00to &#FFFFFF@%discord-name%&#00FF00."
    minecraft-unknown: "&#FF0000The Minecraft player can't be found."
    discord-unknown: "&#FF0000The Discord user can't be found."
    minecraft-linked: "&#FF0000The Minecraft player has their account linked. You have to unlink it first."
    discord-linked: "&#FF0000The Discord user has their account linked. You have to unlink it first."
  unlink:
    success: "&#00FF00You have successfully unlinked &#FFFFFF%minecraft-name%&#00FF00's account."
    unknown: "&#FF0000The player can't be found."
    not-linked: "&#FF0000The player doesn't have a linked Discord account."
  2fa:
    success: "&#00FF00You have successfully disabled two factor authentication for &#FFFFFF%minecraft-name%&#00FF00."
    unknown: "&#FF0000The player can't be found."
    already-disabled: "&#FF0000The player doesn't have two factor authentication turned on."
    not-linked: "&#FF0000The player doesn't have a linked Discord account."

placeholders:
  enabled: "enabled"
  disabled: "disabled"

data-not-loaded: "&#FF0000Your data has not been loaded yet, please wait a moment before trying it again!"
data-not-loaded-other: "&#FF0000The data of &#BB0000%player% &#FF0000has not been loaded yet! Please try again in a moment!"

reload:
  success: "&#33FF33Plugin successfully reloaded!"
  failed: "&#FF3333Failed to reload the plugin! Something is wrong in the &f%file%&#FF3333 file, look in the console or use a yaml validator to fix the errors!"

commands:
  invalid-value: "&#FF0000Invalid parameter: &#BB0000%value%"
  invalid-command: "&#FF0000Invalid command or subcommand!"
  missing-argument: "&#FF0000Missing argument! You must specify a value for &#BB0000%value%&#FF0000."
  no-permission: "&#FF0000You don't have permission to access this command!"
  out-of-range: "&#FF0000The &#BB0000%number% &#FF0000must be between &#BB0000%min% &#FF0000and &#BB0000%max%&#FF0000!"
  player-only: "&#FF0000You must be a player to use this command!"
  invalid-player: "&#FF0000The player &#BB0000%player% &#FF0000can not be found!"
  invalid-selector: "&#FF0000You can not use this selector in this command!"

update-notifier: "&#00BBFFThere is a new version of AxDiscordLink available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"

# do not change this
version: 1

]]>
</code-block>
</procedure>

<procedure title="rewards.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axdiscordlink.html
# ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html
# you can run commands when these actions happen

# should rewards be enabled?
enabled: false

# REWARD SETTINGS (all of them are optional) - you can also add as many rewards for each action as you would like
# require-online: true or false, should the player have to be online for this reward to run? the plugin will wait to give the reward if they aren't online
# message: the text to send to the player when they receive the reward
# commands: the commands to run
# items: the items to give (only works on bukkit based servers)

# when the user links their account, only runs for the first time, if they unlink and link again, it will not run
first-link:
  - require-online: true
    message:
      - "&#00FF00You have linked your discord account!"
    commands: []
    items:
      - material: IRON_INGOT
        name: "&#DDDDDDLinking Iron"
        amount: 1

# runs every time the user links their account, even if they have already linked it before
link:

# runs every time the user unlinks their account
unlink:

# runs every time the user boosts the discord server
server-boost:


# do not change this
version: 1

]]>
</code-block>
</procedure>

<procedure title="embeds/two-factor.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axdiscordlink.html
# WEBHOOK BUILDER: https://docs.artillex-studios.com/discord-webhook-builder.html

not-linked:
  embeds:
    - title:
        text: "Account not linked"
      description: "Use the /link command to link your Minecraft account."
      color: "#AA0000"

disabled-messaging:
  embeds:
    - title:
        text: "Failed to enable 2FA"
      description: "You have direct messages disabled from the server's members, which is required to enable 2FA. Please enable it and try again."
      color: "#AA0000"

2fa-enabled:
  embeds:
    - title:
        text: "Successfully enabled 2FA"
      description: "You will receive a login request as a private message when logging in."
      color: "#00FF00"

2fa-disabled:
  embeds:
    - title:
        text: "Successfully disabled 2FA"
      description: "You no longer have to accept login requests."
      color: "#FF0000"

2fa-request:
  embeds:
    - title:
        text: "Login detected"
      description: "Please click on the button to accept or decline the request."
      color: "#FFFF00"
      footer:
        text: "You can disable this by using the /2fa command."
  # button builder options:
  #  text: button name
  #  style: look of the button, allowed values: primary (blue), secondary (gray), success (green), danger (red)
  #  emoji: (optional) the emoji to use in text format, use the \emoji in discord to get the raw emoji format
  buttons:
    accept:
      text: "Yes, it was me."
      style: "success"
      emoji: "✅"
    decline:
      text: "No, it wasn't me."
      style: "danger"
      emoji: "❌"

2fa-request-accepted:
  embeds:
    - title:
        text: "Login request accepted"
      description: "You can now return to Minecraft."
      color: "#00FF00"

2fa-request-declined:
  embeds:
    - title:
        text: "Login request declined"
      description: "The user has been kicked. Make sure to secure your account."
      color: "#FF0000"

2fa-request-expired:
  embeds:
    - title:
        text: "Login request expired"
      description: "Try logging in again to request a new confirmation."
      color: "#AA0000"

]]>
</code-block>
</procedure>

<procedure title="webhooks" collapsible="true">
See the <i><a href="AxDiscordLink-Webhooks.md">Webhooks page</a></i>.
</procedure>