# Configuration

### Directory Structure
<code-block lang="text">
AxTreasures/
├── config.yml
└── lang.yml
</code-block>

### Default Contents
<procedure title="config.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axtreasures.html

prefix: "<gradient:#FF7700:#FFBB00><b>AxTreasures</b></gradient> &7» "

database:
    # currently only h2 is supported
    type: "h2"
    # don't touch these unless you know what they mean
    pool:
    maximum-pool-size: 10
    minimum-idle: 10
    maximum-lifetime: 1800000
    keepalive-time: 0
    connection-timeout: 5000

# after opening a treasure, how long should it take for the unclaimed items to expire and disappear from the chest?
# set this to -1 to make it only possible to make the treasure lock right after closing it
treasure-expiry-seconds: 60

# used for showing length of boosters
# 1 - HH:MM:SS, for example 01:25:35
# 2 - short format, for example 20m
# 3 - text format, for example 01h 25m 35s
timer-format: 1

# should be plugin notify you if there is a new update?
update-notifier:
    # if enabled, it will display the message in the console
    enabled: true
    # if enabled, it will broadcast the update message to all players who have the <plugin-name>.update-notify permission
    on-join: true

# do not change this
version: 1

]]>
</code-block>
</procedure>

<procedure title="lang.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

# DOCUMENTATION: https://docs.artillex-studios.com/axtreasures.html

help:
    - " "
    - "<gradient:#FF7700:#FFBB00><b>AxTreasures</b></gradient> <#FFCC55>Help"
    - " <#FFCC55>➤ <white>/axtreasures reload <#DDDDDD>| <#FFCCAA>Reload plugin"
    - " <#FFCC55>➤ <white>/axtreasures create [treasure cooldown] [title] <#DDDDDD>| <#FFCCAA>Turn container into treasure"
    - " <#FFCC55>➤ <white>/axtreasures remove <#DDDDDD>| <#FFCCAA>Remove treasure"
    - " <#FFCC55>➤ <white>/axtreasures reset <player> <#DDDDDD>| <#FFCCAA>Reset treasure cooldowns of player"
    - " "

treasure:
    # default inventory title, you can override this by creating a treasure with a title: /axtreasures create [cooldown] [title]
    inventory-title: "⭐ Treasure ⭐"
    not-a-container: "&#FF0000You are not looking at any container!"
    not-a-treasure: "&#FF0000You are not looking at a treasure!"
    created: "&#00FF00You have successfully turned the container into a treasure!"
    removed: "&#FF0000You have successfully removed the treasure!"
    one-time-claimed: "&#FF0000You have already claimed this treasure!"
    on-cooldown: "&#FF0000You must wait another &#FFFFFF%time% &#FF0000before claiming this treasure again!"
    reset: "&#FF0000You have reset the treasure cooldowns of &#FFFFFF%player%&#FF0000!"

time:
    second: "s"
    minute: "m"
    hour: "h"
    day: "d"

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

update-notifier: "&#FFFFAAThere is a new version of AxTreasures available! &#DDDDDD(&#FFFFFFcurrent: &#FF0000%current% &#DDDDDD| &#FFFFFFlatest: &#00FF00%latest%&#DDDDDD)"

# do not change this
version: 1

]]>
</code-block>
</procedure>