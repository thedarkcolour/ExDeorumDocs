# Sound Types
This page gives details on what constitutes a valid `SoundType` for [custom block materials](./customblocktypes.md).

A sound type can either be a string pointing to a Vanilla sound type, or it can be a JSON object defining a custom sound type.
The most common sound types used by Ex Deorum's sieves and barrels are:
```json
"sound_type": "WOOD"
"sound_type": "NETHER_WOOD"
"sound_type": "CHERRY_WOOD"
"sound_type": "BAMBOO_WOOD"
"sound_type": "STONE"
```

A JSON sound type has the following schema:

| Sound | Description |
| ----- | ----------- |
| `break_sound` | The sound made when this block is broken. |
| `step_sound` | The sound made by entities walking on this block. |
| `place_sound` | The sound made when this block is placed. |
| `hit_sound` | The sound made by this block while breaking it. |
| `fall_sound` | The sound made when an entity falls on this block. |

An example mimicking Vanilla's `SoundType.WOOD`:

```json
"sound_type": {
  "break_sound": "minecraft:wood_break",
  "step_sound": "minecraft:wood_step",
  "place_sound": "minecraft:wood_place",
  "hit_sound": "minecraft:wood_hit",
  "fall_sound": "minecraft:fall_sound"
}
```

A string sound type must be one of the following options, case-insensitive:
```json
"sound_type": "EMPTY"
"sound_type": "WOOD"
"sound_type": "GRAVEL"
"sound_type": "GRASS"
"sound_type": "LILY_PAD"
"sound_type": "STONE"
"sound_type": "METAL"
"sound_type": "GLASS"
"sound_type": "WOOL"
"sound_type": "SAND"
"sound_type": "SNOW"
"sound_type": "POWDER_SNOW"
"sound_type": "LADDER"
"sound_type": "ANVIL"
"sound_type": "SLIME_BLOCK"
"sound_type": "HONEY_BLOCK"
"sound_type": "WET_GRASS"
"sound_type": "CORAL_BLOCK"
"sound_type": "BAMBOO"
"sound_type": "BAMBOO_SAPLING"
"sound_type": "SCAFFOLDING"
"sound_type": "SWEET_BERRY_BUSH"
"sound_type": "CROP"
"sound_type": "HARD_CROP"
"sound_type": "VINE"
"sound_type": "NETHER_WART"
"sound_type": "LANTERN"
"sound_type": "STEM"
"sound_type": "NYLIUM"
"sound_type": "FUNGUS"
"sound_type": "ROOTS"
"sound_type": "SHROOMLIGHT"
"sound_type": "WEEPING_VINES"
"sound_type": "TWISTING_VINES"
"sound_type": "SOUL_SAND"
"sound_type": "SOUL_SOIL"
"sound_type": "BASALT"
"sound_type": "WART_BLOCK"
"sound_type": "NETHERRACK"
"sound_type": "NETHER_BRICKS"
"sound_type": "NETHER_SPROUTS"
"sound_type": "NETHER_ORE"
"sound_type": "BONE_BLOCK"
"sound_type": "NETHERITE_BLOCK"
"sound_type": "ANCIENT_DEBRIS"
"sound_type": "LODESTONE"
"sound_type": "CHAIN"
"sound_type": "NETHER_GOLD_ORE"
"sound_type": "GILDED_BLACKSTONE"
"sound_type": "CANDLE"
"sound_type": "AMETHYST"
"sound_type": "AMETHYST_CLUSTER"
"sound_type": "SMALL_AMETHYST_BUD"
"sound_type": "MEDIUM_AMETHYST_BUD"
"sound_type": "LARGE_AMETHYST_BUD"
"sound_type": "TUFF"
"sound_type": "TUFF_BRICKS"
"sound_type": "POLISHED_TUFF"
"sound_type": "CALCITE"
"sound_type": "DRIPSTONE_BLOCK"
"sound_type": "POINTED_DRIPSTONE"
"sound_type": "COPPER"
"sound_type": "COPPER_BULB"
"sound_type": "COPPER_GRATE"
"sound_type": "CAVE_VINES"
"sound_type": "SPORE_BLOSSOM"
"sound_type": "AZALEA"
"sound_type": "FLOWERING_AZALEA"
"sound_type": "MOSS_CARPET"
"sound_type": "PINK_PETALS"
"sound_type": "MOSS"
"sound_type": "BIG_DRIPLEAF"
"sound_type": "SMALL_DRIPLEAF"
"sound_type": "ROOTED_DIRT"
"sound_type": "HANGING_ROOTS"
"sound_type": "AZALEA_LEAVES"
"sound_type": "SCULK_SENSOR"
"sound_type": "SCULK_CATALYST"
"sound_type": "SCULK"
"sound_type": "SCULK_VEIN"
"sound_type": "SCULK_SHRIEKER"
"sound_type": "GLOW_LICHEN"
"sound_type": "DEEPSLATE"
"sound_type": "DEEPSLATE_BRICKS"
"sound_type": "DEEPSLATE_TILES"
"sound_type": "POLISHED_DEEPSLATE"
"sound_type": "FROGLIGHT"
"sound_type": "FROGSPAWN"
"sound_type": "MANGROVE_ROOTS"
"sound_type": "MUDDY_MANGROVE_ROOTS"
"sound_type": "MUD"
"sound_type": "MUD_BRICKS"
"sound_type": "PACKED_MUD"
"sound_type": "HANGING_SIGN"
"sound_type": "NETHER_WOOD_HANGING_SIGN"
"sound_type": "BAMBOO_WOOD_HANGING_SIGN"
"sound_type": "BAMBOO_WOOD"
"sound_type": "NETHER_WOOD"
"sound_type": "CHERRY_WOOD"
"sound_type": "CHERRY_SAPLING"
"sound_type": "CHERRY_LEAVES"
"sound_type": "CHERRY_WOOD_HANGING_SIGN"
"sound_type": "CHISELED_BOOKSHELF"
"sound_type": "SUSPICIOUS_SAND"
"sound_type": "SUSPICIOUS_GRAVEL"
"sound_type": "DECORATED_POT"
"sound_type": "DECORATED_POT_CRACKED"
"sound_type": "TRIAL_SPAWNER"
"sound_type": "SPONGE"
"sound_type": "WET_SPONGE"
```