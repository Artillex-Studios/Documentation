# Configuration

## config.yml

### dupe-protection (default: false)

* This only works for UNSTACKABLE vouchers!
* This setting does NOT support copying items in creative!
* If you want to do that, don't. Use the command to give the player a new voucher.

> This setting does not actually prevent duping!
> This only prevents the use of vouchers that exceed the amount given.
> {style="warning"}

### prevent-crafts (default: true)

* If a voucher is used in a crafting recipe, we set the result to nothing.

### send-requirement-fail (default: true)

* If we should send which requirement failed, the messages are customizable in the messages.yml!

## Voucher yml

### item

* Please refer to [the Item Builder](Item-Builder.md)

### actions

* Refer to [the actions configuration](Actions.md)

* Example:

```yaml

actions:
  - "[player] spawn"
  - "[console] say %\player% is cool!"
```

### random-actions

* If you have random actions and actions, both will run!
* Refer to [the actions configuration](Actions.md)

* Example:

```yaml

random-actions:
  - chance: 25
    actions:
      - "[player] I like the taste of water!"
```

### placeholders

* Placeholders can come really handy when using the plugin
* You can create vouchers that have placeholders that are resolved in the lore,
name type of the item, or in the actions.

```yaml

placeholders:
  - "name"

```

### requirements

* Refer to [the requirements configuration](Requirements.md)

* Example:

```yaml

requirements:
  - "[permission] your.permission.node"
  - "[world] world"
```

### items

* You can add your items here, which you can refer to in rewards
* Please refer to [the Item Builder](Item-Builder.md)

* Example:

```yaml

items:
  - id: 1
    type: stone
    name: "Stone"
  - id: 2
    type: blaze_rod
    name: "Blaze rod"
```

### cooldown

* The cooldown of the voucher in seconds

### stackable

* If the voucher is stackable. If enabled, the item won't be stackable.

### consume

* If the voucher needs to be consumed, for example eaten.

### confirm

* If the player needs to click twice to activate the voucher

<procedure title="example.yml" collapsible="true"><step>
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
  <![CDATA[item:
  type: "stone_sword"
  name: "<red>Sword"

actions:
- "[player] spawn"
- "[console] say %player% has got some serious weapons now! <name>" # The name placeholder is used here
- "[firework] #ff0000,ball"
- "[sound] entity_player_levelup,0.5,0.2"
- "[item] 1" # You can check the items a bit further down!

random-actions:
- chance: 25
  actions:
    - "[player] I like oreos!"

placeholders:
  - "name"

requirements:
- "[permission] your.permission.node"
- "[!permission] the.permission.you.dont.want" # You can use a ! to negate the expression
- "[world] world|world2"
- "[placeholder] %player_name%=Karcsi"

items:

- id: 1
  type: stone
  name: "Stone"

cooldown: 30 # Seconds
stackable: false
consume: false # If the player needs to consume (for example, eat) the item to use it
confirm: true # If you need to click twice to use this voucher]]>
</code-block></step>
</procedure>