# Items

### Description
- Handles items in the players' inventory

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# note: this module clears the inventory and overrides all slots

server-info:
  slot: 0
  name: "<gradient:#FF4500:#FF1493><b>SERVER INFO</b></gradient>"
  material: BOOK
  lore:
    - " "
    - "&#FFCC44Right click to use!"
  actions:
    - "[MESSAGE] "
    - "[MESSAGE] &#FF0000&lWEBSITE > &fwww.example.com"
    - "[MESSAGE] &#FF0000&lWEBSTORE > &fshop.example.com"
    - "[MESSAGE] "

ender-bow:
  slot: 1
  name: "<gradient:#FF4500:#FF1493><b>ENDER BOW</b></gradient>"
  material: BOW
  lore:
    - " "
    - "&#FFCC44Right click to use!"
  actions:
    - "[ENDER_BOW]"

grappling-hook:
  slot: 3
  name: "<gradient:#FF4500:#FF1493><b>GRAPPLING HOOK</b></gradient>"
  material: FISHING_ROD
  lore:
    - " "
    - "&#FFCC44Right click to use!"
  actions:
    - "[GRAPPING_HOOK]"

fun-gun:
  slot: 5
  # cooldown is in ticks, 1 second = 20 ticks
  cooldown: 60
  name: "<gradient:#FF4500:#FF1493><b>FUN GUN</b></gradient>"
  material: BLAZE_ROD
  lore:
    - " "
    - "&#FFCC44Right click to use!"
  actions:
    - "[FUN_GUN]"

server-selector:
  slot: 4
  name: "<gradient:#FF4500:#FF1493><b>SERVER SELECTOR</b></gradient>"
  material: COMPASS
  lore:
    - " "
    - "&#FFCC44Right click to use!"
  actions:
    - "[MENU] selector"

ender-pearl-rider:
  slot: 7
  name: "<gradient:#FF4500:#FF1493><b>ENDER PEARL RIDER</b></gradient>"
  material: ENDER_PEARL
  lore:
    - " "
    - "&#FFCC44Right click to use!"
  actions:
    - "[RIDER]"

hider-hide:
  conditions:
    - "%hidden% = false"
  slot: 8
  # cooldown is in ticks, 1 second = 20 ticks
  cooldown: 60
  name: <gradient:#FF4500:#FF1493><b>HIDE PLAYERS</b></gradient>
  material: LIME_DYE
  lore:
    - ' '
    - '&#FFCC44Right click to use!'
  actions:
    - "[HIDER]"
hider-show:
  conditions:
    - "%hidden% = true"
  slot: 8
  # cooldown is in ticks, 1 second = 20 ticks
  cooldown: 60
  name: <gradient:#FF4500:#FF1493><b>SHOW PLAYERS</b></gradient>
  material: GRAY_DYE
  lore:
    - ' '
    - '&#FFCC44Right click to use!'
  actions:
    - "[HIDER]"

# do not change this value
version: 1
    ]]>
</code-block>
