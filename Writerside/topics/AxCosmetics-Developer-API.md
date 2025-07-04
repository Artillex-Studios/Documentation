# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios.axcosmetics:axcosmetics:CHANGE-THIS:all")
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
    <groupId>com.artillexstudios.axcosmetics</groupId>
    <artifactId>axcosmetics</artifactId>
    <version>CHANGE-THIS</version>
    <classifier>all</classifier>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/axcosmetics/axcosmetics"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/axcosmetics/axcosmetics?color=40c14a&amp;amp;name=AxAuctionsAPI" alt=""/></a></p>

> Make sure that you are NOT including the api jar in your plugin!
> <br><br>Check that the scope is set to **provided** in maven or that you use **compileOnly** on gradle!</br></br>
{style="warning"}

## API Usage

Don't forget to add AxCosmetics to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxCosmetics
```
or:
```yaml
softdepend:
  - AxCosmetics
```

## Registering a CosmeticSlot

CosmeticSlots are useful for allowing users to have cosmetics in different places.
Registering a new slot is pretty simple!

You can register new slots in your onLoad.
```java

@Override
public void onLoad() {
    CosmeticSlot slot = new CosmeticSlot("YOUR_SLOT");
    AxCosmeticsAPI.instance().cosmeticSlots().register(slot);   
}

```

## Working with Users

Users are our representation of a cosmetic holder.

If you want to get a user for a player who is currently online on the server:
```java
public void yourMethod(Player player) {
    User user = AxCosmeticsAPI.instance().getUserIfLoadedImmediately(player);
}

```

If you want to work with players who might not be online at the time:
```java
public void yourMethod(Player player) {
    AxCosmeticsAPI.instance().getUser(player).thenAccept(user -> {
        // Do something with the user
    });
}   

```

## Creating your own cosmetic types

Before creating your cosmetic type, you need to create a CosmeticConfig for your type.
```java
public final class YourCosmeticConfig extends CosmeticConfig {
    private final int yourValue;
    
    public YourCosmeticConfig(String name, Map<String, Object> config) {
        super(name, config);
        // This gets an option, and throws if the option is not present
        this.yourValue = this.getInt("your-option"); 
    }

    // This is so we know what item to use for the gui
    @Override
    public WrappedItemStack guiItem(CosmeticData data) {
        return new ItemBuilder((Map<Object, Object>) this.getMap("item-stack"),
                Placeholder.unparsed("edition", String.valueOf(data.counter())),
                Formatter.date("date", ZonedDateTime.ofInstant(Instant.ofEpochMilli(data.timeStamp()), ZoneId.systemDefault()))
        ).wrapped();
    }

    // Your methods
}

```

Now, you can create your Cosmetic type!

```java
public final class YourCosmetic extends Cosmetic<YourCosmeticConfig>  {

    public YourCosmetic(User user, CosmeticData data, YourCosmeticConfig config) {
        super(user, data, config);
    }

    @Override
    public void spawn() {
        // Something you want to do when the cosmetic is equipped
    }

    @Override
    public void update() {
        // Something you do when the cosmetic is ticked
    }

    @Override
    public void despawn() {
        // Something you want to do when the cosmetic is unequipped
    }
    
    // The valid cosmetic slots for the cosmetic
    @Override
    public Collection<CosmeticSlot> validSlots() {
        return List.of(CosmeticSlots.YOUR_SLOT);
    }
}

```

After creating your cosmetic config and type, you need to register them. These should be loaded in the onLoad part of your plugin, so that
they can be loaded by our configloader.

```java
@Override
public void onLoad() {
    AxCosmeticsAPI.instance().cosmeticConfigTypes().register("your-type", YourCosmeticConfig::new);
    AxCosmeticsAPI.instance().cosmeticTypes().register("your-type", YourCosmetic::new);
}

```

After this, you're all set, and your custom cosmetic type is registered!