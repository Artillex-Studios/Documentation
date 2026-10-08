# Supported Platforms

### Proxy
- Velocity
- BungeeCord

### Backend server
- Paper
- Spigot
- Folia

> Note: Forks of these projects, like Purpur, Pufferfish, Waterfall, Leaf, etc... should be all fully supported unless they contain huge modifications. (like modded forks)

### Limitations
- Running the bot on multiple backend servers at the same time is not supported can cause issues, we suggest running it on the proxy if you need control over it from multiple servers.
- Giving item rewards is not possible from proxy (Velocity/BungeeCord) servers. In the future we plan on releasing an addon to achieve this. For now we suggest using the bot on the backend server or using a third party proxy plugin to give item/command rewards that need to be given on spigot/paper servers.
- Permissions are not given by default on Velocity servers, you must install LuckPerms and give players access based on the [Commands page](AxDiscordLink-Commands.md).
- The proxy servers don't provide any way to block movements or inventory actions, which can allow players to do some things before confirming their identify with the 2FA system, we suggest setting up a auth/lobby server if you require preventing players from having access. Running commands, server switching and chatting is always blocked for 2FA pending players.