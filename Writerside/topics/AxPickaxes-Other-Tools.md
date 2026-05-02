# Other Tools

**The list of tool plugins that work best together:**
- [AxHoes](AxHoes.md)
- [AxPickaxes](AxPickaxes.md)

**How to synchronize currencies and xp between plugins?**
1. Pick one of the plugins that will be the primary source and storage for xp and essence. For example we will use AxHoes here. So the setup is going to be like this:
```
AxHoes [primary, provides essence and player xp]
AxPickaxes [secondary, uses AxHoes provided essence and player xp]
```
2. Go to all of the other tool plugins and open the hooks.yml.
3. Change the `essence-plugin` and `player-xp-plugin` to the name of your primary tool plugin. For example:
```yaml
essence-plugin:
  plugin: axhoes
  currency: ''

player-xp-plugin: axhoes
```
> Make sure that you keep these values on `builtin` for your primary tool plugin. (So for this example that plugin is axhoes)
4. After this, reload the plugins and they should start using your /axhoes essence and player xp instead of the plugin's builtin currencies.
5. **(Optional)** Disable the /essence and /level commands in your non-primary plugins, so they won't override the primary commands. You can do this by setting the `essence-commands` and `player-xp-commands` to an empty block. For example:
```yaml
essence-commands: []

player-xp-commands: []
```
6. Restart the server to apply changes.