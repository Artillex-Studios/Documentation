# Converters

- Converters can be used to move from another plugin to AxVaults
- Vaults and their contents are converted, make sure that you change the permissions from the old plugin to [axvaults' permissions](AxVaults-Permissions.md)! (also make sure to set the `vault-storage-rows` setting to the same value before converting) 

### How to use?

1. Make sure to have both the plugin that you are converting from and AxVaults running on the server.
2. Run `/axvaultsadmin converter &lt;plugin>` (Use the tab completer for the &lt;plugin> part!)
3. The converter should have done its job, make sure to check the console for any errors!
4. If there are no errors, remove the other plugin and enjoy AxVaults!

### Supported Plugins:
- PlayerVaultsX

> Is there another plugin that you would like support for? Open a new feature request on our
<font color="#1f67ff">[GitHub](https://github.com/Artillex-Studios/Issues)</font>