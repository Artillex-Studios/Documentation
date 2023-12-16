# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxInventoryRestore:CHANGE-THIS")
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
    <artifactId>AxInventoryRestore</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxInventoryRestore"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxInventoryRestore?color=40c14a&amp;name=AxInventoryRestore" alt=""/></a></p>

## API Usage

### Events

|-|-|
| Event | Description |
| InventoryBackupEvent | Called when a backup is made |
| InventoryRestoreEvent | Called before a backup is restored |