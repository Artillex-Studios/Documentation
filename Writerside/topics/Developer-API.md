# Developer API

Use the API in your project:

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://jitpack.io' }
```

Add the dependency to your **dependencies** section:


**Replace Tag** with the latest version from **[Jitpack](https://jitpack.io/#Artillex-Studios/AxMinions/)**
```groovy
compileOnly("com.github.Artillex-Studios:AxMinions:Tag")
```

</tab>

<tab title="Maven">

Add the following to your **repositories** section:
```xml
<repository>
    <id>jitpack.io</id>
    <url>https://jitpack.io</url>
</repository>
```

Add the following to your **dependencies** section:


**Replace Tag** with the latest version from **[Jitpack](https://jitpack.io/#Artillex-Studios/AxMinions/)**
```xml
<dependency>
<groupId>com.github.Artillex-Studios</groupId>
<artifactId>AxMinions</artifactId>
<version>Tag</version>
</dependency>
```
</tab>
</tabs>