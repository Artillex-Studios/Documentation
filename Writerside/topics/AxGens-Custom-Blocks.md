# Custom Blocks

You can use textured blocks instead of vanilla minecraft blocks, note that this requires external plugins (Nexo, Oraxen or ItemsAdder) as of right now!

<tabs>

<tab title="Nexo">

<b>Adding Nexo custom blocks:</b>
* Go to the plugins/AxGens/tiers.yml file and find the tier that you want to edit
<br></br>

Example tier configuration:

```yaml
tiers:
  '1':
    generator-item:
      material: HAY_BLOCK # material is only used for the item
      # add this section \/
      custom-block-id: my_block # change the amethyst_block to your own custom block
      custom-model-data: 1000 # you may also want to add a custom-model-data, but it is not required
```

> The following parts of this documentation might not be accurate!
{style='warning'}

<br></br>
<b>Where can I get the name of the custom block from?</b>
* go to `plugins/Nexo/items/blocks.yml`

This is how the block I am using looks like: (this is from the default config of oraxen, you can use your own)
```yaml
my_block: # <<< THIS IS THE custom-block-id THAT YOU NEED
  itemname: "My block"
  material: DIAMOND
  Pack:
    parent_model: "block/cube_all"
    textures:
      - my_block_texture.png
  Mechanics:
    custom_block:
      type: NOTEBLOCK
      custom_variation: 2
      model: my_block
      hardness: 20 # this makes it really hard to mine
      drop:
        silktouch: false
        minimal_type: STONE
        best_tool: PICKAXE
        loots:
          - { nexo_item: caveblock, probability: 1.0 }
```

</tab>

<tab title="Oraxen">

<b>Adding Oraxen custom blocks:</b>
* Go to the plugins/AxGens/tiers.yml file and find the tier that you want to edit
<br></br>

Example tier configuration:

```yaml
tiers:
  '1':
    generator-item:
      material: HAY_BLOCK # material is only used for the item
      # add this section \/
      custom-block-id: amethyst_block # change the amethyst_block to your own custom block
      custom-model-data: 1000 # you may also want to add a custom-model-data, but it is not required
```

<br></br>
<b>Where can I get the name of the custom block from?</b>
* go to `plugins/Oraxen/items/blocks.yml`

This is how the block I am using looks like: (this is from the default config of oraxen, you can use your own)
```yaml
amethyst_ore: # <<< THIS IS THE custom-block-id THAT YOU NEED
  displayname: <gradient:#4B36B1:#6699FF>Amethyst Ore
  material: PAPER
  Pack:
    generate_model: true
    parent_model: block/cube_all
    textures:
    - default/amethyst_ore
    custom_model_data: 1001 # <<< YOU CAN ALSO USE THIS 
  Mechanics:
    noteblock:
      block_sounds:
        break_sound: block.stone.break
        place_sound: block.stone.place
      custom_variation: 1
      model: amethyst_ore
      hardness: 6
      drop:
        silktouch: true
        fortune: true
        minimal_type: IRON
        best_tools:
        - PICKAXE
        loots:
        - oraxen_item: amethyst
          probability: 1.0
```

</tab>

<tab title="ItemsAdder">

<b>Adding ItemsAdder custom blocks:</b>
* Go to the plugins/AxGens/tiers.yml file and find the tier that you want to edit
<br></br>

Example tier configuration:

```yaml
tiers:
  '1':
    generator-item:
      material: HAY_BLOCK # material is only used for the item
      # add this section \/
      custom-block-id: "iasurvival:dark_amethyst_block" # change this to your own custom block
      custom-model-data: 1000 # you may also want to add a custom-model-data, but it is not required
```

<br></br>
<b>Where can I get the name of the custom block from?</b>
* go to your own custom block's file, this is the one I used: `plugins/ItemsAdder/contents/iasurvival/configs/blocks/items/minerals/amethyst_block.yml`

This is how the block I am using looks like: (this is from the default config of itemsadder, you can use your own)
```yaml
info:
  namespace: iasurvival # <<< THIS IS THE FIRST PART
items:
  dark_amethyst_block: # <<< THIS IS THE SECOND PART, SO THE FINAL ID IS: iasurvival:dark_amethyst_block
    enabled: true
    display_name: display-name-dark_amethyst_block
    permission: iasurvival.minerals.dark_amethyst_block
    resource:
      material: PAPER
      generate: true
      textures:
        - block/minerals/dark_amethyst_block
    specific_properties:
      block:
        placed_model:
          type: REAL_NOTE # <<< SOME TYPES MAY NOT WORK, USE REAL_NOTE, THAT 100% WORKS
          break_particles_material: PURPLE_CONCRETE
        break_tools_whitelist:
          - PICKAXE
          - pickaxe
```

</tab>
</tabs>