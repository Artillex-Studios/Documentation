# Adding New Rewards

### Adding rewards is simple:
- Go to the menu where you want to add/edit rewards. (the menus can be found at plugins/AxRewards/menus)
- Copy one of the premade rewards from the default menu (or if you deleted it, you can still find it [on our github](https://github.com/Artillex-Studios/AxRewards/blob/master/src/main/resources/menus/default.yml))
- Make sure to change the name of the reward and the `slot` section (slots start from 0 and they go from top left to right)
- Change the things that you would like
- Reload the plugin with /axrewards reload
- And that's it!

### More information
- All the items use our [itembuilder](Item-Builder.md), you can use anything from it.
- It is possible to require a permission for claiming rewards, you can do it by setting the `permission` section.
- The `cooldown` section is required to make the reward claimable multiple times. This is defined in seconds. You can set it to -1 to make a reward never refresh.
- You can define rewards in the `claim-commands` section, it is a list, so you can add as many rewards as you would like. Also use %\player% for the player's name!
- There are 2 or 3 different items that you can set:
  - `claimable` - This item is shown when the reward is claimable
  - `unclaimable` - This item is shown if the reward is already claimed
  - (optional) `no-permission` - This will only show if the reward has a permission and the player is missing it