## csv2terrain 
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/quantumjim/csv2terrain/master?filepath=island_generator_demo.ipynb)

This is a mod for [Minetest](https://github.com/minetest/). It has been intended to be used as part of the standard [Minetest game](https://github.com/minetest/minetest_game). For best results, use in conjunction with the [flatgen mod](https://forum.minetest.net/viewtopic.php?id=8952).

Details on how to install a Minetest mod are [here](https://wiki.minetest.net/Installing_Mods).

This mod reads in data from 'blocks.csv', a user provided csv file which should have lines of the form

`x,y,z,keyword,`

Where `x`, `y` and `z` are numbers. 

If the keyword is *player*, the position (x,y,z) is used as the spawn point of the player whenever a new game is started or a file is openened

The keywords can also be names of blocks. The following are known to work (in conjunction with the default mod).

```
dirt_with_grass, sand, stone, 
water_source, lava_source, 
tree, leaves, torch, 
diamondblock, goldblock, stone_with_coal, stone_with_iron, stone_with_copper, stone_with_tin, stone_with_gold, stone_with_diamond
fern_1, fern_2, fern_3, marram_grass_1, marram_grass_2, marram_grass_3
```

The mod adds these blocks to their specified positions whenever the command `/ltbv` is invoked. This stands for 'Let there be voxels!', to allow the player their moment of creation.

If there are weird gaps in terrain generated in this way, simply try invoking the command again to patch it up. If there are weird dark patches, it seems best to just try again with a new world.

Note that keywords *min* and *max* also need to be present in the csv. The coordinates for these define the volume in which all the blocks reside.

A csv generator is included within the mod, generates terrain using [Qiskit](https://qiskit.org). It needs to be run separately from the game, and runs using Python 3.
