# Developer API

<tabs>

<tab title="Gradle">

Add the following to your **repositories** section:
```groovy
maven { url 'https://repo.artillex-studios.com/releases/' }
```

Add the dependency to your **dependencies** section:

```groovy
compileOnly("com.artillexstudios:AxParties:CHANGE-THIS")
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
    <artifactId>AxParties</artifactId>
    <version>CHANGE-THIS</version>
    <scope>provided</scope>
</dependency>
```
</tab>
</tabs>
<p>Replace <b>CHANGE-THIS</b> to the latest version: <a href="https://repo.artillex-studios.com/#/releases/com/artillexstudios/AxParties"><img src="https://repo.artillex-studios.com/api/badge/latest/releases/com/artillexstudios/AxParties?color=40c14a&amp;amp;name=AxParties" alt=""/></a></p>

> Make sure that you are NOT including the api jar in your plugin!
> <br><br>Check that the scope is set to **provided** in maven or that you use **compileOnly** on gradle!</br></br>
{style="warning"}

## API Usage

Don't forget to add AxParties to your plugin's plugin.yml, like this:
```yaml
depend:
  - AxParties
```
or:
```yaml
softdepend:
  - AxParties
```

### Using the API:

The current API is very simple, you can access all the useful methods in the `com.artillexstudios.axparties.api.AxPartiesAPI` class.

AxPartiesAPI#getParties -

| Method               | Returns            | Explanation                                                                         |
|----------------------|--------------------|-------------------------------------------------------------------------------------|
| getParties           | Map<String, Party> | Returns an unmodifiable map of all parties (key = party name, value = party object) |
| getPartyOf(player)   | Optional<\Party>   | Returns an optional party, it will be empty if the player doesn't have a party      |
| getPartyByName(name) | Optional<\Party>   | Returns an optional party, it will be empty if the party is not found               |

### Simple example:

```java
String partyName = "test";
Optional<Party> partyOptional = AxPartiesAPI.getPartyByName(partyName);
if (partyOptional.isEmpty()) {
    System.out.println("Not found");
} else {
    Party party = partyOptional.get();
    System.out.println(party.getName());
    // party.getMembers() - get all members (as OfflinePlayer)
    // party.getOnlineMembers() - get online members (as Player)
    // party.getOfflineMembers() - get offline members (as OfflinePlayer)
}
```

And that's all, if you need anything else, feel free to [contact us](https://dc.artillex-studios.com/) or make a pull request on [github](https://github.com/Artillex-Studios/AxParties)!