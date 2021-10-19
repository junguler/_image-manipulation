## what is needed to get started?
tiler is a cool and amazing python cli programs that uses small pictures (tiles) to recreate pictures in those styles, find the github repo [here](https://github.com/nuno-faria/tiler)
visit the repo to know how to install

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and some royalty free stock footage from youtube

## explanation of the config file and how the program works
customizing config is done by changing values in the `conf.py` and there is two different sections for changing config, one is for `gen_tiles.py` which is for making custom color varients of our tiles 
and `tiler.py` which is the main part of program that converts our images

| config | default | gen_tiles.py |
| --- | --- | --- |
| DEPTH | DEPTH = 4 |number of divisions in each color channel (ex: DEPTH = 4 -> 4 * 4 * 4 = 64 colors) |
| ROTATIONS | ROTATIONS = [0] | list of rotations, in degrees, to apply over the original image (ex: [0, 90]) |

| config | default | tiler.py |
| --- | --- | --- |
| COLOR_DEPTH | COLOR_DEPTH = 32 | number of divisions in each color channel (ex: COLOR_DEPTH = 4 -> 4 * 4 * 4 = 64 colors) |
| RESIZING_SCALES | RESIZING_SCALES = [0.5, 0.4, 0.3, 0.2, 0.1] | scale to apply to each tile (ex: [1, 0.75, 0.5, 0.25]) |
| PIXEL_SHIFT | PIXEL_SHIFT = (5, 5) | number of pixels shifted to create each box (ex: (5,5)); if None, shift will be the same as the tile dimension) |
| OVERLAP_TILES | OVERLAP_TILES = False | if tiles can overlap |
| RENDER | RENDER = False | render image as its being built |
| POOL_SIZE | POOL_SIZE = 8 | multiprocessing pool size |
| IMAGE_TO_TILE | OUT = 'out.png' | image to tile (ignored if passed as the 1st arg) |
| TILES_FOLDER | IMAGE_TO_TILE = None | folder with tiles (ignored if passed as the 2nd arg) |
| OUT | TILES_FOLDER = None | result image filename |

## basic usage
