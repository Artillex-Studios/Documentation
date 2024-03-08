# Configuration

* This page might be outdated, however it does show our basic configuration style that you will see in the plugin.

<procedure title="config.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[prefix: "<gradient:#AAFF00:#77FF44><b>AxQuestBoard</b></gradient> &7» "

    database:
        # h2, sqlite
        # for single server setups we recommend h2 because it's way faster than sqlite
        type: "h2"
    
    # timer format for %time% placeholders
    # 1 - HH:MM:SS, for example 01:25:35
    # 2 - short format, for example 20m
    # 3 - text format, for example 01h 25m 35s
    timer-format: 1
    
    # you must define at least 1
    # reloading will add new commands, however a restart is recommended when editing this
    command-aliases:
        - "axquestboard"
        - "axqb"
        - "questboard"
        - "qb"
    
    # you must define at least 1
    # reloading will add new commands, however a restart is recommended when editing this
    shop-commands:
        - "axquestshop"
        - "questshop"
    
    # how big the board should be at these player counts?
    # so with the default config at 13 players the board will be 3 rows, at 50 it will be 6 rows
    # if you just want a static board, use this:
    # board-rows:
    #   0:
    #     rows: 6
    #     quest-slots: 0-53
    board-rows:
        0:
            # how many rows should there be at 0-4 players?
            rows: 1
            # which of the slots should be used for quests?
            # please double-check that you defined this correctly or hidden quests may appear (https://c4k3.github.io/wiki.vg/File:DoubleChest-slots.png.html)
            quest-slots: 0-8
        5:
            rows: 2
            quest-slots: 9-17
        10:
            rows: 3
            quest-slots: 18-26
        15:
            rows: 4
            quest-slots: 27-35
        20:
            rows: 5
            quest-slots: 36-44
        25:
            rows: 6
            quest-slots: 45-53

    # how often should the board rows be checked?
    # this is only used to recalculate the row amount of the gui
    # this is not too heavy, if you prefer it, you can set it lower
    # requires a restart to change
    resize-check-seconds: 60
    
    # how often should quest scores be saved to the database?
    # requires a restart to change
    auto-save-seconds: 180
    
    # after someone completing a quest from the board, how long should it take to generate a new quest?
    # this is in seconds
    new-quest-cooldown: 1800
    
    # https://docs.oracle.com/javase/tutorial/i18n/format/decimalFormat.html
    # how money should be formatted?
    number-format: "#,###.##"

    # broadcasts may be a bit spammy, if you want you can display them as an actionbar
    broadcasts:
        chat: true
        actionbar: false
    
    # do not change this
    version: 1]]>
</code-block></step>
</procedure>

<procedure title="guis.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[title: "&0Quest Board"
    
    # ----- ITEMS -----
    
    # used when a quest slot is on cooldown
    cooldown-item:
        material: WEEPING_VINES
        name: "&#EE0000&lRefreshing..."
        lore:
            - " "
            - "&#EE0000New quest will appear in:"
            - " &7- &f%time%"
            - " "
    
    ## when you add decorations MAKE SURE that you did not set them in the place of a quest
    ## look at the board-rows in the config.yml and change it if your decoration overlaps
    #decoration-example:
    #  slot: 13
    #  material: IRON_INGOT
    #  name: '&eDECORATION'
    #  lore:
    #    - ' '
    #    - ' &fWoah, what a cool decoration!'
    
    # do not change this
    version: 1]]>
</code-block></step>
</procedure>

<procedure title="lang.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[help:
      - " "
      - "<gradient:#AAFF00:#77FF44><b>AxQuestBoard</b></gradient> &7»"
      - " &7- &f/axqb &7| &#AAFF00Open menu"
      - " &7- &f/axqb reload &7| &#AAFF00Reload plugin"
      - " &7- &f/axqb forceopen <player> &7| &#AAFF00Open the board for the player"
      - " "
    
    reload:
        success: "&#33FF33Plugin successfully reloaded!"
        failed: "&#FF3333Failed to reload the plugin! Something is wrong in the &f%file%&#FF3333 file, look in the console or use a yaml validator to fix the errors!"
    
    time:
        second: "s"
        minute: "m"
        hour: "h"
        day: "d"
    
    # set to "" to disable
    broadcasts:
        resize-up: "&fThe size of the &#AAFF00/questboard &fhave been increased to &#AAFF00%rows% rows &fbecause the player count goal have been reached!"
        resize-down: "&fThe size of the &#AAFF00/questboard &fhave been decreased to &#AAFF00%rows% rows &fbecause the player count went down! Invite your friends to increase it again!"
        completed-single: "&#AAFF00%player% &fhas completed the quest titled &#AAFF00'%quest%' &fon the &#AAFF00/questboard &fand won &#AAFF00%points% points&f!"
        completed-multiple: "&#AAFF00%player% &fhas completed &#AAFF00%amount% &fquests titled &#AAFF00'%quest%' &fon the &#AAFF00/questboard &fand won &#AAFF00%points% points&f!"
        taken-over: "&#AAFF00%player% &fhas taken your &#AAFF00#1 &fspot on the &#AAFF00/questboard &fquest titled &#AAFF00'%quest%'"
        new-quest: "&fA new quest on available on the &#AAFF00/questboard &ftitled &#AAFF00'%quest%'"
    
    points:
        changed: "&#33FF33You have changed &f%player%&#33FF33's quest points to &f%amount%&#33FF33!"
    
    shop:
        not-enough-money: "&#FF3333You can't afford this!"
        success: "&#33FF33Successful purchase!"
    
    # do not change this
    version: 1]]>
</code-block></step>
</procedure>

<procedure title="shop.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[# in the shop you can buy items from points
    
    title: "&0Quest Shop"
    # a gui can only have 1-6 rows
    rows: 5
    # how many item should be shown on a single page?
    page-size: 36
    
    buy-sounds:
        # list of sounds: https://www.digminecraft.com/lists/sound_list_pc.php
        not-enough-money: "entity.experience_bottle.throw"
        success: "entity.experience_orb.pickup"
    
    # ----- ITEMS -----
    
    buyable-items:
        1:
            price: 1000
            display:
            material: DIAMOND_SWORD
            name: "&#AAFF00A very cool diamond sword!"
            lore:
                - " "
                - " &7- &fPrice: &#AAFF00%price% points"
                - " &7- &fYour points: &#AAFF00%points%"
                - " "
                - "&#AAFF00&l(!) &#AAFF00Click here to buy!"
            # commands to run when buying, optional
            buy-commands:
                - "give %player% diamond 1"
            # items to give when buying, optional
            buy-items:
            1:
                material: DIAMOND_SWORD
                name: "&#AAFF00A very cool diamond sword!"
        2:
            price: 500
            display:
                amount: 3
                material: diamond
                name: "&#AAFF00A shiny diamond!"
            lore:
                - " "
                - " &7- &fPrice: &#AAFF00%price% points"
                - " &7- &fYour points: &#AAFF00%points%"
                - " "
                - "&#AAFF00&l(!) &#AAFF00Click here to buy!"
            # items to give when buying, optional
            buy-items:
                1:
                    material: DIAMOND
                    amount: 3
        
    previous-page:
        slot: 39
        material: "ARROW"
        name: "&#AAFF00&lᴘʀᴇᴠɪᴏᴜs ᴘᴀɢᴇ"
        lore:
            - " "
            - " &fClick here to go back"
            - " &fto the previous page!"
            - " "
            - "&#AAFF00&lClick &#DDDDDD» &#CCFFAAPrevious Page"
        # list of sounds: https://www.digminecraft.com/lists/sound_list_pc.php
        # the sound played when clicking this item
        # set to "" to disable
        sound: "ui.button.click"
    
    next-page:
        slot: 41
        material: "ARROW"
        name: "&#AAFF00&lɴᴇxᴛ ᴘᴀɢᴇ"
        lore:
            - " "
            - " &fClick here to go"
            - " &fto the next page!"
            - " "
            - "&#AAFF00&lClick &#DDDDDD» &#CCFFAANext Page"
        sound: "ui.button.click"
    
    filler:
        slot: [36, 37, 38, 40, 42, 43, 44]
        material: "LIME_STAINED_GLASS_PANE"
        name: " "
    
    # do not change this
    version: 1]]>
</code-block></step>
</procedure>

* The default quest file has 50 premade quests, however that would be way too large to paste here, so instead here are 2 simple examples
<procedure title="quests.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
    quests:
      1:
        # example #1 has ALL the possible customizations, you don't have to use most of them
        title: "Kill %required% creepers"
        # chance of this quest appearing
        # can go over 100, optional
        chance: 60
        settings:
          trigger: KILL
          # extra information for the specified trigger, optional
          extra: CREEPER
          # how many actions should it require?
          required: 100
          # if the trigger supports it, it will also decrease the progress when needed
          # for example the break trigger will decrease if the player places the quest block
          # optional
          prevent-cheating: true
          # how many points can they win?
          win-points: 3
        display-item:
          material: CREEPER_HEAD
          name: "&#EE3333&l%title%"
          lore:
            - " "
            - "&#EE3333&lʏᴏᴜ: &f%score%&7/%required%"
            - " "
            - "&#EE3333&lʟᴇᴀᴅᴇʀʙᴏᴀʀᴅ"
            - " &#FF0000%top_1_name%: %top_1_score%"
            - " &#FFAA00%top_2_name%: %top_2_score%"
            - " &#FFFF00%top_3_name%: %top_3_score%"
            - " "
            - "&#EE3333&lʀᴇᴡᴀʀᴅ: &f%points% points"
    
    2:
        title: "Break %required% ancient debris"
        chance: 30
        settings:
            trigger: BREAK
            extra: ANCIENT_DEBRIS
            prevent-cheating: true
            required: 10
            win-points: 5
        display-item:
            material: ANCIENT_DEBRIS
            name: "&#00CCFF&l%title%"
            lore:
            - " "
              - "&#00CCFF&lʏᴏᴜ: &f%score%&7/%required%"
              - " "
              - "&#00CCFF&lʟᴇᴀᴅᴇʀʙᴏᴀʀᴅ"
              - " &#FF0000%top_1_name%: %top_1_score%"
              - " &#FFAA00%top_2_name%: %top_2_score%"
              - " &#FFFF00%top_3_name%: %top_3_score%"
              - " "
              - "&#00CCFF&lʀᴇᴡᴀʀᴅ: &f%points% points"
    
    # do not change this
    version: 1]]>
</code-block></step>
</procedure>