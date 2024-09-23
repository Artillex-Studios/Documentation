# Common Questions

### Why doesn't X booster boost the give command?
- Most of the time the plugin doesn't provide a way for this, also even if they would, this is not a good idea as players can usually use a pay command to send currency between each other, and that would cause infinity money glitches.

### Why would a +50% booster give 1.5x the money/xp?
- We have an in-depth explanation of this [**here**](AxBoosters-How-Multiplier-Works.md)!

### Why is X booster not working?
- Firstly make sure that you are using the right booster, for example there are many plugins that have sell prices.
- Make sure that you have set the booster to use that booster hook, you can search for issues with /axboosteradmin debug.
- Double check if you are using the booster correctly! Did you activate it? (in the /booster menu) Is this booster even supposed to do that? (for example most mobcoin boosters will only boost the mob kill mobcoins)
- If this still doesn't work, report this issue on our [discord server](https://dc.artillex-studios.com/) (and tell us the plugin that use use and it's version)

### Why is there not a setting to prevent two of the same booster from being started?
- It is not possible to implement this. Why?
- Think about it. User A starts a personal booster, if User B start a global one, what are we supposed to do? We can't say that "hey, you can't start a global booster, because someone has a personal booster running", so this issue is not really resolvable.
- Instead, either keep the `multiplier-stacking-mode` on mode 0 or set a limit with the `booster-max-multiplier` setting to prevent abuse!
- Also, we do provide a setting that prevents multiple of the same personal boosters from being started, so if you only give players personal boosters, enable the `prevent-booster-stacking` setting and it should work.

### How can I make different lores for all boosters?
- In the booster's configuration file, you need to add this to the `override-lore` section:
<procedure title="Example" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[override-lore:
      my-boosters:
      - " "
      - "&#0099FFsᴛᴀᴛs"
      - " &8❙ &fAudience: &#0099FF%audience%"
      - " &8❙ &fMultiplier: &#0099FF%multiplier%"
      - " &8❙ &fLength: &#0099FF%length%"
      - " &8❙ &fReceived date: &#0099FF%date%"
      - " "
      - "&#0099FF&l(!) &#0099FFClick here to activate the booster!"
      admin-viewer:
      - " "
      - "&#0099FFsᴛᴀᴛs"
      - " &8❙ &fAudience: &#0099FF%audience%"
      - " &8❙ &fMultiplier: &#0099FF%multiplier%"
      - " &8❙ &fLength: &#0099FF%length%"
      - " &8❙ &fReceived date: &#0099FF%date%"
      - " "
      - "&#0099FF&l(!) &#0099FFClick here to REMOVE booster from the inventory!"
      active-boosters:   
      - " "
      - " &7- &fEnds in: &#0099FF%time_formatted%"
      - " "
      - "&#0099FFsᴛᴀᴛs"
      - " &8❙ &fAudience: &#0099FF%audience%"
      - " &8❙ &fMultiplier: &#0099FF%multiplier%"
      - " &8❙ &fLength: &#0099FF%length%"
      - " &8❙ &fReceived date: &#0099FF%date%"
      - " "
      - "&#0099FF&l(!) &#0099FFClick here to thank them for boosting!"]]>
</code-block></step>
</procedure>