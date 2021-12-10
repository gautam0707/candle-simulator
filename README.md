# candle-simulator
This repository consists of Blender python scripts and corresponding assets to generate variants of the IITH-CANDLE dataset.

# Environment Setup
Download and install [Blender](https://www.blender.org/). Make sure that it's accessible from the command line. 

**Note:** Tests and rendering were performed on version 2.90. Unless future versions include breaking changes, functionality should be largely unaffected. Will be happy to receive a PR/issue if any issues arise.

# Running the script
The main script `candle_simulator.py` runs in an instance of blender invoked by the command:
```
# starts blender in the background, without audio and runs the python script
$ blender -b -noaudio -P candle_simulator.py
```
# The rendered CANDLE dataset
![IITH-CANDLE grid](./sample_images/grid.png)
The rendered version of the dataset is provided at [the IITH-CANDLE repository](https://causal-disentanglement.github.io/IITH-CANDLE/).

# Extending CANDLE
Each factor of variation can be independently modified or extended by simply editing or adding `.blend` files under `./data/` consisting of just that factor. The script then combines them independently while generating the dataset.

## Steps to extend
1. Add in or modify a factor, say we add `./objects/monkey.blend`. Ensure that the filename and the property name of the factor in Blender match.
2. Update `properties: object_type` to include `monkey`.
3. Rendering a version now will augment IITH-CANDLE with all variants of monkey.

## Conventions followed
| Factor | Conventions |
| --- | --- |
| objects | We recommend the objects fit in a 1x1x1m space at the origin. This helps with uniform translation and scaling. Also update `properties: object_type`.|
| scenes | They are node-based world textures pointing to a HDRI image. We recommend just copying an existing one over and modifying the image to point to the required one. Also update `scenes` and `bounds` in the script with the XY coordinates where objects are allowed to be placed. |
| size | Just modify `properties: size` in the script. The objects will be scaled at runtime. |
| rotation | Just modify `properties: rotation` in the script. The objects will be rotated at runtime. |
| lights | To modify the type of light, edit `lights.blend`. If only the positions have to be changed, just edit `lights` and `light_position` correspondingly. |
| color (materials) | Vanilla Blender materials. Just modify `properties: color` as well. |

# License
This work is licensed under the [MIT License](https://choosealicense.com/licenses/mit/).
