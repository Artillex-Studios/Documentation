# Converters

- Converters can be used to move from another plugin to AxAuctions
- Please note that some converters may not keep all values, for example currency might default to vault (depends on the plugin) and expiration dates might not match the original.

### How to use?

1. Make sure to have the plugin that you are converting from **running on the server**. (Not all the converters require it, read the table at the bottom of the page)
2. Run `/axahadmin convert \<plugin>` (Use the tab completer for the \<plugin> part!)
3. The converter should have done its job, make sure to check the console for any errors!
4. If there are no errors, remove the other plugin and enjoy axauctions!

### Supported Plugins:

| Plugin         | Converter | Requires Plugin |
|----------------|-----------|-----------------|
| AuctionHouse   | SQLite    | no              |
| CrazyAuctions  | YAML      | no              |
| zAuctionHouse  | JSON      | yes             |
| PlayerAuctions | SQLite    | yes             |
| PlayerShopGUI+ | SQLite    | yes             |
* Plugin - name of the plugin
* Converter - we can only convert if you use this database type in the plugin you are converting from (you can set axauctions' database to anything)
* Requires Plugin - do you need to have the plugin running on the server when you run the converter?

> Is there another auction plugin that you would like to have a converter for? Open a ticket on our discord:
<font color="#1f67ff">[dc.artillex-studios.com](https://dc.artillex-studios.com/)</font>