# First Time Setup

1. Place the plugin's jar into your server's plugins folder.
2. Restart the server and go to the newly generated `plugins/AxDiscordLink` (on Velocity folder names are in lowercase) folder.
3. If you see a `token.secret` file, you did it correctly, now open that and put it aside.
4. Next we need to create the discord bot, because we are using our own bot, this needs to be done on discord's developer portal.
5. Head to the [Discord Developer Portal](https://discord.com/developers/applications) and click on "New Application".

![image_279.png](image_279.png)

6. Give it a name, (you can name it anything) accept Discord's Terms of Services and click on "Create".

![image_280.png](image_280.png)

7. Go to the "Bot" section on the left.

![image_281.png](image_281.png)

8. Next, optionally you can give your bot a username, icon, banner.
9. Click on the "Reset Token" button, then click on "Yes, do it!" in the confirmation modal.

![image_282.png](image_282.png)

10. Copy the token and paste it into the `token.secret` text file that we have opened. (delete everything from the text file before pasting)

![image_283.png](image_283.png)

> Never share this token with anyone, otherwise they will be able to take over your discord bot and execute anything with it.
{style="warning"}

11. After you have saved the `token.secret` file, the next is going to be setting up the intents of the bot and then inviting it to your discord guild.
12. Scroll down to the "Privileged Gateway Intents" section and enable the "Server Members Intent".

![image_284.png](image_284.png)

*This is required for the automatic `Discord → Minecraft` role sync to work. You can keep this disabled if you are not planning on using that.*
> If your server has more than 10.000 members, you might need to verify yourself.

13. After the modifications, make sure to click on "Save Changes".

![image_285.png](image_285.png)

14. Go to the "Installation" section on the sidebar.

![image_286.png](image_286.png)

15. At the bottom, click into the "Guild Install" and add `bot` to it.

![image_287.png](image_287.png)

16. Give the bot all the required permissions.

![image_288.png](image_288.png)

*The `Manage Nicknames` is used for the nickname sync, the `Manage Roles` for the role sync and the `Send Messages` for the webhooks, you don't have to give this, you can also manually give access to webhook channels later.*

17. After the modifications, make sure to click on "Save Changes".

![image_285.png](image_285.png)

18. Scroll up and copy the "Install Link".

![image_289.png](image_289.png)

19. Paste the link into a browser and add the bot to your server.

20. After that you should see that the bot has joined, however there are still a few more steps.

21. First lets quickly make it impossible for people to invite our bot. In the same "Installation" interface set the "Install Link" to `none`.

![image_290.png](image_290.png)

22. After the modifications, make sure to click on "Save Changes".

![image_285.png](image_285.png)

23. Go back to the "Bot" section on the sidebar and disable the "Public Bot" setting.

![image_292.png](image_292.png)

24. After the modifications, make sure to click on "Save Changes".

![image_285.png](image_285.png)

25. Next go to your discord server. If you are planning on using the bot to sync roles to from Minecraft to Discord, then you must move the bot **above** all the user roles. This is an example of that set up in the `Server Settings → Roles`:

![image_291.png](image_291.png)

*This is required, otherwise the bot won't have the permission to add roles above itself. This is also safe, because we didn't give any unnecessary permissions to the bot.*

26. We will also need to give our discord bot the ID of our discord guild, so it can retrieve the members. For this, you need to enable Discord's "Developer Mode".

27. If you don't have it enabled, go to the "User Settings", scroll to the bottom and click on the "Developer" option. In that menu, toggle "Developer Mode" on.

![image_293.png](image_293.png)

28. Right-click on your discord guild's icon or name and click on "Copy Server ID"

![image_294.png](image_294.png)

29. Next go to the plugin's config.yml (plugins/AxDiscordLink/config.yml) and replace the bot -> guild-id value with the ID that you have copied.

![image_295.png](image_295.png)

30. Save the file and run `/axdiscordlink reload` ingame. If you see the `[AxDiscordLink] Bot successfully started on the <name> discord guild!` message in the console, everything is set up correctly!

> If you have any issues, first read through the error as it can be quite useful and if you need assistance, [contact us](https://dc.artillex-studios.com/).

**If everything is working, then we are ready! Next, you can customize the plugin to your server's needs.**