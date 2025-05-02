# Developer API

**THE API HAS NOT BEEN RELEASED YET**

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxChatGamesAPI:CHANGE-THIS")
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
    <artifactId>AxChatGamesAPI</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxChatGamesAPI"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxChatGamesAPI?color=40c14a&amp;amp;name=AxChatGamesAPI" alt=""/></a></p>

> Make sure that you are NOT including the api jar in your plugin!
> <br><br>Check that the scope is set to **provided** in maven or that you use **compileOnly** on gradle!
{style="warning"}

## API Usage

Don't forget to add AxChatGames to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxChatGames
```
or:
```yaml
softdepend:
  - AxChatGames
```

### Events
* The events can be found under the `com.artillexstudios.axchatgames.api.events` package.

| Event              | Cancellable | Description                                   |
|--------------------|-------------|-----------------------------------------------|
| ChatGameStartEvent | true        | Called when a game starts.                    |
| ChatGameWinEvent   | true        | Called when a game ends **with a winner**.    |
| ChatGameEndEvent   | false       | Called when a game ends **without a winner**. |
