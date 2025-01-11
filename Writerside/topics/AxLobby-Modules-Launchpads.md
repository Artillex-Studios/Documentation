# Launchpads

### Description
- Launches players across the map

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# you can create as many launch pads as you would like
launchpads:
  # this is the first launchpad
  LIGHT_WEIGHTED_PRESSURE_PLATE:
    forwards-speed: 1.5
    upwards-speed: 1.0
  # this is the second launchpad
  HEAVY_WEIGHTED_PRESSURE_PLATE:
    forwards-speed: 2.0
    upwards-speed: 1.5

launch-sound: "entity.bat.takeoff|1|1"

# do not change this value
version: 1
    ]]>
</code-block>
