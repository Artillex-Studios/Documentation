# Join & Leave Messages

### Description
- Sends messages when players join or leave

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# the message will be sent to the player right after they join
message-of-the-day:
  enabled: true
  # delay to send the message
  # in ticks
  # 20 ticks = 1 second
  delay-ticks: 10
  message:
    - " "
    - "&#FF4500Welcome &f%player%&#FF4500!"
    - "&#FFAAAABuy perks @ shop.example.com"
    - " "


# if you define more than 1, it will randomly select one of them
# you can set it to a [] to disable the message completely (example: join-message: [])
join-message:
  - "&#00FF00&l(+) &#AAFFAA%player%"

quit-message:
  - "&#FF0000&l(-) &#FFAAAA%player%"

# do not change this value
version: 1
    ]]>
</code-block>
