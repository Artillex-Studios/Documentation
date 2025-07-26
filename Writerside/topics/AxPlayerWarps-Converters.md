# Converters

- Converters can be used to move from another plugin to AxPlayerWarps
- Please note that we only convert the most important warp data (warp name, location, description), we don't migrate the config files.

### How to use?

1. Make sure to have the plugin that you are converting from **running on the server**. (Not all the converters require it, read the table at the bottom of the page)
2. Run `/axpwadmin converter &lt;plugin>` (Use the tab completer for the &lt;plugin> part!)
3. The converter should have done its job, make sure to check the console for any errors!
4. If there are no errors, remove the other plugin and enjoy axplayerwarps!

### Supported Plugins:

| Plugin      | Converter | Requires Plugin |
|-------------|-----------|-----------------|
| PlayerWarps | SQLite    | no              |
* Plugin - name of the plugin
* Converter - we can only convert if you use this database type in the plugin you are converting from (the default db is always supported)
* Requires Plugin - do you need to have the plugin running on the server when you run the converter?

> Is there another plugin that you would like to have a converter for? Open a ticket on our discord:
<font color="#1f67ff">[dc.artillex-studios.com](https://dc.artillex-studios.com/)</font>