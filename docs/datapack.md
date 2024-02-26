# Datapack Support
Most of Ex Deorum is configurable through data packs.

To help modpack developers convert their datapacks over to Ex Deorum from Ex Nihilo: Sequentia, I wrote a Python program which converts ENS recipes to Ex Deorum recipes.    
Download it from [GitHub](https://github.com/thedarkcolour/ExDeorumRecipeConverter).
---
## Barrel Compost
A barrel compost recipe defines how much compost an item is worth when put into the barrel.    
Recipe type: `exdeorum:barrel_compost`    

| Property  | Type | Description |
| --------- | ------| ----------- |
| `ingredient` | ingredient | The input to be turned into compost. |
| `amount` | integer | The compost filled by this item. 1000 compoost makes one dirt. |

Example recipe for composting leaves into 125 compost:
```json
{
  "type": "exdeorum:barrel_compost",
  "ingredient": {
    "tag": "minecraft:leaves"
  },
  "volume": 125
}
```
---
## Barrel Item Mixing
A barrel item mixing recipe allows crafting an item by putting an item into a barrel with some fluid in it.      
Recipe type: `exdeorum:barrel_item_mixing`

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `ingredient` | ingredient | The input ingredient. |
| `fluid` | string | The registry ID of the fluid required for this recipe. |
| `fluid_amount` | integer | The amount of fluid used to craft this recipe. |
| `result` | string | The registry ID of the item crafted by this recipe. |

Example recipe for mixing dust into water to create clay:
```json
{
  "type": "exdeorum:barrel_mixing",
  "fluid": "minecraft:water",
  "fluid_amount": 1000,
  "ingredient": {
    "item": "exdeorum:dust"
  },
  "result": "minecraft:clay"
}
```
---
## Barrel Fluid Mixing
A barrel fluid mixing allows crafting an item by combining two fluids using a barrel. An example of this is crafting Obsidian inside a barrel. Note that recipes which have hot base fluids can only be crafted inside fire resistant barrels, like Stone barrels or Warped/Crimson barrels.    
Recipe type: `exdeorum:barrel_fluid_mixing`

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `base_fluid` | string | The registry ID of the fluid inside the barrel used for crafting. |
| `base_fluid_amount` | integer | The amount fluid inside the barrel used for crafting. |
| `additive_fluid` | string | The registry ID of the fluid placed on top of the barrel. |
| `fluid_amount` | integer | The amount of fluid used to craft this recipe. |
| `result` | string | The registry ID of the item crafted by this recipe. |
| `consumes_additive` | boolean | OPTIONAL: If the additive fluid is consumed. Default: true|

Example recipe for mixing water into lava to craft obsidian:
```json
{
  "type": "exdeorum:barrel_fluid_mixing",
  "additive_fluid": "minecraft:water",
  "base_fluid": "minecraft:lava",
  "base_fluid_amount": 1000,
  "consumes_additive": false,
  "result": "minecraft:obsidian"
}
```
---
## Barrel Fluid Transformation
As of Ex Deorum 1.25, barrel fluid transformation recipes are not currently supported in Ex Deorum. Check [this issue](https://github.com/thedarkcolour/ExDeorum/issues/4) for updates.

---
## Crucible Heat Source
A crucible heat source recipe defines the heat multiplier of a block when placed below a lava crucible.    
Recipe type: `exdeorum:crucible_heat_source`

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `block_predicate` | block_predicate | Specifies which blocks count as this heat source. |
| `heat_value` | integer | The heat multiplier for this heat source. |

Example recipe for giving lit campfires a heat multiplier of 2x:
```json
{
  "type": "exdeorum:crucible_heat_source",
  "block_predicate": {
    "block": "minecraft:campfire",
    "state": {
      "lit": "true"
    }
  },
  "heat_value": 2
}
```
---
## Crucible
A crucible recipe defines what fluid is produced by melting a certain block in a crucible. Ex Deorum uses two separate recipe types to distinguish between "water crucibles" (made of non-fireproof wood and usually produce water) and "lava crucibles" (made of fireproof materials and usually produce lava, affected by heat sources). Besides that, the recipe JSONs are written in exactly the same way.   
Recipe type for Lava Crucible: `exdeorum:lava_crucible`     
Recipe type for Water Crucible: `exdeorum:water_crucible`

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `ingredient` | ingredient | The input to be melted into fluid. |
| `fluid` | FluidStack | The fluid resulting from melting the ingredient. |

Example Lava Crucible recipe for turning Netherrack into 500mb of Lava:
```json
{
  "type": "exdeorum:lava_crucible",
  "fluid": {
    "Amount": 500,
    "FluidName": "minecraft:lava"
  },
  "ingredient": {
    "tag": "forge:netherrack"
  }
}
```

Example Water Crucible recipe for turning Leaves into 250mb of Water:
```json
{
  "type": "exdeorum:water_crucible",
  "fluid": {
    "Amount": 250,
    "FluidName": "minecraft:water"
  },
  "ingredient": {
    "tag": "minecraft:leaves"
  }
}
```
---
## Crook
A crook recipe defines a single drop for a certain block when broken with a crook (any item in the tag `#exdeorum:crooks`).    
Recipe type: `exdeorum:crook`

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `block_predicate` | block_predicate | Specifies which blocks this item can drop from. |
| `chance` | float | The probability of this item dropping. |
| `result` | string | The registry ID of the item to drop. |

Example recipe for giving silkworms a 1% chance to drop from leaves:
```json
{
  "type": "exdeorum:crook",
  "block_predicate": {
    "block_tag": "minecraft:leaves"
  },
  "chance": 0.01,
  "result": "exdeorum:silk_worm"
}
```
---
## Hammer
A hammer recipe defines a single drop for a certain block when broken with a  hammer (any item in the tag `#exdeorum:hammers`) with the appropriate mining level.    
Recipe type: `exdeorum:hammer`

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `ingredient` | ingredient | Specifies which blocks this item can drop from. |
| `result` | string | The registry ID of the item to drop. |
| `result_amount` | number provider | The quantity dropped. See [Minecraft Wiki](https://minecraft.wiki/w/Loot_table#Number_provider) for info. |

Example recipe for crushing Deepslate and Cobbled Deepslate into Crushed Deepslate:
```json
{
  "type": "exdeorum:hammer",
  "ingredient": [
    {
      "item": "minecraft:deepslate"
    },
    {
      "item": "minecraft:cobbled_deepslate"
    }
  ],
  "result": "exdeorum:crushed_deepslate",
  "result_amount": 1.0
}
```
---
## Sieve
A sieve recipe defines a single sieve drop for a certain block using a certain mesh.     
Recipe type: `exdeorum:sieve`

| Property  | Type | Description |
| --------- | ------- | ----------- |
| `ingredient` | ingredient | The item to be sifted. |
| `mesh` | string | The registry ID of the mesh used for sifting. |
| `result` | string | The registry ID of the item dropped from this recipe. |
| `result_amount` | number provider | The quantity dropped. See [Minecraft Wiki](https://minecraft.wiki/w/Loot_table#Number_provider) for info. |
| `result` | string | The registry ID of the item crafted by this recipe. |
| `consumes_additive` | boolean | OPTIONAL: If the additive fluid is consumed. Default: true|

Example recipe for giving Raw Gold an 8% chance of dropping from Red Sand using a Diamond Mesh:
```json
{
  "type": "exdeorum:sieve",
  "ingredient": {
    "item": "minecraft:red_sand"
  },
  "mesh": "exdeorum:diamond_mesh",
  "result": "minecraft:raw_gold",
  "result_amount": {
    "type": "minecraft:binomial",
    "n": 1.0,
    "p": 0.08
  }
}
```
Example recipe for always dropping an Iron Nugget from Crushed Deepslate using a Diamond Mesh:
```json
{
  "type": "exdeorum:sieve",
  "ingredient": {
    "item": "minecraft:crushed_deepslate"
  },
  "mesh": "exdeorum:diamond_mesh",
  "result": "minecraft:iron_ingot",
  "result_amount": 1
}
```


## Important Types
Types used in the JSON recipes are described here. This should help clarify how the recipes are made.

---
### ingredient
An ingredient is a JSON type used in Vanilla Minecraft's crafting recipes. You can read about how it is used on the [Minecraft Wiki](https://minecraft.wiki/w/Recipe).
An ingredient is made up of "ingredient values". Values are JSON objects that can specify an "item" or "tag" property. Ingredients can be written either as an array of ingredient values or just as a single ingredient value.     

Here are a few examples:     

An ingredient matching one specific item, using one "item" value:
```json
"ingredient": {
  "item": "minecraft:cake"
}
```
An ingredient matching any item from a specific tag, using a "tag" value:
```json
"ingredient": {
  "tag": "minecraft:leaves"
}
```
An ingredient matching two possible items, using two "item" values (notice how an array is used this time):
```json
"ingredient": [
  {
    "item": "minecraft:deepslate"
  },
  {
    "item": "minecraft:cobbled_deepslate"
  }
]
```
---

### number provider
A number provider represents a number value that might be randomly chosen. In Vanilla Minecraft, they are used mostly in Loot Tables to determine how many items to drop. Although Ex Deorum adds additional functionality to them, most of the information about number providers can be found on the [Minecraft Wiki](https://minecraft.wiki/w/Loot_table#Number_provider).     
In addition to the types of number providers used by Vanilla Minecraft, Ex Deorum adds a Summation provider, with the type `exdeorum:summation`. The summation provider uses one field, an array of number providers called "values". The random value chosen by a summation number provider is just the sum of random values chosen by the number providers in its values array. Here are a few examples of number providers:    
A constant number provider of 1. No matter what, the result will always be one:
```json
"result_amount": 1
```
A [uniform](https://en.wikipedia.org/wiki/Continuous_uniform_distribution) number provider, giving values between 2 and 4 with equal likelihood:
```json
"result_amount": {
  "type": "minecraft:uniform",
  "max": 4.0,
  "min": 2.0  
}
```
A [binomial](https://en.wikipedia.org/wiki/Binomial_distribution) number provider, with a 70% chance of being 1, 30% chance of being 0:
```json
"result_amount": {
  "type": "minecraft:binomial",
  "n": 1.0,
  "p": 0.7
}
```

A summation number provider, with a 40% chance of being 2, 60% chance of being 1:
```json
"result_amount": {
  "type": "exdeorum:summation",
  "values": [
    1,
    {
      "type": "minecraft:binomial",
      "n": 1.0,
      "p": 0.4
    }
  ]
}
```
---

### block predicate
A block predicate is a type added by Ex Deorum that includes blocks matching certain conditions. A block predicate can either match a single block, a single block with specific block state properties (ex. a lit campfire), or any block belonging to a certain tag. Here are examples of each:    
A block predicate only matching fire:
```json
"block_predicate": {
  "block": "minecraft:fire"
}
```
A block predicate only matching campfires when they are lit:
```json
"block_predicate": {
  "block": "minecraft:campfire",
  "state": {
    "lit": "true"
  }
}
```
A block predicate matching any block in the `minecraft:leaves` tag:
```json
"block_predicate": {
  "block_tag": "minecraft:leaves"
}
```