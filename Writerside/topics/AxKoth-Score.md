# Score

### How to win in score mode?
* For every second a player stays in the zone, they will gain 1 point (only 1 player can get points at once) - if you get knocked out, the points stay and after either the time runs out or you reach a set time, the winner will be the player with the most points.

### Default Score Koth Config:
<code-block lang="yaml" ignore-vars="true" collapsible="false" show-white-spaces="true">
    <![CDATA[display-name: "&#FFCC00SCORE KOTH"

    # which koth mode should be active? modes:
    # CAPTURE - requires a player to be in the koth zone without getting knocked out for a set time
    # SCORE - every second a player is in the koth zone, their time will increase, at the end the winner will be the player with the most time
    mode: SCORE
    
    # these settings are for the SCORE mode
    settings:
        # if team mode is true, scores will be counter per team instead of per player
        # you must have a team plugin set in your config.yml
        # in team mode, the last capturer player from the team will get the rewards
        team-mode: false
        # the time needed to capture the koth
        # you can set it to -1 to make max time decide the winner
        capture-time-seconds: -1
        # the winner will be announced when the max time is reached
        max-time-seconds: 1200
    
    zone:
        location1: "world;0.0;0.0;0.0;0.0;0.0"
        location2: "world;5.0;5.0;5.0;0.0;0.0"
    
    # format:
    # TOP:<PLACEMENT>:<COMMAND WITHOUT SLASH>
    # or to only give rewards to the TOP1:
    # <COMMAND WITHOUT SLASH>
    reward-commands:
    - "TOP:1:give %player% diamond 3"
    - "TOP:2:give %player% diamond 2"
    - "TOP:3:give %player% diamond 1"
    
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
          - "&f%capturer% &7| &f%timeLeft_formatted%"
    
    bossbar:
        enabled: true
        only-show-when-capturing: false
        # set to -1 to make it that everyone in the world can see it
        # set to 0 to make it that everyone on the server can see it
        view-distance: 64
        name: "&#FF0000%displayName% &#DDDDDD| &#FF6600%capturer% &#DDDDDD(%timeLeft_formatted%)"
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
          - "&#FF0000Leaderboard:"
          - " &#FFFF001. &f%score_1_player%: &f%score_1_points%"
          - " &#FFAA002. &f%score_2_player%: &f%score_2_points%"
          - " &#FF66003. &f%score_3_player%: &f%score_3_points%"
          - " &#FF0000You: &f%score%"
          - " "
          - "&#FF0000Ends in:"
          - " &#444444❙ &f%maxTimeLeft_formatted%"
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