# Creating a new minion

Creating a new minion type is really easy, all you have to do is create a new class that extends MinionType.

<tabs>
<tab title="Java">

```java
import com.artillexstudios.axminions.api.minions.Minion;
import com.artillexstudios.axminions.api.minions.miniontype.MinionType;
import org.bukkit.enchantments.Enchantment;
import org.bukkit.entity.Entity;
import org.bukkit.entity.Player;
import org.bukkit.plugin.java.JavaPlugin;

import java.util.Collection;

public class YourMinionType extends MinionType {

    public YourMinionType(JavaPlugin plugin) {
        super("yourminiontype", plugin.getResource("yourminiontype.yml"));
    }

    @Override
    public boolean shouldRun(Minion minion) {
        return AxMinionsAPI.getINSTANCE().getTick() % minion.getNextAction() == 0L;
    }

    @Override
    public void onToolDirty(Minion minion) {
        minion.setRange(getDouble("range", minion.getLevel()));
        double level = minion.getTool().getEnchantmentLevel(Enchantment.DIG_SPEED);
        double tool = level == 0 ? 0.1 : level / 10;
        double efficiency = 1.0 - tool > 0.9 ? 0.9 : tool;
        minion.setNextAction((int) (getLong("speed", minion.getLevel()) * efficiency));
    }

    @Override
    public void run(Minion minion) {
        Collection<Entity> entities =  minion.getLocation().getWorld().getNearbyEntities(
                minion.getLocation(),
                minion.getRange(),
                minion.getRange(),
                minion.getRange()
        );

        for (Entity entity : entities) {
            if (!(entity instanceof Player player)) return;

            player.sendMessage("I like cats!");
        }
    }
}
```
</tab>
<tab title="Kotlin">

```kotlin
import com.artillexstudios.axminions.api.minions.Minion
import com.artillexstudios.axminions.api.minions.miniontype.MinionType
import kotlin.math.roundToInt
import org.bukkit.enchantments.Enchantment
import org.bukkit.entity.Player
import org.bukkit.plugin.java.JavaPlugin

class YourMinionType(plugin: JavaPlugin) : MinionType("yourminiontype", plugin.getResource("yourminiontype.yml")!!) {

    override fun shouldRun(minion: Minion): Boolean {
        return AxMinionsAPI.INSTANCE.getTick() % minion.getNextAction() == 0L
    }

    override fun onToolDirty(minion: Minion) {
        minion.setRange(getDouble("range", minion.getLevel()))
        val tool = minion.getTool()?.getEnchantmentLevel(Enchantment.DIG_SPEED)?.div(10.0) ?: 0.1
        val efficiency = 1.0 - if (tool > 0.9) 0.9 else tool
        minion.setNextAction((getLong("speed", minion.getLevel()) * efficiency).roundToInt())
    }

    override fun run(minion: Minion) {
        val entities = minion.getLocation().world?.getNearbyEntities(
            minion.getLocation(),
            minion.getRange(),
            minion.getRange(),
            minion.getRange()
        ) ?: return

        for (entity in entities) {
            if (entity !is Player) continue;

            entity.sendMessage("I like cats!")
        }
    }
}
```
</tab>
</tabs>

## Registering

After you have your shiny new MinionType, you have to register it. 

<tabs>
<tab title="Java">

```java
MinionType type = new YourMinionType();

// Sadly, we have to do this, because other minions have already been loaded in the loaded worlds.
// After registration however, the plugin will load minions for the worlds loaded afterwards. 
for (World world : Bukkit.getWorlds()) {
    AxMinionsAPI.getINSTANCE().getDataHandler().loadMinionsForWorld(type, world);
}

MinionTypes.register(type);
```
</tab>
<tab title="Kotlin">

```kotlin
val type = YourMinionType()

// Sadly, we have to do this, because other minions have already been loaded in the loaded worlds.
// After registration however, the plugin will load minions for the worlds loaded afterwards. 
for (world in Bukkit.getWorlds()) {
    AxMinionsAPI.INSTANCE.getDataHandler().loadMinionsForWorld(type, world);
}

MinionTypes.register(type);
```
</tab>
</tabs>
