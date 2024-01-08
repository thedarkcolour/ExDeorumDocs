# KubeJS Support
Ex Deorum provides some functionality that should make it easier to use KubeJS to customize the machines. Here is a list of every function added by Ex Deorum to KubeJS, under the `exdeorum` extension. [Types](#types) added by Ex Deorum are listed at the bottom of the page.
## Functions
### `removeDefaultSieveRecipes(event: RecipesEventJS)`
Removes every sieve recipe added by Ex Deorum. Useful if you prefer to write your own sieve drops instead of using the default ones in Ex Deorum.
```js
ServerEvents.recipes((event) => {
  // Removes every sieve recipe added by default in Ex Deorum
  exdeorum.removeDefaultSieveRecipes(event);
});
```
***
### `removeDefaultHeatSources()`
Removes all default heat sources added by Ex Deorum from the crucible.
```js
// Removes every default heat source from the crucible.
exdeorum.removeDefaultHeatSources();
```
***
### `setCrucibleHeatValueForState(state: String, heatValue: int)`
Sets the heat value for the specified block state. The `state` string is parsed as a specific BlockState the same way as in the `/setblock` command, rather than every state of a block.
```js
// Sets the heat value of a lit furnace to 2. An inactive furnace will still have no heat value.
exdeorum.setCrucibleHeatValueForState('minecraft:furnace[lit=true]', 2);
```
***
### `setCrucibleHeatValue(block: Block, heatValue: int)`
Shortcut for [setCrucibleHeatValueForBlock](#setcrucibleheatvalueforblockblock-block-heatvalue-int).
### `setCrucibleHeatValueForBlock(block: Block, heatValue: int)`
Sets the heat value for every state of the specified block. Example:
```js
// Sets the heat value of white wool to 5.
exdeorum.setCrucibleHeatValueForBlock('minecraft:white_wool', 5);
// Equivalent
exdeorum.setCrucibleHeatValue('minecraft:white_wool', 5);
```
***
### `RecipeEventJS.remove(filter: RecipeFilter)`
Ex Deorum modifies the `remove` function to also accept a "sieve_mesh" property, useful for removing Sieve recipes based on what mesh they use. Here is an example of what that looks like:
```js
// Removes every sieve recipe added by Ex Deorum for Gravel that uses the Flint Mesh.
ServerEvents.recipes((event) => {
  event.remove({
    input: 'minecraft:gravel',
    sieve_mesh: 'exdeorum:flint_mesh',
    type: 'exdeorum:sieve',
    mod: 'exdeorum'
  });
});
```