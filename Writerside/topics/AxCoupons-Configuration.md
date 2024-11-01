# Configuration

### Configuration of the default coupon:
<procedure title="coupons/example.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
    # DOCUMENTATION: https://docs.artillex-studios.com/axcoupons.html
    # ITEM BUILDER: https://docs.artillex-studios.com/item-builder.html
    
    # what permission is needed to claim?
    # set to "" to disable requirement
    permission: ""
    
    # how often this coupon can be activated?
    # set to -1 to make it a one time coupon
    # this value is in seconds
    cooldown: -1
    
    # when should this coupon be available?
    # if the time is out of this range, the coupon will not be redeemable
    # note: you have to set this to the milliseconds since 1970 of the date
    # you can use this website: https://currentmillis.com/ (on the right side input the date and copy the milliseconds number)
    # set to -1 to disable
    activation:
      start: -1
      end: -1
    
    # how many accounts from one IP address can claim a coupon
    # set to -1 to disable
    ip-limit: -1
    
    # you can add multiple commands/items
    rewards:
      commands:
        - "say %player% claimed the example coupon!"
      items:
        - material: IRON_INGOT
          amount: 1
          name: "&bIron Ingot"
    
    # list of sounds: https://www.digminecraft.com/lists/sound_list_pc.php
    # format: sound|volume|pitch
    sounds:
      success: "entity.experience_orb.pickup|1|1"
      fail: "block.anvil.land|1|1"
    
    messages:
      claim: "&#00EEFFYou have successfully claimed the &#00CCFF%name% &#00EEFFcoupon!"
      one-time: "&#00EEFFYou have already claimed the &#00CCFF%name% &#00EEFFcoupon."
      ip-limit: "&#00EEFFYou can't claim the &#00CCFF%name% &#00EEFFcoupon, because your ip address has reached the claim limit."
      on-cooldown: "&#00EEFFYou can't claim the &#00CCFF%name% &#00EEFFcoupon for: &#00CCFF%time%&#00EEFF!"
      inactive: "&#00EEFFYou can't claim the &#00CCFF%name% &#00EEFFcoupon."
      permission: "&#00EEFFYou don't have permission to claim the &#00CCFF%name% &#00EEFFcoupon."
]]>
</code-block></step>
</procedure>