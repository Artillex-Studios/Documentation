# Configuration

### month (default: "DECEMBER")

* Which month the calendar should work in?
* [List of months](https://docs.oracle.com/javase/8/docs/api/java/time/Month.html)

### timezone (default: "")

* Set to "" to use the server default
* [List of timezones](https://docs.oracle.com/middleware/1221/wcs/tag-ref/MISC/TimeZones.html)

### allow-late-claiming (default: true)

* Should players be able to claim their older presents?

### max-accounts-per-ip (default: 3)

* How many accounts from one ip can claim a day's present?

### command-aliases

* You can add or edit the command aliases here
* The first element of the list will be used as the "main" command

### claim-requirements

* Should the player need these to claim presents?
* Set to [] to disable
* Currently there are 2 types of requirements:
  * `[PLAYTIME] 10`
  * `[PERMISSION] permission.name`