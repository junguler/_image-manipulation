## what is needed to get started?
tiler is a cool and amazing python cli programs that uses small pictures (tiles) to recreate pictures in those styles, find the github repo [here](https://github.com/nuno-faria/tiler) visit the repo to know how to install

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and some royalty free stock footage from youtube

## explanation of the config file and how the program works
customizing config is done by changing values in the `conf.py` and there is two different sections for changing config, one is for `gen_tiles.py` which is for making custom color varients of our tiles and `tiler.py` which is the main part of program that converts our images

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
the program itself comes with some examples of tiles already, lets use them to show how the program works and then we can get to making custom shapes
```
python3 tiler.py bird.jpg tiles/plus/gen_plus/
```
first we tell our shell tiler is a python3 program, and import our image to be converted and finally choose the tiling effect of plus signs

![bird-tiled](https://user-images.githubusercontent.com/59083599/137897304-86e6ec25-84bd-40b2-9fe3-3bdc0a3af951.jpg)

```
python3 tiler.py sun.jpg tiles/times/gen_times/
```
![sun-tiled](https://user-images.githubusercontent.com/59083599/137898424-0f8e6f07-3b33-40d3-9551-68bc0ca93430.jpg)

## unifromed output
so far we've been using the default option of `PIXEL_SHIFT = (5, 5)` which alows for for each pixel to be shifted 5 pixels in x and y axis which lets our image have empty spots and un uniformed shapes, setting this value to None `PIXEL_SHIFT = None` in our `conf.py` makes everything uniform and also greatly speeds up our conversion speeds
```
python3 tiler.py window.jpg tiles/circles/gen_circle_100/
```
![window-tiled](https://user-images.githubusercontent.com/59083599/137899308-3cc966a6-4122-475e-9853-e4605ef812d0.jpg)
```
python3 tiler.py ladyLiberty.jpg tiles/waves/gen_wave/
```
![ladyLiberty-tiled](https://user-images.githubusercontent.com/59083599/137900389-43db6d93-986d-468e-a13a-2cbe5b4a20cf.jpg)

## using multiple tile types
this is very easy, just copy everything you like into a folder, lets do this image with plus and times shapes, make a new folder called combo for example, copy evertyhing from the tiles/plus/gen_plus/ and tiles/times/gen_times/ into our combo folder
```
python3 tiler.py rhino.jpg tiles/combo/
```
![rhino-tiled](https://user-images.githubusercontent.com/59083599/137902311-8e78bece-81ee-489c-aaf9-0add9d19695e.jpg)

vertical and horizontal lines
```
python3 tiler.py rug.jpg tiles/combo2/
```
![rug-tiled](https://user-images.githubusercontent.com/59083599/137903375-06676921-98bc-4b15-a3ee-5eb574ea66be.jpg)

### more examples coming soon including making custom shapes, animted gifs and tiled video clips
