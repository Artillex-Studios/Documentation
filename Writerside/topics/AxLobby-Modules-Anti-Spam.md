# Anti Spam

### Description
- Protects the chat from spammers

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

rules:
  # how many messages are allowed within the given timespan?
  max-messages: 3
  # if the max-messages is reached within this time, the player will be punished
  within-seconds: 3
  # if the player is punished, how long should the not be able to chat?
  # note: this is not the same as a mute, it will only temporarily stop players from chatting
  # you should disable the punishment-commands if you are happy with this
  penalty-seconds: 10

# if someone uses any of the blacklisted words, these will be run
# you can add as many as you would like
# do NOT start the commands with a slash (/)
# disable these by setting it to a [] (punishment-commands: [])
punishment-commands:
  - "tempmute %player% 1m Spam!"

# do not change this value
version: 1
    ]]>
</code-block>
