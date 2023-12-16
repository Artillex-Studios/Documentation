# Configuration

## config.yml

### cleanup-after-days (default: 14)

* How old does a backup needs to be to get cleaned?
* A cleanup happens when the server stops or starts and also can be triggered with `/axir cleanup`

### enable-all-category (default: true)

* Should there be a category where you can find ALL the backups of a player?

### automatic-backup.enabled (default: true)

* Should there be a backup created once in a while?

### automatic-backup.minutes (default: 5)

* How often should a backup be made if `automatic-backup.enabled` is true?