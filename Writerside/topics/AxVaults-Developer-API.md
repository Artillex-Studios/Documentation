# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxVaults:CHANGE-THIS")
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
    <artifactId>AxVaults</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxVaults"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxVaults?color=40c14a&amp;amp;name=AxVaults" alt=""/></a></p>

## API Usage

Don't forget to add AxVaults to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxVaults
```
or:
```yaml
softdepend:
  - AxVaults
```

Currently the plugin does not have specific API classes, however for most use cases, you should check out the `com.artillexstudios.axvaults.vaults.VaultManager` class!