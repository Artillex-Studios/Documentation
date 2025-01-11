# Anti Swear

### Description
- Protects the chat from the blocked words

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# --------------- ANTI SWEARING ----------------

# list of blacklisted words
# you can add as many as you would like
# set to "" to disable
words:
  - "some-really-bad-word"
  - "another-bad-word"

# if someone uses any of the blacklisted words, these will be run
# you can add as many as you would like
# do NOT start the commands with a slash (/)
punishment-commands:
  - "tempmute %player% 5m Swearing!"

# do not change this value
version: 1
    ]]>
</code-block>
