# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxShulkers:CHANGE-THIS")
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
    <artifactId>AxShulkers</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxShulkers"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxShulkers?color=40c14a&amp;amp;name=AxShulkers" alt=""/></a></p>

## API Usage

Don't forget to add AxShulkers to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxShulkers
```
or:
```yaml
softdepend:
  - AxShulkers
```

The plugin does not have a special API, however everything important can be found in the `com.artillexstudios.axshulkers.utils.ShulkerUtils`, use the static methods to get contents of a shulker!