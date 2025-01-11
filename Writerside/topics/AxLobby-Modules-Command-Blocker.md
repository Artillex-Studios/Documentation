# Command Blocker

### Description
- Blocks or allows certain commands

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# list of whitelisted/blacklisted commands
# important: don't start them with a slash (/)
#
# some supported regex:
# - 'say' #  only say is allowed
# - 'say*' #  allows commands starting with say
# - '*say' #  allows commands ending with say
# - '*say*' #  allows commands containing say
# modes: BLACKLIST (disallowed commands), WHITELIST (allowed commands)
mode: BLACKLIST
commands:
  - pay*
  - bal*

# do not change this value
version: 1
    ]]>
</code-block>
