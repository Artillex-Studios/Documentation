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

> It is highly recommended that you register hooks right when the server starts to prevent possible errors.
{style="warning"}

Create a new class and make it implement `com.artillexstudios.axauctions.hooks.currency.CurrencyHook`, it should look something like this:

```Java
public class ExampleCurrency implements CurrencyHook {
    @Override
    public void setup() {
        // this only gets called once when the hook gets registered
    }

    @Override
    public String getName() {
        // the name of your hook, make sure to use this in the currencies.yml
        return "ExampleCurrency";
    }

    @Override
    public boolean worksOffline() {
        // does your hook work with offline players?
        return false;
    }

    @Override
    public boolean usesDouble() {
        // does your hook work uses double/float or not?
        return false;
    }

    @Override
    public boolean isPersistent() {
        // should the plugin unregister the hook when it gets reloaded?
        // you should keep this on true
        return true;
    }

    @Override
    public double getBalance(@NotNull UUID player) {
        // your code here
        return 0;
    }

    @Override
    public void giveBalance(@NotNull UUID player, double amount) {
        // your code here
    }

    @Override
    public void takeBalance(Consumer<Boolean> successful, @NotNull UUID player, double amount) {
        // your code here
        // the Consumer is meant to be used for async plugins, for example if your async sql query fails, return false to prevent giving the item
        successful.accept(true); // it is VERY IMPORTANT to accept the consumer if everything worked!!!
    }
}
```

> Double-check, that in the **takeBalance** method you always accept the consumer (`successful.accept()`)
{style="warning"}

Next is, you will have to create a section in the `currencies.yml`, copy paste one of the other currencies, for example, like this:
```yaml
  ExampleCurrency: # < the name of your currency
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