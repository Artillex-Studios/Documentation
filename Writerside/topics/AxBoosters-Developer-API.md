# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxBoostersAPI:CHANGE-THIS")
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
    <artifactId>AxBoostersAPI</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxBoostersAPI"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxBoostersAPI?color=40c14a&amp;amp;name=AxBoostersAPI" alt=""/></a></p>

> Make sure that you are NOT including the api jar in your plugin!
> <br><br>Check that the scope is set to **provided** in maven or that you use **compileOnly** on gradle!
{style="warning"}

## API Usage

As an example, I will be adding a vanilla minecraft xp booster to AxBoosters with the API!

First, don't forget to add AxBoosters to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxBoosters
```
or:
```yaml
softdepend:
  - AxBoosters
```