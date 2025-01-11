# Chat

### Description
- Customizes the chat

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# THIS MODULE REQUIRES:
# - PlaceholderAPI (optionally with /papi ecloud download Vault)
# - Vault (optional, but group formats will not work without it)

default-format: "&#FFFFFF%vault_prefix% %player% &#AAAAAA» &#DDDDDD%message%"

group-formats:
  admin: "&#FFAAAA%vault_prefix% %player% &#AAAAAA» &#FFAAAA%message%"

# do not change this value
version: 1
    ]]>
</code-block>
