# Supported Plugins

## Booster Hooks

### Builtin
```yaml
  vanilla:damage
  vanilla:flight
  vanilla:flyspeed
  vanilla:maxhealth
  vanilla:walkspeed
  vanilla:experience
  # \ the following ones require mc 1.21 or higher /
  vanilla:block_break_speed
  vanilla:mining_efficiency
  vanilla:scale
  vanilla:underwater_mining_speed
```

**Potion boosters:**

`vanilla:potion_<name>`
- all the vanilla potions work
- instead of multipliers, they are amplifiers
- for example, a potion with +200% multiplier will be a lvl 3 potion (because +0-99% is lvl 1)

### Third party
```yaml
  alonsolevels:experience
  auraskills:experience
  aureliumskills:experience
  axgens:sell_money
  axsellwands:sell_money
  battlepass:experience
  cmi:sell_money
  cyberlevels:experience # read note #1 below
  deluxesellwands:sell_money
  ecojobs:experience
  economyshopgui:sell_money
  ecoskills:experience
  ecoshop:sell_money
  jobsreborn:experience
  mcmmo:experience
  mmocore:experience
  playerpoints:point_change
  rivalharvesterhoes:essence
  rivalharvesterhoes:experience
  sellwand:sell_money
  shopguiplus:sell_money # read note #2 below
  supermobcoins:mobcoin
  tmmobcoins:mobcoin
  valhallammo:experience
  ultimatemobcoins:mobcoin
  voidchest:sell_money
  wildchests:sell_money
```
* #1 CyberLevels requires you to use [our fork](https://github.com/BenceX100/CyberLevels-with-api/releases)!
* #2 The ShopGui SellGui extension does NOT work with this booster; however, we can provide you a modified jar that will work, on our discord.

## Team Hooks
* BentoBox
* IridiumSkyBlock
* SuperiorSkyBlock
* KingdomsX
* BetterTeams

> Is there a plugin that isn't supported? Open a ticket on our discord:
<font color="#1f67ff">[dc.artillex-studios.com](https://dc.artillex-studios.com/)</font>