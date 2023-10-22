# Basic usage

## Get all minions

<tabs>
<tab title="Java">

```java
List<Minion> minions = AxMinionsAPI.getINSTANCE().getMinions();

for (Minion minion : minions) {
    // Do something with the minions
}

```

> The list returned by the `getMinions()` method is an IMMUTABLE copy of the minions.
> Getting the minions creates a new list every time, so it is advised against using it repeatedly.
{style="warning"}
</tab>
<tab title="Kotlin">

```kotlin
val minions = AxMinionsAPI.INSTANCE.getMinions()

minions.forEach { minion ->
    // Do something with the minions
}
```

> The list returned by the `getMinions()` method is an IMMUTABLE copy of the minions.
> Getting the minions creates a new list every time, so it is advised against using it repeatedly.
{style="warning"}
</tab>
</tabs>

## Get blocks around a location in a sphere

<tabs>
<tab title="Java">

```java
LocationUtils.getAllBlocksInRadius(location, range, false).forEach(location -> {
    // Do something with the location
});

```
</tab>
<tab title="Kotlin">

```kotlin
LocationUtils.getAllBlocksInRadius(location, range, false).forEach { location -> 
    // Do something with the location
};
```
</tab>
</tabs>