# Performance Optimizations

* This page contains information about common performance bottlenecks and how can they be solved in AxHoes.

### Block breaking/setting lag
- If hundreds of players are breaking the same few blocks and they are all getting block updates, that can be really heavy for your server.
- AxHoes has a builtin packet regenerator mode, which make the impact of block breaking on the main thread go to 0%, instead it uses packets to update crops for players.
- In the config, enable the `regenerator-mode` -> `packet` setting! You can even make players have their own 'virtual' crops by enabling the `per-player` option.
- Note that this isn't magic, it will increase your netty threads' usage and may cause pings to spike if your server can't handle it.

### High netty (or network) usage
- Usually this is caused by the lore updates. Every time a player breaks a crop, the server resends the item's lore, which can get really heavy.
- To improve this, try increasing the `lore-cache-milliseconds` setting. This setting controls how often should hoe lores update their stats, a high value could be quite annoying for players.

### Economy plugin caused lag
- Some economy plugins, like EssentialsX which update data files on the main thread, which can cause bad performance and it can also increase disk usage if millions of currency updates are sent every minute.
- To fix this, AxHoes comes with a builtin `currency-give-seconds` setting which works in a simple way. It tracks all gained currencies and gives them every X seconds, this drastically reduces load on your server.
- Generally the default value is safe, however if you notice anything related your economy plugin in sparks, try increasing this value!

### Shop plugin caused lag
- If you have hundreds of players and they are all using auto sell, that can mean that thousands of items are sold every second, and some shop plugins are not equipped to handle this much price requests.
- To solve this, AxHoes has a builtin `enable-global-price-caching` option, which can decrease this load by almost 100% when enabled.
- The drawback is that enabling this will break every price modifier.
- If your server doesn't utilize price modifiers, enabling this is highly recommended.