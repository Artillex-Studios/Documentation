# Updating to V3

### Recommendations
- Try the updating process first on a test/local server.
- Take a backup of the axboosters folder.
- Check the console for errors, if you see any concerning AxBoosters errors, contact us.
- If you run a seasonal server, I would just recommend waiting with this update and starting clean, reconfiguring everything. Why? The new files are much cleaner and have some extra placeholders that you will not be able to see if you are updating from an old version. Of course, if this is not a problem for you, you can update.

### Updating process
- Stop the server
- Take a backup of the AxBoosters folder
- Put in the new jar, remove the old jar
- Start the server
- The migration will start, some things will need **MANUAL CHANGES**:
  - **guis.yml** (there were many changes, you will have to reconfigure it yourself)
  - The **commands now use PERCENTAGE format instead of the decimal format** in multipliers, make sure to read and change all commands that you use: **[How Multiplier Works?](AxBoosters-How-Multiplier-Works.md)**
    - This means that you need to replace for example:
    - **OLD:** /axboosteradmin activate <\player> BoosterType global **1.5** 1m
    - **NEW:** /axboosteradmin activate <\player> BoosterType global **50** 1m
  - There is a new hooks.yml, you should make changes, some parts of it are visible to players in the main guis
  - You should also delete all Booster Types from the AxBoosters/boosters folder that you have never used, now you can use the **/axboosteradmin editor** to create them when you need them!
  - Also while you are there, go through all the booster configurations as there are some new texts that you might want to customize
  - Make sure you read through the config.yml and lang.yml, there are some new sections.

That's all, the database should be automatically converted.

**If you have trouble updating, we are happy to help you on our support discord server:** [dc.artillex-studios.com](https://dc.artillex-studios.com/)