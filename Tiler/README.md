## what is needed to get started?
tiler is a cool and amazing python cli programs that uses small pictures (tiles) to recreate pictures in those styles, find the github repo [here](https://github.com/nuno-faria/tiler) visit the repo to know how to install

### quick links
 * [basic usage](https://github.com/junguler/_image-manipulation/tree/main/Tiler#basic-usage)
 * [uniformed output](https://github.com/junguler/_image-manipulation/tree/main/Tiler#unifromed-output)
 * [using multiple tile types](https://github.com/junguler/_image-manipulation/tree/main/Tiler#using-multiple-tile-types)
 * [making custom tiles](https://github.com/junguler/_image-manipulation/tree/main/Tiler#making-custom-tiles)
 * [using custom tiles](https://github.com/junguler/_image-manipulation/tree/main/Tiler#using-custom-tiles)

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

## making custom tiles
before i start showing examples of how to make custom tiles first i want to explain some details to let you create good tiles, first of all we need a transparent png file and our shape needs to have an RGB color of (240,240,240) which is almost completely white.

good            |  bad
:-------------------------:|:-------------------------:
![g1](https://user-images.githubusercontent.com/59083599/137913059-75905a8f-62b2-44dd-807c-415294e3a469.png)  |  ![b1](https://user-images.githubusercontent.com/59083599/137913098-0d8d0099-0b4f-4594-8a51-34a560fb0289.png)

your tile should be one big mass instead of many pieces

good            |  bad
:-------------------------:|:-------------------------:
![g2](https://user-images.githubusercontent.com/59083599/137913938-6fd20824-d2ec-4775-ac5b-335073c48dd5.png)  |  ![b2](https://user-images.githubusercontent.com/59083599/137913959-5f4c5434-9e35-41d4-84d6-15bfe1091291.png)

your tile should surpass all sides of your picture and not be floating inside

good            |  bad
:-------------------------:|:-------------------------:
![g3](https://user-images.githubusercontent.com/59083599/137914443-298a1b51-ba5b-45a6-8f22-c6340ccc647e.png)  |  ![b3](https://user-images.githubusercontent.com/59083599/137914464-69ca09db-5c8f-44e9-bce7-abd2b949478f.png)

and finally your shape should posses the whole picture and not leave empty spaces 

good            |  bad
:-------------------------:|:-------------------------:
![g4](https://user-images.githubusercontent.com/59083599/137914978-1c33ed74-6712-4821-b6e4-81fe49990fbd.png)  |  ![b4](https://user-images.githubusercontent.com/59083599/137915012-84a3cb80-2d6c-4385-a927-09cf6f1c9932.png)

note: i added the black background for people who use the github's light theme to be able to easily see, our shape png has to be transparent for the best result

## using custom tiles
now that we made our custom tiles, taking above explanations into consideration let's use the `gen_tiles.py` program to make other color varients of it.
```
python3 gen_tiles.py tiles/custom/tile1.png
```
this makes a folder named `gen_tile1` in the folder our `tile1.png` is with variations of colors and black to white saturations of our original tile, now lets use this folder to make a tiled picture

![A](https://user-images.githubusercontent.com/59083599/137919877-4f269735-3697-4ea2-bc90-eb016629229e.png)
```
python3 tiler.py snow.jpg tiles/custom/gen_tile1/
```
![snow-tiled](https://user-images.githubusercontent.com/59083599/137917805-21e47039-ee5c-44f5-9153-4aec3fecfc3c.jpg)

lets make another example, this time i make a copy of my tile and turn it 90 degrees to either side to have vertical and horizontal shapes, use `gen_tiles.py` on each of them and put the results into a folder to have combined effect

![B](https://user-images.githubusercontent.com/59083599/137919926-30e97115-8aba-47d8-850b-e9545dc5bd21.png) ![C](https://user-images.githubusercontent.com/59083599/137919941-783027e6-1fcb-471b-85f4-5ac5e0abe9a5.png)
```
python3 tiler.py flower.jpg tiles/custom2/gen_tile+/
```
![flower-tiled](https://user-images.githubusercontent.com/59083599/137919484-901b651c-d6d2-496f-95d1-2673cf77a38c.jpg)

### more examples coming soon including how to make animted gifs and tiled video clips
