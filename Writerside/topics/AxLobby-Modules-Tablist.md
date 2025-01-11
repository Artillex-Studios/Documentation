# Tablist

### Description
- Replaces the tablist with a custom one

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# how often should the tab header/footer update? in ticks
# updating is useful to make placeholders update
# 20 ticks = 1 second
# set to 0 to disable
update-ticks: 10

# you can define as many tablists as you would like
# note that players will see the FIRST tablist that they have permission for
# important: this section uses a map list, which might be a bit confusing for YAML beginners, be careful not to break the syntax!
tablists:
  # permission example
  - permission: "axlobby.admin"
    # set to [] to disable (example: header: [])
    header:
      - ' '
      - '<gradient:#ff4500:#ff1493><b>AxLobby ADMIN</b></gradient>'
      - "&#ff4500TPS: &f%server_tps_1_colored%"
      - ' '
    footer:
      - '&#ff4500%bungee_total% &fplayers online'
      - ' '
      - '&#ff4500play.yourserver.com'
  # no permission example
  - header:
      - ' '
      - '<gradient:#ff4500:#ff1493><b>AxLobby</b></gradient>'
      - ' '
    footer:
      - '&#ff4500%bungee_total% &fplayers online'
      - ' '
      - '&#ff4500play.yourserver.com'

# do not change this value
version: 1
    ]]>
</code-block>
