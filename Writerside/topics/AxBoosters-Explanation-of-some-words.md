# Explanation of Some Words

### Active Booster
- Active boosters always refer to the boosters that were activated by either a player or the server.
- They are made up from a Booster and a start date

### Booster
- Boosters are the most important internally, they are used for most kind of boosters.
- They are made up from a Booster Type and other fields (multiplier, owner, length, audience, date)

### Booster Type
- Booster Types are what your configured boosters are called.
- They can be found in the plugins/AxBoosters/boosters folder, you can edit them, remove them, this can also be done in the /axboostersadmin editor > Boosters menu
- Note: A single booster type can have an unlimited number of booster hooks active, not the other way around!

### Booster Hook
- Booster hooks are the smallest group, they are registered by external plugins (and there are some builtin ones)
- You can check the list of avaliable ones on your server in the /axboostersadmin editor > Loaded Booster Hooks menu!

### Audience
- An audience is the group that is affected by a certain booster.
- More information: **[Audience](AxBoosters-Audiences.md)**