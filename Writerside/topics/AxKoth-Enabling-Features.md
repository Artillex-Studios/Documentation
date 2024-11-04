# Enabling Features

**In the koth config files there are some features that are commented out (disabled) by default:**
- Item Rewards
- Per Koth Broadcast Messages
- Koth Start/End Commands
- Capture Start/End Commands

### How to enable?
- Go to the config file: `plugins/AxKoth/koths/<your-koth>.yml`
- Find the part you want to enable, in this example we will enable item rewards
- Remove first hashtags from all the related lines, like this:

<tabs>

<tab title="Before">
<code-block lang="yaml" ignore-vars="true" collapsible="false" show-white-spaces="true">
    ## ---- REMOVE FIRST HASHTAGS FROM ALL LINES TO ENABLE THIS FEATURE! -----
    #reward-items:
    #  - material: diamond
    #    name: "&#00FFFFShiny diamond"
    #    amount: 1
    #  - material: iron_ingot
    #    name: "&#DDDDDDShiny iron"
    #    amount: 3 
</code-block>
</tab>

<tab title="After">
<code-block lang="yaml" ignore-vars="true" collapsible="false" show-white-spaces="true">
    # ---- REMOVE FIRST HASHTAGS FROM ALL LINES TO ENABLE THIS FEATURE! -----
    reward-items:
      - material: diamond
        name: "&#00FFFFShiny diamond"
        amount: 1
      - material: iron_ingot
        name: "&#DDDDDDShiny iron"
        amount: 3 
</code-block>
</tab>
</tabs>

- Save the file and run /axkoth reload
- The feature should be enabled! Also make sure to customize it, you probably don't want to give the default items.