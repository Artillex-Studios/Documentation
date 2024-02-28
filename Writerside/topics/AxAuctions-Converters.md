# Converters

- Converters can be used to move from another plugin to AxAuctions
- Please note that some converters may not keep all values, for example currency usually defaults to vault and expired items get put back on the auction house.

### How to use?

1. Make sure to have the plugin that you are converting from running on the server. (Not all the converters require it, but some do, so it is better to have them loaded)
2. Run `/axahadmin convert \<plugin>` (Use the tab completer for the \<plugin> part!)
3. The converter should have done its job, make sure to check the console for any errors!
4. If there are no errors, remove the other plugin and enjoy axauctions!

### Supported Plugins:
- AuctionHouse (SQLite database only)
- CrazyAuctions
- zAuctionHouse (JSON database only)
- PlayerAuctions (SQLite database only)

> Is there another auction plugin that you would like to have a converter for? Open a ticket on our discord:
<font color="#1f67ff">[dc.artillex-studios.com](https://dc.artillex-studios.com/)</font>