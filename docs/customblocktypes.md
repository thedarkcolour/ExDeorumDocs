# Custom Block Types
As of Ex Deorum 1.25, modpack creators can now define custom types of Sieves, Barrels, and Crucibles. One reason a modpack author might want to do this is to add support for uncommon wood types that Ex Deorum does not have builtin support for.    
Note that even though you can add new variants of Ex Deorum blocks with these configuration files all Ex Deorum does is register the block and item to the game. You will still
need to use a resource pack to supply models and textures, and a datapack for recipes, loot tables, and the necessary tags.     
<hr>
## Custom Barrel
To register a new type of barrel, add a JSON file to the `.minecraft/config/exdeorum/barrel_materials/` directory. The registry name of the barrel will use the name of this JSON file, so make sure not to use any spaces or uppercase letters.

The following properties are customizable for barrels:

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `sound_type` | SoundType | Defines the sounds made by this block. [More info](./sound_types.md) |
| `strength` | float | Defines block hardness and blast resistance. |
| `map_color` | integer | The color of this block in a map or minimap. [More info](https://minecraft.wiki/w/Map_item_format#Base_colors) |
| `fireproof` | boolean | OPTIONAL: Whether this barrel can handle hot fluids or burns. |
| `transparent` | boolean | OPTIONAL: If true, renders sides and bottom of fluid contents. |
| `needs_correct_tool` | boolean | OPTIONAL: Whether a specific tool is required to mine. |
| `required_mod_id` | string | OPTIONAL: Hides block if mod is not installed. |

An example barrel JSON for an Iron Barrel, whose fluid contents should be rendered in 3D and that should be able to handle hot fluids:


```json
// .minecraft/config/exdeorum/barrel_materials/iron_barrel.json 
{
  "sound_type": "METAL",
  "strength": 5,
  "fireproof": true,
  "map_color": 6,
  "needs_correct_tool": true
}
```

<details>
<summary>Datapack and resource pack files for a Iron Barrel addded with the above JSON</summary>
<hr>
The datapack should have a recipe, loot table, and block/item tags for the barrel. Don't include the comments at the top of the files. <br><br>
        
The loot table:
```json
// mydatapack.zip, data/exdeorum/loot_tables/blocks/iron_barrel.json
{
  "type": "minecraft:block",
  "pools": [
    {
      "bonus_rolls": 0.0,
      "conditions": [
        {
          "condition": "minecraft:survives_explosion"
        }
      ],
      "entries": [
        {
          "type": "minecraft:item",
          "name": "exdeorum:iron_barrel"
        }
      ],
      "rolls": 1.0
    }
  ],
  "random_sequence": "exdeorum:blocks/iron_barrel"
}
```
The recipe:
```json
// mydatapack.zip, data/exdeorum/recipes/iron_barrel.json
{
  "type": "minecraft:crafting_shaped",
  "category": "misc",
  "key": {
    "m": {
      "item": "minecraft:heavy_weighted_pressure_plate"
    },
    "s": {
      "item": "minecraft:iron_ingot"
    }
  },
  "pattern": [
    "s s",
    "s s",
    "sms"
  ],
  "result": {
    "item": "exdeorum:iron_barrel"
  }
}
```
The block tag file for harvesting with a pickaxe:
```json
// mydatapack.zip, data/minecraft/tags/blocks/mineable/pickaxe.json
{
  "values": [
    "exdeorum:iron_barrel"
  ]
}
```
The item tag file:
```json
// mydatapack.zip, data/exdeorum/tags/items/stone_barrels.json
{
  "values": [
    "exdeorum:iron_barrel"
  ]
}
```
<hr>
The resource pack should include a blockstate file, a block and item model, and optionally textures. For Iron Block, we'll just use Vanilla texture. <br><br>
The blockstate file:
```json
// myresourcepack.zip, assets/exdeorum/blockstates/iron_barrel.json
{
  "variants": {
    "": {
      "model": "exdeorum:block/iron_barrel"
    }
  }
}
```
The block model file:
```json
// myresourcepack.zip, assets/exdeorum/models/block/iron_barrel.json
{
  "parent": "exdeorum:block/template_barrel",
  "textures": {
    "barrel": "minecraft:block/iron_block"
  }
}
```
The item model file:
```json
// myresourcepack.zip, assets/exdeorum/models/item/iron_barrel.json
{
  "parent": "exdeorum:block/iron_barrel"
}
```
</details>
<hr>

## Custom Sieve
To register a new type of sieve, add a JSON file to the `.minecraft/config/exdeorum/sieve_materials/` directory. The registry name of the sieve will use the name of this JSON file, so make sure not to use any spaces or uppercase letters.     

The following properties are customizable for sieves:

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `sound_type` | SoundType | Defines the sounds made by this block. [More info](./sound_types.md) |
| `strength` | float | Defines block hardness and blast resistance. |
| `needs_correct_tool` | boolean | OPTIONAL: Whether a specific tool is required to mine. |
| `required_mod_id` | string | OPTIONAL: Hides block if mod is not installed. |

An example barrel JSON for a Stone Sieve:

```json
// .minecraft/config/exdeorum/sieve_materials/stone_sieve.json 
{
  "sound_type": "STONE",
  "strength": 2,
  "needs_correct_tool": true
}
```

<details>
<summary>Datapack and resource pack files for a Stone Sieve addded with the above JSON</summary>
<hr>
The datapack should have a recipe, loot table, and block tags for the barrel. Don't include the comments at the top of the files.  <br><br>
        
The loot table:
```json
// mydatapack.zip, data/exdeorum/loot_tables/blocks/stone_sieve.json
{
  "type": "minecraft:block",
  "pools": [
    {
      "bonus_rolls": 0.0,
      "conditions": [
        {
          "condition": "minecraft:survives_explosion"
        }
      ],
      "entries": [
        {
          "type": "minecraft:item",
          "name": "exdeorum:stone_sieve"
        }
      ],
      "rolls": 1.0
    }
  ],
  "random_sequence": "exdeorum:blocks/stone_sieve"
}
```
The recipe:
```json
// mydatapack.zip, data/exdeorum/recipes/stone_sieve.json
{
  "type": "minecraft:crafting_shaped",
  "category": "misc",
  "key": {
    "I": {
      "item": "exdeorum:stone_pebble"
    },
    "O": {
      "item": "minecraft:stone"
    },
    "_": {
      "item": "minecraft:stone_slab"
    }
  },
  "pattern": [
    "O O",
    "O_O",
    "I I"
  ],
  "result": {
    "item": "exdeorum:stone_sieve"
  }
}
```
The block tag file for harvesting with a pickaxe:
```json
// mydatapack.zip, data/minecraft/tags/blocks/mineable/pickaxe.json
{
  "values": [
    "exdeorum:stone_sieve"
  ]
}
```
<hr>

The resource pack should include a blockstate file, a block and item model, and optionally textures. For Stone, we'll just use Vanilla texture. <br><br>
The blockstate file:
```json
// myresourcepack.zip, assets/exdeorum/blockstates/stone_sieve.json
{
  "variants": {
    "": {
      "model": "exdeorum:block/stone_sieve"
    }
  }
}
```
The block model file:
```json
// myresourcepack.zip, assets/exdeorum/models/block/stone_sieve.json
{
  "parent": "exdeorum:block/template_sieve",
  "textures": {
    "texture": "minecraft:block/stone"
  }
}
```
The item model file:
```json
// myresourcepack.zip, assets/exdeorum/models/item/stone_sieve.json
{
  "parent": "exdeorum:block/stone_sieve"
}
```
</details>
<hr>

## Custom Crucible
To register a new type of crucible, add a JSON file to either the `.minecraft/config/exdeorum/lava_crucible_materials/` or `.minecraft/config/exdeorum/water_crucible_materials/` directory, depending on the type of crucible you'd like to add. The registry name of the crucible will use the name of this JSON file, so make sure not to use any spaces or uppercase letters.     

The following properties are customizable for crucibles:

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `sound_type` | SoundType | Defines the sounds made by this block. [More info](./sound_types.md) |
| `strength` | float | Defines block hardness and blast resistance. |
| `map_color` | integer | The color of this block in a map or minimap. [More info](https://minecraft.wiki/w/Map_item_format#Base_colors) |
| `needs_correct_tool` | boolean | OPTIONAL: Whether a specific tool is required to mine. |
| `required_mod_id` | string | OPTIONAL: Hides block if mod is not installed. |

An example barrel JSON for an Iron Crucible:

```json
// .minecraft/config/exdeorum/lava_crucible_materials/iron_crucible.json 
{
  "sound_type": "METAL",
  "strength": 5,
  "map_color": 6,
  "needs_correct_tool": true
}
```

<details>
<summary>Datapack and resource pack files for an Iron Crucible addded with the above JSON</summary>
<hr>
The datapack should have a recipe, loot table, and block tags for the crucible. Don't include the comments at the top of the files.  <br><br>
        
The loot table:
```json
// mydatapack.zip, data/exdeorum/loot_tables/blocks/iron_crucible.json
{
  "type": "minecraft:block",
  "pools": [
    {
      "bonus_rolls": 0.0,
      "conditions": [
        {
          "condition": "minecraft:survives_explosion"
        }
      ],
      "entries": [
        {
          "type": "minecraft:item",
          "name": "exdeorum:iron_crucible"
        }
      ],
      "rolls": 1.0
    }
  ],
  "random_sequence": "exdeorum:blocks/iron_crucible"
}
```
The recipe:
```json
// mydatapack.zip, data/exdeorum/recipes/iron_crucible.json
{
  "type": "minecraft:crafting_shaped",
  "category": "misc",
  "key": {
    "O": {
      "item": "minecraft:iron_ingot"
    },
    "_": {
      "item": "minecraft:heavy_weighted_pressure_plate"
    }
  },
  "pattern": [
    "O O",
    "O O",
    "O_O"
  ],
  "result": {
    "item": "exdeorum:iron_crucible"
  }
}
```
The block tag file for harvesting with a pickaxe:
```json
// mydatapack.zip, data/minecraft/tags/blocks/mineable/pickaxe.json
{
  "values": [
    "exdeorum:iron_crucible"
  ]
}
```
<hr>

The resource pack should include a blockstate file, a block and item model, and optionally textures. For Stone, we'll just use Vanilla texture. <br><br>
The blockstate file:
```json
// myresourcepack.zip, assets/exdeorum/blockstates/iron_crucible.json
{
  "variants": {
    "": {
      "model": "exdeorum:block/iron_crucible"
    }
  }
}
```
The block model file:
```json
// myresourcepack.zip, assets/exdeorum/models/block/iron_crucible.json
{
  "parent": "exdeorum:block/template_crucible",
  "textures": {
    "texture": "minecraft:block/iron_block"
  }
}
```
The item model file:
```json
// myresourcepack.zip, assets/exdeorum/models/item/iron_crucible.json
{
  "parent": "exdeorum:block/iron_crucible"
}
```
</details>
