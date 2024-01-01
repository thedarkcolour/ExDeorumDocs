# KubeJS Support
Ex Deorum provides some functionality that should make it easier to use KubeJS to customize the machines. Here is a list of every function added by Ex Deorum to KubeJS, under the `exdeorum` extension.

### `removeDefaultSieveRecipes(RecipesEventJS)`
Removes every sieve recipe added by Ex Deorum. Useful if you prefer to write your own sieve drops instead of using the default ones in Ex Deorum.
```js
ServerEvents.recipes((event) => {
  // Removes every sieve recipe added by default in Ex Deorum
  exdeorum.removeDefaultSieveRecipes(event);
});
```

### `removeDefaultHeatSources`
Removes all default heat sources added by Ex Deorum from the crucible.
```js
// Removes every default heat source from the crucible.
exdeorum.removeDefaultHeatSources();
```

### `setCrucibleHeatValueForState(state: String, heatValue: int)`
Sets the heat value for the specified block state. The `state` string is parsed as a specific BlockState the same way as in the `/setblock` command, rather than every state of a block.
```js
// Sets the heat value of a lit furnace to 2. An inactive furnace will still have no heat value.
exdeorum.setCrucibleHeatValueForState("minecraft:furnace[lit=true]", 2);
```

### `setCrucibleHeatValue(block: Block, heatValue: int)`
Shortcut for [setCrucibleHeatValueForBlock](#setcrucibleheatvalueforblockblock-block-heatvalue-int).
### `setCrucibleHeatValueForBlock(block: Block, heatValue: int)`
Sets the heat value for every state of the specified block. Example:
```js
exdeorum.setCrucibleHeatValueForBlock();
```