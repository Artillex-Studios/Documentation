# Join Actions

### Description
- Sets some default values for joining players

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

teleport-to-spawn: true

clear-inventory: true

# fill heart bar
heal: true
# fill food & saturation
feed: true

# set to gamemode: "" to disable
gamemode: "ADVENTURE"

# set default hotbar slot on join (can be between 0 and 8)
# set to -1 to disable
default-hotbar-slot: 4

firework:
  enabled: true
  only-first-join: true
  settings: "#ff0000,ball"

# do not change this value
version: 1
    ]]>
</code-block>
