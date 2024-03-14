# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxAuctionsAPI:CHANGE-THIS")
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
    <artifactId>AxAuctionsAPI</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxAuctionsAPI"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxAuctionsAPI?color=40c14a&amp;amp;name=AxAuctionsAPI" alt=""/></a></p>

## API Usage

Don't forget to add AxAuctions to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxAuctions
```
or:
```yaml
softdepend:
  - AxAuctions
```

### Adding your own currency:

Create a new class and make it implement `com.artillexstudios.axauctions.hooks.currency.CurrencyHook`, it should look something like this:

```Java
public class ExampleCurrency implements CurrencyHook {
    @Override
    public void setup() {
        
    }

    @Override
    public String getName() {
        return null;
    }

    @Override
    public boolean worksOffline() {
        return false;
    }

    @Override
    public boolean usesDouble() {
        return false;
    }

    @Override
    public boolean isPersistent() {
        return false;
    }

    @Override
    public double getBalance(@NotNull UUID player) {
        return 0;
    }

    @Override
    public void giveBalance(@NotNull UUID player, double amount) {

    }

    @Override
    public void takeBalance(@NotNull UUID player, double amount) {

    }
}
```

Next is, you will have to create a section in the `currencies.yml`, just copy paste one of the other currency's, for example like this:
```yaml
  ExampleCurrency:
    register: true
    tax: 0
    display:
      # the way the currency will be shown in the lores of the auction gui
      gui: "&f%\price% &#AAFFFFcoins"
      # used in the currency switcher and tab completion
      raw: "My Currency"
      # the item shown in the currency selector
      item:
        material: GOLD_INGOT
        name: "&#00DDFFMy Currency"
        lore:
          - " "
          - "&#00DDFF&l(!) &#00DDFFClick here to select!"
```

Create your implementation for all these methods, after that is done, you will have to register it by using the
`com.artillexstudios.axauctions.hooks.HookManager.registerCurrencyHook()` method, for the plugin parameter give the instance of your plugin's main class.

And if all of this is done, congratulations, you have added a new currency to AxAuctions!