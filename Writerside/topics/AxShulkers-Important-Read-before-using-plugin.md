# ❗ Read before using plugin

### Note
- The plugin's anti dupe puts an **UUID** (Universal Unique Identifier) on **EVERY shulker** that is opened with the shulker viewer.
- This means that if you open a shulker and share that with others (for example if you put it in a CRATE, KIT, or anywhere else) it will be the **SAME virtual inventory**!!
- You can check if your shulker has a UUID (on paper and forks) with the /paper dumpitem command while holding it.
![image_40.png](image_40.png)

### What does this mean?
- This simply means that if **players get the shulker which has the same UUID**, (and they will if you opened the shulker before giving it to people) which also means that they can **steal** each others' stuff from the shulkers, because **it is the exact same inventory**.

### What can I do to stop this from happening?
- **OPTION A)** 
  - AFTER you have finished creating the shulker for a kit, crate, or anything else, **HOLD** the shulker in your hand and run **/axshulkers clear**
  - This command removes the UUID from the shulker item, which means that it will became a sharable shulker!
  - Note: if you run this command and after that you **open the shulker preview**, you WILL have to **do it again** as a new UUID will be put on it!
- **OPTION B)**
  - Never use the shulker preview for creating shulkers that you intend to share with players!
  - Just place the shulker on the ground and modify the items there. That will cause the uuid to be removed even if it existed on the item.
- **OPTION C)**
  - Enable the experimental `auto-clear-shulkers` setting in the config.
  - This will automatically remove the UUID right after closing the shulker.
  - It relies on java weak references, so it might not be a safe option, however if you find any issues with it, we will fix it ASAP.

### Why is this needed?
- With this solution we can prevent 100% of the dupes as players can't touch or get rid of the virtual inventory, it will always be the same.

### Desync issues
- Because we use virtual inventories, the contents of a shulker box may not always be the same as in the description.
- Note that this is NOT an exploit/dupe, this is simply when the description of a shulker box doesn't match real the contents of the shulker.
- The plugin does it's best to prevent this from happening, however some external plugins might not handle this, causing to desync.
- This can be used for scamming, for example on auction houses. We suggest using AxAuctions as it has builtin AxShulkers support, which will always show the virtual inventory.
- You shouldn't have to worry about this as desync issues are quite rare and if you find anything, we can fix it.
- You can ask developers that have plugins with shulker viewers to add axshulkers support! (for devs: you can find all useful methos in the ShulkerUtils class)