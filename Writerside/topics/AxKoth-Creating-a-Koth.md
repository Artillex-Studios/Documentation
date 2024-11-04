# Creating a Koth

- The process is very simple! You don't need any plugin other than AxKoth!
- Firstly, get a wand with the `/axkoth wand` command.
- Next, hold the wand in your hand and left and right click on the 2 corners that you want to select the area for the koth zone.
- If you did is correctly, particles should outline the selection
- One you are happy with the selection, finish the setup with the `/axkoth create <name> <capture/score>` command! Note: replace `<name>` with the name you want. Also you must choose the koth type, for more info about types, check [_this page_](AxKoth-Types.md) out!

![image_51.png](image_51.png)

- Now that this is done, you can edit settings within the `/axkoth editor <name>` gui!
- Note that some settings can not be found in the gui editor, you don't forget to check the settings in these files:
  - `plugins/AxKoth/koths/<name>.yml`
  - `plugins/AxKoth/config.yml`
  - `plugins/AxKoth/messages.yml`
  - `plugins/AxKoth/schedulers.yml`