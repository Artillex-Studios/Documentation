# Supported Plugins

## Booster Hooks

### Builtin
```yaml
  vanilla:damage
  vanilla:flight
  vanilla:flyspeed
  vanilla:experience
```

**Potion effect booster hooks:**

`vanilla:potion_<name>`
- all the vanilla potions work (from /effects)
- [https://minecraft.wiki/w/Potion#ID](https://minecraft.wiki/w/Potion#ID)
- instead of multipliers, they are amplifiers
- for example, a potion with +200% multiplier will be a lvl 3 potion (because +0-99% is lvl 1)
- examples: Night Vision, Jump Boost, Speed, Haste & many more

**Attribute booster hooks:**

`vanilla:attribute_<name>`
- all the attributes work (from /attribute)
- [https://minecraft.wiki/w/Attribute](https://minecraft.wiki/w/Attribute) (note that a lot of attributes are only available on 1.21)
- examples: Mining Speed, Walking Speed, Player Scale & many more
> Some attributes might not work on players! (check the wiki link above to see which ones work)

### Third party


`alonsolevels:experience`
> AlonsoLevels's api doesn't support updating the values, which means that boosters won't show the boosted value in the chat. (however players will still get the increased XP amount)

`auraskills:experience`

`aureliumskills:experience`

`axgens:sell_money`

`axsellwands:sell_money`

`battlepass:experience`

`cmi:sell_money`

`cyberlevels:experience`
> CyberLevels requires you to use [our modified version](https://github.com/BenceX100/CyberLevels-with-api/releases)!

`deluxesellwands:sell_money`

`ecojobs:experience`

`economyshopgui:sell_money`
> EconomyShopGUI's api is really messy and in some situations boosters might not boost sell prices.

`ecoskills:experience`

`ecoshop:sell_money`

`essentials:sell_money`

`jobsreborn:experience`

`jobsreborn:money`

`jobsreborn:points`

`mcmmo:experience`

`mmocore:experience`

`playerpoints:point_change`

`rivalharvesterhoes:essence`

`rivalharvesterhoes:experience`

`rivalpickaxes:essence`

`rivalpickaxes:experience`

`rivalfishingrods:essence`

`rivalfishingrods:experience`

`rivalmobswords:essence`

`rivalmobswords:experience`

`sellwand:sell_money`
> Sellwand is a generic name, this booster is made for [this](https://www.spigotmc.org/resources/sell-wand.87014/) plugin!

`shopguiplus:sell_money`
> If you use ShopGUIPlus-SellGUI, you have to use [our modified version](https://github.com/BenceX100/ShopGUIPlus-SellGUI/releases)!

`supermobcoins:mobcoin`

`tmmobcoins:mobcoin`

`valhallammo:experience`

`ultimatemobcoins:mobcoin`

`wildchests:sell_money`

`axspawners:sell_money`

`axspawners:xp_withdraw`

`axspawners:xp_generate`

## Team Hooks
* BentoBox
* IridiumSkyBlock
* SuperiorSkyBlock
* KingdomsX
* BetterTeams
* UltimateClans

> Is there another plugin that you would like support for? Open a new feature request on our
<font color="#1f67ff">[GitHub](https://github.com/Artillex-Studios/Issues)</font>

**Some plugins that we will never be able to add:** (there are some exceptions to these)
- economy plugin like vault, as they only manage the economy, not give currency to players (however, we can add other plugins, like shop plugins)
- we can't boost commands, (what could command * 1.5 look like?) time based things (like reward cooldowns)
- closed source plugins without a public API jar
- plugins that only have give/pay commands, because we can't prevent abusing boosts by paying currency to each other