# KubeJS Support
Ex Deorum provides some functionality that should make it easier to use KubeJS to customize the machines. Here is a list of every function added by Ex Deorum to KubeJS, under the `exdeorum` extension. [Types](#types) added by Ex Deorum are listed at the bottom of the page.
## Removing default sieve recipes
Removes every sieve recipe added by Ex Deorum. Useful if you prefer to write your own sieve drops instead of using the default ones.
```js
ServerEvents.recipes((event) => {
  // Removes every Sieve recipe added by default in Ex Deorum
  event.remove({type: "exdeorum:sieve"})
  // Removes every Compressed Sieve recipe added by default in Ex Deorum
  event.remove({type: "exdeorum:compressed_sieve"})
});
```
### Removing specific sieve recipes
Ex Deorum modifies KubeJS's `remove` function to also accept a `sieve_mesh` property, useful for removing Sieve recipes based on what mesh they use. Here's an example of what that looks like:
```js
// Removes every sieve recipe added by Ex Deorum for Gravel that uses the Flint Mesh
ServerEvents.recipes((event) => {
  event.remove({
    input: 'minecraft:gravel',
    sieve_mesh: 'exdeorum:flint_mesh',
    type: 'exdeorum:sieve',
    mod: 'exdeorum'
  });
});
```

## Removing default heat sources
Removes all default crucible heat sources added by Ex Deorum.
```js
ServerEvents.recipes((event) => {
  event.remove({type: "exdeorum:crucible_heat_source"})
});
```