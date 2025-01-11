# Bossbar

### Description
- Makes a rotating bossbar appear for all players

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# how long should a single bossbar be shown?
# 20 ticks = 1 second
bar-stay-ticks: 180

# how often should the bossbar update? in ticks
# 20 ticks = 1 second
bar-update-every-x-ticks: 12

# should the bars be randomized?
# if disabled, they will show up in order
randomize-bars: false

# the plugin will keep rotating between all the bars
bars:
  # this is first example bar
  - name: "&#ff4500You are currently playing on &#ffaaaa&nplay.example.com&#ff4500!"
    # colors: https://javadoc.io/static/net.kyori/adventure-api/4.11.0/net/kyori/adventure/bossbar/BossBar.Color.html
    color: RED
    # styles: https://javadoc.io/static/net.kyori/adventure-api/4.11.0/net/kyori/adventure/bossbar/BossBar.Overlay.html
    style: NOTCHED_20

  # this is second example bar
  - name: "&#00ffffYou are using the &#aaffff&nAxLobby&#00ffff plugin! :)"
    # colors: https://javadoc.io/static/net.kyori/adventure-api/4.11.0/net/kyori/adventure/bossbar/BossBar.Color.html
    color: BLUE
    # styles: https://javadoc.io/static/net.kyori/adventure-api/4.11.0/net/kyori/adventure/bossbar/BossBar.Overlay.html
    style: NOTCHED_20

  # this is third example bar, you can add more in the same way, just be careful with the syntax
  - name: "&#ffff00Make sure to leave a &#ffffaa&nreview&#ffff00 if you enjoy the plugin!"
    # colors: https://javadoc.io/static/net.kyori/adventure-api/4.11.0/net/kyori/adventure/bossbar/BossBar.Color.html
    color: YELLOW
    # styles: https://javadoc.io/static/net.kyori/adventure-api/4.11.0/net/kyori/adventure/bossbar/BossBar.Overlay.html
    style: NOTCHED_20

# do not change this value
version: 1
    ]]>
</code-block>
