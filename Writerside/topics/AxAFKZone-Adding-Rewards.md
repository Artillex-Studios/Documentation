# Adding Rewards

### Steps of adding a new reward:
- Navigate to the configuration file of the zone that you want to edit the rewards of. The location of the file is: `plugins/AxAFKZone/zones/name-of-zone.yml`
- Open the file and find the rewards section
- For the rewards, we use a YAML list, it might be confusing at first, but it is acutally quite simple.

```yaml
rewards:
  - chance: 50.0
    display: "&#AAAAAA1x Iron Ingot"
    commands:
      - "give %\player% iron_ingot 1"
  - chance: 25.0
    display: "&#88FFFF1x Diamond"
    items:
      - amount: 1
        material: diamond
```

- The rewards section has different elements, all the elements start with a "-" and all the indented text are part of that section.
- To add a new command reward, you want to add this to the rewards section:
```yaml
  - chance: 50.0
    display: "&#AAAAAA1x Iron Ingot"
    commands:
      - "give %\player% iron_ingot 1"
```
- Of course, you can customize it, there is a chance, display name and commands section.
- Also note that you can add multiple commands if you want, because that is another list within a list! Here is a multi command example:
```yaml
  - chance: 15.5
    display: "&71 stone and a hello message"
    commands:
      - "give %\player% stone 1"
      - "say %\player% hello"
```
- It is important through, that this is a SINGLE reward, all of these commands will be run at once, you will need to add multiple rewards if you want to do these seperately, for example:
```yaml
  - chance: 30.0
    display: "&71 stone"
    commands:
      - "give %\player% stone 1"
  - chance: 30.0
    display: "&7hello message"
    commands:
      - "say %\player% hello"
```
- Next, let's add an item reward, it is pretty much the same process, except that items can use our [Item Builder](Item-Builder.md)
```yaml
  - chance: 25.0
    display: "&#88FFFF1x Diamond"
    items:
      - amount: 1
        material: diamond
```
- The only 2 required fields are material and amount, you can add anything else from our itembuilder, for example even complex items like:
```yaml
  - chance: 25.0
    display: "&#88FFFF1x Diamond"
    items:
      - amount: 1
        material: diamond_sword
        custom-model-data: 1000
        name: "&#FF0000A really cool sword"
        lore:
          - "&#DDDDDDNot sure what"
          - "&#DDDDDDto write here!"
        enchants:
          - protection:4
          - unbreaking:3
```
- So lets combine these examples and add them to the rewards section:
```yaml
rewards:
  - chance: 15.5
    display: "&71 stone and a hello message"
    commands:
      - "give %\player% stone 1"
      - "say %\player% hello"
  - chance: 25.0
    display: "&#88FFFF1x Diamond"
    items:
      - amount: 1
        material: diamond_sword
        custom-model-data: 1000
        name: "&#FF0000A really cool sword"
        lore:
          - "&#DDDDDDNot sure what"
          - "&#DDDDDDto write here!"
        enchants:
          - protection:4
          - unbreaking:3
```