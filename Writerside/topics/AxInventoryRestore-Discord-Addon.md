# Discord Addon
* To use the discord addon, you need to enable the `enable-discord-addon` setting in the plugins/AxInventoryRestore/config.yml!
![image_80.png](image_80.png)
* Once this is done, reload the plugin with /axir reload and open the generated discord.yml.

## Discord Webhook
* Toggleable webhook events: backup-create, backup-restore, backup-export
![image_81.png](image_81.png)

### How to set up webhooks?
1. Go to the channel where you want the webhooks to be sent and click on "Edit Channel"
![image_38.png](image_38.png)
2. Click on the "Integrations" tab and then click on "Create Webhook"
![image_77.png](image_77.png)
3. Open the webhook that you just created and click on "Copy Webhook URL"
![image_78.png](image_78.png)
4. Go to the discord.yml in the plugins/AxInventoryRestore folder and find the webhook URL section.
5. Paste the copied URL
![image_79.png](image_79.png)

*It should look something like this, feel free to customize the settings, then run /axir reload and test it!*

## Discord Bot

This feature allows staff with the `axinventoryrestore.discord-request` permission send a discord embed with 2 buttons to a discord server:

<p>Minecraft side:</p>

![image.png](image.png)

<p>Discord side:</p>

![image_1.png](image_1.png)

![image_2.png](image_2.png)

When the restore button is pressed, the player will receive the restored inventory.

### How to set up the discord bot?
1. Go to the [_discord developer portal_](https://discord.com/developers/applications).
2. Create a new application that will be used for your bot
![image_82.png](image_82.png)
![image_83.png](image_83.png)
3. Go to the "Bot" section
![image_84.png](image_84.png)
4. Click on "Reset Token" and generate a new token
![image_85.png](image_85.png)
5. Copy the generated token (note: don't ever share this with anyone or else they be able to take over your bot with it)
![image_86.png](image_86.png)
6. Go to the discord.yml in the plugins/AxInventoryRestore folder, find the `token` section and paste the token there.
![image_87.png](image_87.png)
7. Go back to the discord developer portal and now choose the "Installation" option
8. Here first uncheck the "User Install" option, then add "bot" to the Guild Install -> Scopes, then set up the permission that you want for the bot (you can skip this if you want to set it up later) - and lastly, press on "Save Changes"
![image_88.png](image_88.png)
9. Next, invite the bot with the link that can be found at the "Install Link" section, after that select your server.
10. After that make sure [_copy the ID of the channel_](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID#h_01HRSTXPS5FMK2A5SMVSX4JW4E) where you want the bot to post. (make sure to give the required permissions to the bot if you haven't yet!)
11. In the discord.yml find the `channel-id` and put the copied value there.
![image_89.png](image_89.png)
12. Everything should be good! Run /axir reload and test the bot. Make sure to test the bot, look in the console for missing permissions or other problems if it wouldn't work.
13. Optional: Go back to the "Installation" page, set the Install Link to `None` and on the "Bot" page uncheck the "Public Bot" value! (if you don't do this, other will also be able to invite your bot)