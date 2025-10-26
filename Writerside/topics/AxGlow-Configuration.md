# Configuration

You can create any number of glows, this is how the rainbow glow is set up in the default config.
<procedure title="glows/rainbow.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[

    # item to use in the glow gui
    item:
        slot: 28
        material: PLAYER_HEAD
        texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvY2ZmYzk3N2NjN2UxMGU1NjRhMDk2MzhhNTNiYmM0YzU0YzljOGRhYzc0NTBiYTNkZmEzYzkwOTlkOTRmNSJ9fX0=
        name: "<rainbow><b>Rainbow</b></rainbow>"
    
    # the permissions required to use the glow
    permission: "axglow.color.rainbow"
    # randomize the order of glow colors
    randomize: true
    # the time it takes to switch between colors
    switch-milliseconds: 1000
    # the list of colors to switch between
    colors:
        - BLACK
        - DARK_BLUE
        - DARK_GREEN
        - DARK_AQUA
        - DARK_RED
        - DARK_PURPLE
        - GOLD
        - GRAY
        - DARK_GRAY
        - BLUE
        - GREEN
        - AQUA
        - RED
        - LIGHT_PURPLE
        - YELLOW
        - WHITE
	
    ]]>
</code-block></step>
</procedure>