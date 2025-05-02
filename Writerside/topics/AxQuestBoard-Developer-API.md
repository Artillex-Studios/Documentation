# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxQuestBoardAPI:CHANGE-THIS")
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
    <artifactId>AxQuestBoardAPI</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxQuestBoardAPI"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxQuestBoardAPI?color=40c14a&amp;amp;name=AxQuestBoardAPI" alt=""/></a></p>

> Make sure that you are NOT including the api jar in your plugin!
> <br><br>Check that the scope is set to **provided** in maven or that you use **compileOnly** on gradle!</br></br>
{style="warning"}

## API Usage

Don't forget to add AxQuestBoard to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxQuestBoard
```
or:
```yaml
softdepend:
  - AxQuestBoard
```

### Events:

|-|-|
| Event | Description |
| QuestActivationEvent | Called when a new quest gets activated |
| QuestCompletionEvent | Called when a player completes a quest |

Other: Use the static method in the `com.artillexstudios.axquestboard.api.AxQuestBoardAPI` class.