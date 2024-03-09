# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxBoostersAPI:CHANGE-THIS")
```
</tab>

<tab title="Maven">

Add the following to your **repositories** section:
```xml
<repository>
    <id>Artillex-Studios</id>
    <url>https://repo.artillex-studios.com/releases/</url>
</repository>
```

Add the following to your **dependencies** section:

```xml
<dependency>
    <groupId>com.artillexstudios</groupId>
    <artifactId>AxBoostersAPI</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxBoostersAPI"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxBoostersAPI?color=40c14a&amp;amp;name=AxBoostersAPI" alt=""/></a></p>

## API Usage

As an example, I will be adding a vanilla minecraft xp booster to AxBoosters with the API!

First, don't forget to add AxBoosters to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxBoosters
```
or:
```yaml
softdepend:
  - AxBoosters
```

Next, you will have to create a class that implements `com.artillexstudios.axboosters.hooks.booster.BoosterHook`.

I will also implement the Listener class, because I want to boost XP gained.
```Java
public class AxBoostersExample implements Listener, BoosterHook {

    @Override
    public String getName() {
        return "axboosters:example"; // you can set this to anything, but the current format is pluginname:booster
    }

    @Override
    public boolean isPersistent() {
        return true; // make sure that this is set to true, otherwise the hook will be unloaded on /axboosters reload
    }

    @EventHandler // use your listener here
    public void onEvent(@NotNull PlayerExpChangeEvent event) {
        double am = event.getAmount();
        event.setAmount((int) Math.round(am * BoosterUtils.getMultiplier(event.getPlayer(), this)));
    }
}
```

Next, you will have to register the hook: (`this` should be the instance of your main class):
```Java
final AxBoostersExample booster = new AxBoostersExample();
// register the booster
HookManager.registerBoosterHook(this, booster);
// if you use a listener, you will have to register it
getServer().getPluginManager().registerEvents(booster, this);
```

And If this is done, you can use the booster, using the name specified:

<code-block lang="yaml" ignore-vars="true">
boosted:
- axboosters:example
</code-block>

That's all! Just start the server and everything should work! Activate the booster and test it:
`/axboosteradmin activate @s <BOOSTER-FILE-NAME-HERE> global 2.0 10m`