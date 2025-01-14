# Input Types

- In the plugin currently there are 3 available input types: SIGN, ANVIL, CHAT
- Input types are used to request some information from the player, for example when renaming a warp.
- They can be customized in the input.yml file!

### Sign
![image_74.png](image_74.png)

- The sign input requires you to write your input in the **first line** of the sign

**Configuration format:**
```yaml
sign:
  - " "
  - "---------------"
  - "This is"
  - "a sign input!"
```

### Anvil
![image_75.png](image_75.png)

- The anvil input requires the player to write their input in the rename menu and they need to click the renamed item to accept.

**Configuration format:**
```yaml
anvil:
  title: '&0Anvil Input'
  item:
    material: PAPER
    glow: true
    name: '&fINPUT HERE'
    lore:
      - "&#33EEBB↑ input"
```

### Chat
![image_76.png](image_76.png)

- The chat input requires the user to open the chat and write their input in the chat and send it.

**Configuration format:**
```yaml
chat:
  - '&#33EEBBWrite your input in the chat: &#DDDDDD(write &#33EEBBcancel to stop)'
```