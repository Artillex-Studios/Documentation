# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxGraves:CHANGE-THIS")
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
    <artifactId>AxGraves</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxGraves"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxGraves?color=40c14a&amp;name=AxGraves" alt=""/></a></p>

## API Usage

### Events

|-|-|
| Event | Description |
| GraveInteractEvent | Called when a player opens/collects a grave |
| GraveOpenEvent | Called when a player opens a grave |
| GravePreSpawnEvent | Called before a grave have spawned |
| GraveSpawnEvent | Called after a grave have spawned |