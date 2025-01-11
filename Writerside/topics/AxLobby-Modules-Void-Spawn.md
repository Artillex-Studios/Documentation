# Void Spawn

### Description
- Used to teleport players back to the spawn if they fall under a certain Y level

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# under what Y level should the plugin teleport the player back to the spawn?
teleport-under-y: -64

# worlds where it shouldn't teleport you back
# case sensitive
disabled-worlds:
  - "SOME_DISABLED_WORLD"

# do not change this value
version: 1
    ]]>
</code-block>
