# candle-simulator
This repository consists of Blender python scripts and corresponding assets to generate variants of the CANDLE dataset.

# Environment Setup
Download and install [Blender](https://www.blender.org/). Make sure that it's accessible from the command line. 

Note: Tests and rendering were performed on version 2.90. Unless future versions include breaking changes, functionality should be largely unaffected. Will be happy to receive a PR/issue if any issues arise.

# Running the script
The main script `candle_simulator.py` runs in an instance of blender invoked by the command:
```
# starts blender in the background, without audio and runs the python script
$ blender -b -noaudio -P candle_simulator.py
```

# The rendered CANDLE dataset
![CANDLE grid](./sample_images/grid.png)
The rendered version of the dataset is provided at [the CANDLE repository](https://causal-disentanglement.github.io/CANDLE/).

# Conventions followed while designing the simulator
- We recommend the objects fit in a 1x1x1m space at the origin. This helps with uniform translation and scaling.
- Backgrounds are node-based world textures pointing to a HDRI image. This helps with realistic global illumination. We recommend just copying it over and modifying the image to point to the required one.
- The filename and the property name in blender have to match. For ex., if adding a cuboid, call the object `cuboid` in the outline and name the file `cuboid.blend`.

# License
This work is licensed under the [MIT License](https://choosealicense.com/licenses/mit/).
