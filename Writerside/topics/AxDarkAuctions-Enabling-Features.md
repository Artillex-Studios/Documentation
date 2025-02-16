# Enabling Features

**In the auction config files there are some features that are commented out (disabled) by default:**
- Auction Time overrides

### How to enable?
- Go to the config file: `plugins/AxDarkAuctions/auctions/<your-auction>.yml`
- Find the part you want to enable, in this example we will enable auction time overrides
- Remove first hashtags from all the related lines, like this:

<tabs>

<tab title="Before">
<code-block lang="yaml" ignore-vars="true" collapsible="false" show-white-spaces="true">
    # this is a way to set per auction times
    # go to the config.yml for the global settings
    # uncomment lines that you want to override for the auction
    times:
    #  start-wait-time: 60
    #  show-time: 5
    #  bid-time: 15
    #  extend-bid-time: true
    #  extend-time: 8
    #  time-between-bids: 5
    #  end-wait-time: 30
</code-block>
</tab>

<tab title="After">
<code-block lang="yaml" ignore-vars="true" collapsible="false" show-white-spaces="true">
    # this is a way to set per auction times
    # go to the config.yml for the global settings
    # uncomment lines that you want to override for the auction
    times:
      start-wait-time: 60
      show-time: 5
      bid-time: 15
      extend-bid-time: true
      extend-time: 8
      time-between-bids: 5
      end-wait-time: 30
</code-block>
</tab>
</tabs>

- Save the file and run /axda reload
- The feature should be enabled! Also make sure to customize it, otherwise there isn't really a point to do this.