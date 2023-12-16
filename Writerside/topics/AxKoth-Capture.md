# Capture

### How to win in capture mode?
* You must stay in the koth zone for x seconds without getting knocked out. The winner is the player, who can stay in for the whole capture time.

### Default Capture Koth Config:
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[display-name: "&#FF0000CAPTURE KOTH"
    
    # which koth mode should be active? modes:
    # CAPTURE - requires a player to be in the koth zone without getting knocked out for a set time
    # SCORE - every second a player is in the koth zone, their time will increase, at the end the winner will be the player with the most time
    mode: CAPTURE
    
    # these settings are for the CAPTURE mode
    settings:
      # the time needed to capture a koth
      capture-time-seconds: 180
      # if a player stops capturing the koth, should the timer reset?
      capture-end-reset-time: true
      # the max time a koth can run for
      # set to -1 to make it run until someone wins
      max-time-seconds: 7200
      # if the max time is reached, should the player who is currently capturing get the rewards?
      end-reward-capturer: false
    
    zone:
      location1: "world;0.0;0.0;0.0;0.0;0.0"
      location2: "world;5.0;5.0;5.0;0.0;0.0"
    
    reward-commands:
      - "give %player% diamond 1"
    
    # set to -1 to make it that everyone in the world can see it
    # set to 0 to make it that everyone on the server can see it
    # how far should the messages.yml broadcasts section messages reach?
    broadcast-distance: 0
    
    starter:
      enabled: true
      material: "BLAZE_POWDER"
      glow: true
      name: "&#FF0000%displayName% Koth Starter"
      lore:
        - " "
        - "&#FF0000Information:"
        - " &#444444❙ &#FFAA66Location: &f%x%; Y%y%; Z%z%"
        - " &#444444❙ &#FFAA66Time: &f%time_formatted%"
        - " &#444444❙ &#FFAA66Max Time: &f%maxTime_formatted%"
        - " "
        - "&#FF0000ᴄʟɪᴄᴋ ᴛᴏ sᴛᴀʀᴛ"
    
    # automatically start the koth at certain times
    # this uses the cron format:
    # https://crontab.cronhub.io/
    # you can add multiple lines
    schedules:
      - "0 0 18 * * ?"
    
    # set to 0 to disable
    # this is ONLY checked on schedule start & starter use
    minimum-players: 0
    
    hologram:
      enabled: true
      location-offset:
        x: 0
        y: 3
        z: 0
      line-height: 0.3
      lines:
        - "&#FF0000&l%displayName%"
        - "&f%capturer_raw% &7| &f%timeLeft_formatted%"
    
    bossbar:
      enabled: true
      only-show-when-capturing: false
      # set to -1 to make it that everyone in the world can see it
      # set to 0 to make it that everyone on the server can see it
      view-distance: 64
      name: "&#FF0000%displayName% &#DDDDDD| &#FF6600%capturer_raw% &#DDDDDD(%timeLeft_formatted%)"
      # colors: https://javadoc.io/static/net.kyori/adventure-api/4.11.0/net/kyori/adventure/bossbar/BossBar.Color.html
      color: RED
      # styles: https://javadoc.io/static/net.kyori/adventure-api/4.11.0/net/kyori/adventure/bossbar/BossBar.Overlay.html
      style: NOTCHED_20
    
    scoreboard:
      enabled: true
      only-show-when-capturing: false
      # set to -1 to make it that everyone in the world can see it
      # set to 0 to make it that everyone on the server can see it
      view-distance: 64
      title: "&#FF0000&l%displayName%"
      lines:
        - " "
        - "&#FF0000Location:"
        - " &#444444❙ &fX%x%; Y%y%; Z%z%"
        - " "
        - "&#FF0000Capturer:"
        - " &#444444❙ &f%capturer_raw%"
        - " "
        - "&#FF0000Time:"
        - " &#444444❙ &f%timeLeft_formatted%"
        - " "
        - "&#FF0000play.yourserver.com"
    
    # These are all the options that you can use in the webhook section: (most of them are optional, you can remove them)
    #    # the message before the embed, you can put a ping here in the <@&1234567890123456789> format
    #    content: "<@&1234567890123456789>"
    #    # color in hex
    #    color: "#FF6600"
    #    description: "Your description"
    #    title:
    #      # required
    #      text: "Title!"
    #      icon: ""
    #    author:
    #      # required
    #      name: "Author name"
    #      icon-url: ""
    #      url: ""
    #    footer:
    #      # required
    #      text: "Footer"
    #      icon: ""
    #    image-url: ""
    #    thumbnail-url: ""
    #    fields:
    #      1:
    #        # required
    #        inline: false
    #        # required
    #        name: "Field1"
    #        # required
    #        value: "Value1"
    webhook:
      # your webhook url here
      url: ""
      start:
        enabled: true
        content: "Get ready!"
        color: "#FF0000"
        title:
          text: "%name% - STARTED"
        fields:
          1:
            inline: true
            name: "Time"
            value: "%timeLeft_formatted%"
      stop:
        enabled: true
        color: "#CC0000"
        title:
          text: "%name% - STOPPED"
        fields:
          1:
            inline: true
            name: "Time"
            value: "%timeTaken_formatted%"
      capture-start:
        enabled: true
        color: "#AAFFAA"
        title:
          text: "%name% - CAPTURE STARTED"
        fields:
          1:
            inline: true
            name: "Capturer"
            value: "%capturer_name%"
          2:
            inline: true
            name: "Team"
            value: "%capturer_team_name%"
          3:
            inline: true
            name: "Time"
            value: "%timeLeft_formatted%"
      capture-end:
        enabled: true
        color: "#FFAAAA"
        title:
          text: "%name% - CAPTURE STOPPED"
        fields:
          1:
            inline: true
            name: "Capturer"
            value: "%capturer_name%"
          2:
            inline: true
            name: "Team"
            value: "%capturer_team_name%"
          3:
            inline: true
            name: "Time"
            value: "%timeLeft_formatted%"
      captured:
        enabled: true
        content: ":tada:"
        color: "#00FF00"
        title:
          text: "%name% - CAPTURED"
        fields:
          1:
            inline: true
            name: "Capturer"
            value: "%capturer_name%"
          2:
            inline: true
            name: "Team"
            value: "%capturer_team_name%"
          3:
            inline: true
            name: "Time"
            value: "%timeTaken_formatted%"]]>
</code-block>