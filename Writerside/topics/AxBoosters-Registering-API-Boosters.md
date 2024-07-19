# Registering API Boosters

## What is an API Booster?
- API Boosters are meant to be used for long-term boosters that are related to something in your plugin.
- For example, we can use it in our AxKoth plugin to give boosters to the capturing player and their team while they are capturing a koth.
- It takes in existing booster configurations, this is not the place for registering new booster types, you can only use existing ones here.

## How to register one?

### Some information
- Use the `com.artillexstudios.axboosters.api.boosters.APIBoosterManager` class.
- The APIBoosterManager#register method is used to create a new API booster, it takes in your plugins intance and an APIBooster object
- The APIBooster object requires you to set a BoosterType, Audience, a multiplier and optionally an owner uuid.
- You should store the APIBooster object in ram, because API Boosters don't expire (except when the server restarts)
- Use the APIBoosterManager#unregister method to remove your registered boosters.

### Getting the BoosterType object
- First of all, this is intended to be something that the user can input, for example add it to your hook configuration, so players can set which Booster Type to use.
- Booster Types can be found in the AxBoosters/boosters folder, users can create any amount of them.
- You can get an object by using its name with the **AxBoostersAPI#getBoosterType** method.
- Alternatively you can also get the list of all the enabled Booster Types from the BoosterTypes class.

### Example

```Java
public class APIBoosterExample {
    private APIBooster booster;
    private Plugin instance;

    public APIBoosterExample(Plugin instance, Player player) {
        this.instance = instance;

        // get the BoosterType object, this is recommended to be a user inputted value
        BoosterType boosterType = AxBoostersAPI.getBoosterType(CONFIG.getString("some-user-inputted-booster-type"));
        if (boosterType == null) {
            // can't find booster, make sure to notify the user about a configuration mistake
            return;
        }
        this.booster = new APIBooster(player.getUniqueId(), boosterType, Audience.PERSONAL, 150); // +150% booster

        // make sure to register it
        APIBoosterManager.register(instance, booster);
    }

    public void unregister() {
        // unregister it if you no longer need it
        APIBoosterManager.unregister(instance);
    }
}
```