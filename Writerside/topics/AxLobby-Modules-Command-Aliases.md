# Command Aliases

### Description
- Allows for custom command aliases

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# format:
# <command to run>:
#    - "aliases"
#
# note: you don't need to put a slash (/)
# also currently permissions are not checked, so everyone will be able to tab complete these (don't worry, they still won't run if people don't have the permission)
# important: you might have to restart the server for these to apply
aliases:
  "axlobby lockchat":
    - "lockchat"
  "axlobby clearchat":
    - "clearchat"

# do not change this value
version: 1
    ]]>
</code-block>
