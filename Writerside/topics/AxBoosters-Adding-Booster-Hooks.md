# Adding Booster Hooks

## What is a booster hook?
- It is the base of all boosters, this is what you can add to a booster configuration file (also known as Booster Type)
- More information: **[Explanation of Some Words](AxBoosters-Explanation-of-some-words.md)**

## How to add your own booster hook?

Next, you will have to create a class that implements `com.artillexstudios.axboosters.hooks.booster.BoosterHook`.

I will also implement the Listener class, because we want to boost XP gained.
```Java
public class AxBoostersExample implements Listener, BoosterHook {

    @Override
    public Key getKey() {
        return Key.key("myplugin", "experience");
    }

    @Override
    public Material getIcon() {
        return Material.EXPERIENCE_BOTTLE;
    }

    // you should set persistent to true, otherwise AxBoosters will unregister it after a reload
    @Override
    public boolean isPersistent() {
        return true;
    }

    @EventHandler
    public void onEvent(@NotNull PlayerExpChangeEvent event) {
        int original = event.getAmount();
        Player player = event.getPlayer();

        User user = UserList.getUser(player);
        if (user == null) {
            return;
        }

        float boost = user.getBoost(this);
        if (boost == 1.0f) {
            return;
        }

        // this is the important part, make sure to use the BoosterManager#multiply method
        int boosted = BoosterManager.multiply(boost, original);
        if (boosted == original) return;

        event.setAmount(boosted);
    }

    // OPTIONAL: you can also use the apply, unapply instead of using a listener
    // this is not required, and we could remove this if we are making a booster with a listener
    @Override
    public void apply(User user) {
    }

    @Override
    public void unapply(User user) {
    }
}
```

Next, you will have to register the hook! (`instance` should be your main class' instance)
You can only load booster hooks right when the plugin is being loaded, so make sure to listen to the AxBoostersLoadEvent event.
```Java
public class AxBoostersHook implements Listener {

    @EventHandler
    public void onLoad(AxBoostersLoadEvent event) {
        final AxBoostersExample booster = new AxBoostersExample();
        // register the booster
        AxBoostersAPI.registerBoosterHook(instance, booster);
        // if you use a listener, you will have to register it
        getServer().getPluginManager().registerEvents(booster, instance);
    }
}
```

Make sure to register the listener, you should set up the listener in your onEnable() method, so it works right when your plugin loads, this is very important!
```Java
    @Override
    public void onEnable() { // it also might be a good idea to make sure that axboosters is loaded
        getServer().getPluginManager().registerEvents(new AxBoostersHook(), this);
    }
```

And If this is done, restart the server and you can use the booster, using the name specified:

<code-block lang="yaml" ignore-vars="true">
boosted:
- myplugin:experience
</code-block>

You can also customize some other stuff in the `plugins/AxBoosters/hooks.yml` file, your hook should be automatically added if it was registered successfully.

That's all! Just start the server and everything should work! Activate the booster and test it:
`/axboosteradmin activateserver <BOOSTER TYPE> 100 10m`
(this command starts +100% global server booster for 10 minutes, you can use other commands)