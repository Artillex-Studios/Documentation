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
    <url>https://repo.artillex-studios.com/snapshots/</url>
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

As an example, I will be adding a vanilla minecraft xp booster to axboosters with the API!

First, don't forget to app AxBoosters to your plugin's plugin.yml, like this:
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
        return "AxBoostersExample"; // this will be used in the messages.yml, make sure to set it to a unique string
    }

    @Override
    public boolean isPersistent() {
        return true; // make sure that this is set to true, otherwise the hook will be unloaded on /axboosters reload
    }

    @EventHandler // use your listener here
    public void onEvent(@NotNull PlayerExpChangeEvent event) {
        double am = event.getAmount();
        event.setAmount((int) Math.round(am * BoosterUtils.getMultiplier(event.getPlayer(), getName())));
    }
}
```

Next, you will have to register the hook, like this (`this` should be the instance of your main class):
```Java
final AxBoostersExample booster = new AxBoostersExample();
// register the booster
HookManager.registerBoosterHook(this, booster);
// if you use a listener, you will have to register it
getServer().getPluginManager().registerEvents(booster, this);
```

And If this is done, make sure to add your booster to the `messages.yml` file, like this:

<code-block lang="yaml" ignore-vars="true">
  MY-BOOSTER1:
    type: AxBoostersExample # use the string that you wrote to the getName() method here
    bossbar:
      name: '&amp;f%player%&amp;#FFDD00''s &amp;#FFDD00&amp;l%multiplier%x xᴘ ʙᴏᴏsᴛᴇʀ &amp;#DDDDDD| &amp;#FFFFFF%time% seconds'
      color: yellow
      style: progress
    chat:
      start: '&amp;f%player% &amp;#00FF00has started a &amp;#FFDD00&amp;l%multiplier%x xᴘ ʙᴏᴏsᴛᴇʀ&amp;#00FF00! It ends in &amp;#FFFFFF%time% seconds&amp;#00FF00!'
      end: '&amp;#FF0000A &amp;#FFDD00&amp;l%multiplier%x xᴘ ʙᴏᴏsᴛᴇʀ &amp;#FF0000has ended!'
    # item shown in guis
    item:
      type: EXPERIENCE_BOTTLE
      name: '&amp;#FFDD00&amp;lXP BOOST'
</code-block>

That's all! Just start the server and everything should work! Activate the booster and test it:
`/axboosteradmin activate @s MY-BOOSTER1 global 2.0 10m`