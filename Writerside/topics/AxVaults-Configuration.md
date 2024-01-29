# Configuration

### auto-save-minutes (default: 5)

* How often should vaults be saved to the database?
* This is useful if you have a lot of crashes,
* It is recommended to set it to the same value as the world save time!

### vault-selector-rows (default: 6)

* How many rows should the /axvault selector menu have?

### vault-storage-rows (default: 6)

* How many rows should vaults have?

### database (default: h2)

* You should not change is, unless you really want to use SQLite.
* H2 is faster, SQLite may be more stable, however usually it does not matter.

### permission-mode (default: 0)

* 0 - Every vault needs a separate permission (axvaults.vault.10 will only give access to vault #10)
* 1 - The highest permission will give all the previous vaults (axvaults.vault.10 will give access to vaults #1-#10)

### show-locked-vaults (default: true)

* Should locked vaults be shown in the gui?
* This could be useful if you randomly give many vaults.

### blacklisted-items

* Items that match will be removed when the player dies from the grave
* You can also define a material and a name-contains subsection