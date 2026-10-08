# Webhooks

### What can it do?
- AxDiscordLink contains a powerful webhook system, which can be used to send discord webhooks from any event on the server.
- Creating new webhooks requires basic programming knowledge as it uses the event class's internals to extract variables.
- As a benefit, you can send a webhook after ANY event on the server coming from any plugin. You can also use any parameter from event classes.

### Example

<tabs>

<tab title="Spigot/Paper">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

    enabled: false
    # the discord channel id where this section should be sent
    channel: ""
    # the event class that should trigger sending a section
    event: "org.bukkit.event.player.PlayerJoinEvent"
    
    # the section to send, you can use all fields from our discord section builder
    webhook:
    embeds:
    - title:
      text: "Join Event"
      description: "%getPlayer.getName% has joined the server."
      color: "#FFFFAA"

]]>
</code-block>
</tab>

<tab title="Velocity">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

    enabled: false
    # the discord channel id where this section should be sent
    channel: ""
    # the event class that should trigger sending a section
    event: "com.velocitypowered.api.event.connection.PostLoginEvent"
    
    # the section to send, you can use all fields from our discord section builder
    webhook:
    embeds:
    - title:
      text: "Join Event"
      description: "\%getPlayer.getUsername% has joined the server."
      color: "#FFFFAA"

]]>
</code-block>

</tab>

<tab title="BungeeCord">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

    enabled: false
    # the discord channel id where this section should be sent
    channel: ""
    # the event class that should trigger sending a section
    event: "net.md_5.bungee.api.event.PostLoginEvent"
    
    # the section to send, you can use all fields from our discord section builder
    webhook:
    embeds:
    - title:
      text: "Join Event"
      description: "\%getPlayer.getName% has joined the server."
      color: "#FFFFAA"

]]>
</code-block>

</tab>
</tabs>

### How it works?
- The java class fields and getter methods are converted into text and can be used as placeholders.
- You can run methods in sub parent classes as well, for example in PlayerJoinEvent to get the player's name, first we need to get the player object from the event (getPlayer) and then the name from the player object, (getName) which results in: %\getPlayer.getName%
- The plugin works backwards, it first takes placeholders from the webhook and tries to find them in the event class, this way no unexpected methods are accidentally called.

> Be careful when using any method which is not simple getter as they are called and their modifications will take effect even if you are just using them to get a value for a webhook.
{style="warning"}