# Groups

## What are groups?

Your vanished players can be categorized into different groups, that you can give them.
These groups determine what they can do, where they're hidden from, or who they can see.

## Default groups.yml

```yaml

groups:
  default:
    priority: 1 # Higher priorities can see lower priorities
    capabilities:
      - type: silent_open
      - type: invincible
      - type: flight
      - type: chat
        bypass-prefix: "!" # The bypass prefix
      - type: prevent
        actions:
          - "block_break"
          - "block_place"
          - "block_change"
          - "entity_target"
          - "damage"
          - "pickup"
          - "hunger"
          - "item_drop"
          - "interact"
          - "tab_complete"
          - "command_use"
      - type: action_bar
        message: "<white>You are currently vanished!"
        refresh-interval: 20 # In ticks
      - type: message
        join: ""
        leave: ""
      - type: potion_effects
        effects:
          - "night_vision 10" # Potion type, amplifier

config-version: 1
```

## Giving groups

Well, first off the name of the group here is `default`. The name of the group is what determines the permission
for being in the group.

To be in this group, you need to give the `axvanish.group.default` permission, where you replace default
with the name of the group which you'd like to give.

For example, if we create a new group called `admin`, then we will need to give the `axvanish.group.admin` permission.

## Configuring the abilities of groups

- `priority`: determines who the players of this group can see. If you have two groups, one named admin, one default,
  then if we give the default group a priority of 1, and the admin group a priority of let's say 2, then the players of
  the admin group will be able to see the players of the default group while vanished, but if a player from the admin
  group goes into vanish, the players of group default will not be able to see that player.

- `capabilities`: these determine what happens while the player is vanished, which actions are prevented, and what extra
  functionalities are given to vanished players.

## Configuring capabilities
By default, the plugin has a few important capabilities, but this can be expanded by using our developer API.

The default capabilities are:
### Action bar
Sends the player an action bar message while vanished.

- `type`: action_bar
- `message`: The message, that you'd like to have as the text, you can use PlaceholderAPI placeholders in here.
- `refresh-interval`: The interval in ticks of how often the actionbar refreshes.

### Chat
Prevents the user from chatting, if enabled.

- `type`: chat
- `bypass-prefix`: The character or string of characters which needs to be put in front of the message to be sent even while in vanish.

### Flight
Gives the player the ability to fly.

- `type`: flight


### Invincible
Gives the player invincibility.

- `type`: invincible

### Message
Determines the messages to send when the player enters/quits vanish, this is broadcasted to the whole server.

- `type`: message
- `join`: The message to broadcast to the server when the player unvanishes.
- `leave`: The message to broadcast to the server when the player vanishes.

### Potion effects
Gives the player potion effects.

- `type`: potion_effects
- `effects`: The list of potion effects to give the player, the name of the potion effect separated from the amplifier by a space character.

### Prevent
This section controls what the player is not allowed to do, or what isn't allowed to happen to players.

- `type`: prevent
- `actions`: The prevented actions.

Actions of the prevent capability:
- `block_break`: prevents breaking blocks
- `block_place`: prevents placing blocks
- `block_change`: prevents blocks from being changed by the player, like crop trampling
- `entity_target`: prevents the player from being targeted by entities
- `damage`: prevents the player from being damaged
- `pickup`: prevents items being picked up by the player
- `hunger`: prevents hunger
- `item_drop`: prevents dropping items
- `interact`: prevents interactions with all interactables like doors, levers, etc.
- `tab_complete`: prevents the player's name from being tab-completed by players who can't see the player
- `command_use`: prevents using commands on the hidden player by players who can't see the player
- `arrow_pickup`: prevents picking up arrows

### Silent open
Silently opens a container for the player, preventing the opening of the lid, or making a sound.

- `type`: silent_open
