# Configuration

## config.yml

### cleanup-after-days (default: 14)

* How old does a backup needs to be to get cleaned?
* A cleanup happens when the server stops or starts and also can be triggered with `/axir cleanup`

### enable-all-category (default: true)

* Should there be a category where you can find ALL the backups of a player?

### automatic-backup.enabled (default: true)

* Should there be a backup created once in a while?

### automatic-backup.seconds (default: 180)

* How often should a backup be made if `automatic-backup.enabled` is true?

### menu-rows

* You can customize the row amount of the guis
* This can be a value between 2 and 6
* main-menu - First menu that appears when using /axir view &lt;name\>
* backup-selector - Second menu, appears after selecting a category

### compact-database (default: true)

* If your server often doesn't stop randomly and axir spams stuff, try disabling this
* Runs the databases builtin cleanup mechanism to decrease disk size
* If you have 100K+ backups or a lot of storage, you can disable this as this could slow down the server shutdown process

### enabled-backups

* You can disable categories by setting them to false
* This is useful if your server type doesn't require on of these events

### enable-discord-addon (default: false)

* More info: [Discord Addon](AxInventoryRestore-Discord-Addon.md)