# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxKothAPI:CHANGE-THIS")
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
    <artifactId>AxKothAPI</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxKothAPI"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxKothAPI?color=40c14a&amp;amp;name=AxKothAPI" alt=""/></a></p>

> Make sure that you are NOT including the api jar in your plugin!
> <br><br>Check that the scope is set to **provided** in maven or that you use **compileOnly** on gradle!
{style="warning"}

## API Usage

Don't forget to add AxKoth to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxKoth
```
or:
```yaml
softdepend:
  - AxKoth
```

### Events:

|-|-|
| Event | Description |
| AxKothCapturedEvent | Called when a player captures the koth |
| AxKothCaptureEndEvent | Called when a player gets knocked out of a koth |
| AxKothCaptureStartEvent | Called when a player starts capturing a koth |
| AxKothGainScoreEvent | Called after a player is in the zone for a second |
| AxKothStartEvent | Called when a koth starts |
| AxKothStopEvent | Called when a koth gets stopped or runs out of time |