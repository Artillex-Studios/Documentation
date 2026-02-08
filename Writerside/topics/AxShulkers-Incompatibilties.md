# Incompatibilties
*Known incompatibilities, if you find any, let us know*

## Total incompatibilities
- **EconomyShopGui**: Shulker quick sell can be used to duplicate items (solution: set `sell-shulker-boxes` to false in the economyshopgui config.yml)
- Any Plugin that removes/adds items or modifies them inside shulkers. Their actions will be overwritten by axshulkers, which can cause items to dupe or allow players to farm money.
- Other shulker viewers (for obvious reasons)

## Minor incompatibilities
- Plugins that have a shulker view *might* get desynced and show the wrong items (note: if you find something like this and know how to replicate it, we can patch it)

> Developers of incompatible plugins can hook into AxShulkers with the [Developer API](AxShulkers-Developer-API.md) to fix these!