# Common Issues

### My graves are not storing items or xp, instead they are dropped on the ground.
- This is most often caused by some third party plugin, most often keep invetory plugins. The first thing that you should check is that your keepinventory gamerule is not enabled. (`/gamerule keep_inventory` should be false) Next try removing your permissions to see if some plugin is giving you keep inventory. (for example EssentialsX has a `essentials.keepinv`/`essentials.keepxp` permission given by default to OP users)
> You can try to enable the `override-keep-inventory` and `override-keep-level` settings in the AxGraves config if you suspect that this is the issue. After changing settings, run `/axgraves reload` to apply the changes.
- If none of these are the case, then we will have to look for a faulty third party plugin.
> On Paper servers you can list all plugins that use this event with the `/paper dumplisteners org.bukkit.event.entity.PlayerDeathEvent` command. If you want to figure out which one is causing it, hover on them and look for ones with event priorities like LOWEST, LOW, NORMAL. Try removing them one by one until the issue is resolved.
- If you don't want to go plugin hunting, you can solve this by decreasing the event priority of AxGraves, to make its tasks run before other plugins. Go to the `plugins/AxGraves/config.yml` and find the `death-listener-priority` setting. Try decreasing this value, setting this to `LOWEST` will solve this issue as it will make AxGrave run first. You will have to restart your server after changing this setting for it to apply.
- By default, the plugin uses the `HIGHEST` listener priority for compatibility reasons, however if you have plugins that misuse death events, this might be necessary to override them.
- If this still didn't solve the issue, the only possible things are that the conflicting plugin is using the `LOWEST` priority as well. (unlikely) Or the more likely is that you have some AxGraves settings misconfigured. Make sure that the `store-items` and the `store-xp` settings are enabled. You can also try to enable `override-keep-inventory` and `override-keep-level` to make sure. After changing these values, run the `/axgraves reload` command to apply the modifications.

### My grave heads sometimes turn black when they spawn on a block.
- This happens when the grave entity clips into the block and on some minecraft versions it can instantly turn the grave dark.
- Check if the player who has this issue is using the same minecraft version as your server.
- If not: Go to the `plugins/ViaVersion/config.yml` and try tweaking the `hologram-patch`, `hologram-y` options to move the holograms a bit higher.
- If they are using the server's version, then you can make these changes by increasing the `plugins/AxGraves/config.yml` → `head-height` option. You might need to restart the server for the changes to apply to existing graves.