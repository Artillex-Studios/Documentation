# AxShulkers

## What is AxShulkers?

*A highly customizable shulker viewer plugin that is dupe free by design! Open your shulkers anywhere, you don't even need to place them.
*Just right click with a shulker to open it!

## How it works:
* Every shulker is saved to a database and when they are interacted with, their inventory is loaded and kept in memory, which stops most duplication exploits that are present in other shulker viewer plugins.
* We don't read the shulker item's contents, but we read it from a database and shulkers work more like smart backpacks
* Important: You must run /axshulkers clear before giving filled shulker boxes to players (for example before putting a shulker into a crate you should run this)

## Features:
* Open shulkers without placing them
* Highly customizable (open & close messages, sounds, inventory name, cooldown)
* Shulker open cooldown
* Disable shulker opening is specific worlds
* Blacklist items from shulker boxes (customizable)
* Shulker content obfuscation (makes it impossible to see what is in a shulker without opening it)
* H2, SQLite database
* Supports minimessage, &#RRGGBB and legacy (&a) color codes)