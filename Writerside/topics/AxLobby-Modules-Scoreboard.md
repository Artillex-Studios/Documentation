# Scoreboard

### Description
- Replaces the scoreboard with a custom one

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# how often should the scoreboards? in ticks
# updating is useful to make placeholders update
# 20 ticks = 1 second
# set to 0 to disable
update-ticks: 10

# you can define as many scoreboards as you would like
# note that players will see the FIRST board that they have permission for
# important: this section uses a map list, which might be a bit confusing for YAML beginners, be careful not to break the syntax!
scoreboards:
  # permission example
  - permission: "axlobby.admin"
    title: "&#FF0000&lAxLobby [ADMIN]"
    lines:
      - " "
      - "&#FF0000%player_name%"
      - " &#444444❙ &#FFAAAAPing: &f%player_ping% ms"
      - " "
      - "&#FF0000TPS: %server_tps_1_colored%"
      - " "
      - "&#FF0000play.yourserver.com"
  # no permission example
  - title: "&#FF0000&lAxLobby"
    lines:
      - " "
      - "&#FF0000%player_name%"
      - " &#444444❙ &#FFAAAAPing: &f%player_ping% ms"
      - " "
      - "&#FF0000play.yourserver.com"

# do not change this value
version: 1
    ]]>
</code-block>
