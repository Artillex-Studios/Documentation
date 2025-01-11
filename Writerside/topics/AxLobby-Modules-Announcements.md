# Announcements

### Description
- Sends an announcement periodically to all online players

### Configuration 
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# how often should an announcements be sent?
# in seconds
announce-time-seconds: 30

# should the announcements be randomized?
# if disabled, they will show up in order
randomize-announcements: false

announcements:
  - message:
      - " "
      - "&#ff4500You are currently playing on &#ffaaaa&nplay.example.com&#ff4500!"
      - " "
    click-url: "https://docs.artillex-studios.com/axlobby.html"
  - message:
      - " "
      - "&#00ffffYou are using the &#aaffff&nAxLobby&#00ffff plugin! :)"
      - " "
    click-command: "axlobby help"
  - message:
      - " "
      - "&#ffff00Make sure to leave a &#ffffaa&nreview&#ffff00 if you enjoy the plugin!"
      - " "
    click-url: "https://docs.artillex-studios.com/axlobby.html"

# do not change this value
version: 1
    ]]>
</code-block>
