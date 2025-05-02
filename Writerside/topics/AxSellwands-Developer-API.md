# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxSellwands:CHANGE-THIS")
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
    <artifactId>AxSellwands</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxSellwands"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxSellwands?color=40c14a&amp;amp;name=AxSellwands" alt=""/></a></p>

> Make sure that you are NOT including the api jar in your plugin!
> <br><br>Check that the scope is set to **provided** in maven or that you use **compileOnly** on gradle!</br></br>
{style="warning"}

## API Usage

Don't forget to add AxSellwands to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxSellwands
```
or:
```yaml
softdepend:
  - AxSellwands
```

### Events:

|-|-|
| Event | Description |
| AxSellwandsSellEvent | Called when a sell wand is used to sell items |

Other: Use the static methods in the `com.artillexstudios.axsellwands.HookManager` class to register a new protection/currency/price hooks.