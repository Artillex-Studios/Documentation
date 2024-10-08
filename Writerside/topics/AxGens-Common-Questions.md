# Common Questions

### Why does /selldrops not work?
- If the command doesn't exist, try enabling: `force-register-sell` in the config.yml
- If it just doesn't sell items, make sure to check the `price-plugin` section in the hooks.yml! Also note that if you change this from builtin, the builtin drop prices from tiers.yml will be ignored

### Why does my axgens.limit.X permission does not work?
- Please note that enabling the `team-plugin` section in the hooks.yml will DISABLE the permission limits
- Why? Because with the bukkit api, you can't get permissions of an offline player and the team mode combines team members' limits.
- In the future we might add support for this with the luckperms or vault api, but because that requires external plugins, it feels not worth the effort, just use the `/axgens limit` command to give players higher limits!

### Why are my generator upgrade prices so weired?
- In the tiers.yml you can only customize the price of generators, not their upgrade price
- By default the upgrade prices are calculated like this: `price of next tier - price of current tier`
- You can change this in the config.yml, search for the `generator-price-calculation` section!

### Does this plugin support ItemsAdder or Oraxen?
- Yes, if you want to use custom blocks, check: [Custom Blocks](AxGens-Custom-Blocks.md)
- If you want to make items have a custom texture, check: [Item Builder](Item-Builder.md#custom-model-data)
- (and if you don't know what a custom model data is, ask the ItemsAdder/Oraxen support, and they should be able to help you find it)

### What are levels and how can I gain levels?
- Levels are currently not possible to gain.
- You can disable levels in the config or it is also possible to give levels with the /axgen level command.
- We recommend disabling it OR using a supported level plugin and enabling that in the hooks.yml.
- The only reason why it is enabled so people know how to use the placeholders, it is much easier to remove them if you don't need them.