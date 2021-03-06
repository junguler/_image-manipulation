# Tiler
tiler is a cool and amazing python cli programs that uses small pictures (tiles) to recreate pictures in those styles, find the github repo [here](https://github.com/nuno-faria/tiler) and read about how to install it

<br>

### quick links
 * [basic usage](https://github.com/junguler/_image-manipulation/tree/main/Tiler#basic-usage)
 * [uniformed output](https://github.com/junguler/_image-manipulation/tree/main/Tiler#unifromed-output)
 * [using multiple tile types](https://github.com/junguler/_image-manipulation/tree/main/Tiler#using-multiple-tile-types)
 * [making custom tiles](https://github.com/junguler/_image-manipulation/tree/main/Tiler#making-custom-tiles)
 * [using custom tiles](https://github.com/junguler/_image-manipulation/tree/main/Tiler#using-custom-tiles)
 * [change resizing scale](https://github.com/junguler/_image-manipulation/tree/main/Tiler#change-resizing-scale)
 * [overlap tiles](https://github.com/junguler/_image-manipulation/tree/main/Tiler#overlap-tiles)
 * [changing colors](https://github.com/junguler/_image-manipulation/tree/main/Tiler#changing-colors)
 * [tilify a video](https://github.com/junguler/_image-manipulation/tree/main/Tiler#tilify-a-video)
 * [make animated gif out of one photo](https://github.com/junguler/_image-manipulation/tree/main/Tiler#make-animated-gif-out-of-one-picture)
 * [make gif by changing colors](https://github.com/junguler/_image-manipulation/tree/main/Tiler#make-gif-by-changing-colors)

<br>

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and some royalty free stock footage from youtube

<br>

## explanation of the config file and how the program works
customizing config is done by changing values in the `conf.py` and there is two different sections for changing config, one is for `gen_tiles.py` which is for making custom color variants of our tiles and `tiler.py` which is the main part of program that converts our images

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

<br>

## basic usage
the repo of program comes with some examples of tiles already, lets use them to show how the program works and then we can get to making custom shapes
```
python3 tiler.py bird.jpg tiles/plus/gen_plus/
```
first we tell our shell tiler is a python3 program, and import our image to be converted and finally choose the tiling effect of plus signs

![bird-tiled](https://user-images.githubusercontent.com/59083599/137897304-86e6ec25-84bd-40b2-9fe3-3bdc0a3af951.jpg)

```
python3 tiler.py sun.jpg tiles/times/gen_times/
```
![sun-tiled](https://user-images.githubusercontent.com/59083599/137898424-0f8e6f07-3b33-40d3-9551-68bc0ca93430.jpg)

<br>

## uniformed output
so far we've been using the default option of `PIXEL_SHIFT = (5, 5)` which alows for for each pixel to be shifted 5 pixels in x and y axis which lets our image have empty spots and un uniformed shapes, setting this value to None `PIXEL_SHIFT = None` in our `conf.py` makes everything uniform and also greatly speeds up our conversion speeds
```
python3 tiler.py window.jpg tiles/circles/gen_circle_100/
```
![window-tiled](https://user-images.githubusercontent.com/59083599/137899308-3cc966a6-4122-475e-9853-e4605ef812d0.jpg)
```
python3 tiler.py ladyLiberty.jpg tiles/waves/gen_wave/
```
![ladyLiberty-tiled](https://user-images.githubusercontent.com/59083599/137900389-43db6d93-986d-468e-a13a-2cbe5b4a20cf.jpg)

<br>

## using multiple tile types
this is very easy, just copy everything you like into a folder, lets do this image with plus and times shapes, make a new folder called combo for example, copy everything from the tiles/plus/gen_plus/ and tiles/times/gen_times/ into our combo folder
```
python3 tiler.py rhino.jpg tiles/combo/
```
![rhino-tiled](https://user-images.githubusercontent.com/59083599/137902311-8e78bece-81ee-489c-aaf9-0add9d19695e.jpg)

vertical and horizontal lines
```
python3 tiler.py rug.jpg tiles/combo2/
```
![rug-tiled](https://user-images.githubusercontent.com/59083599/137903375-06676921-98bc-4b15-a3ee-5eb574ea66be.jpg)

<br>

## making custom tiles
before i start showing examples of how to make custom tiles first i want to explain some details to let you create good tiles, first of all we need a transparent png file and our shape needs to have an RGB color of (240,240,240) which is almost completely white.

good  |  bad
:-------------------------:|:-------------------------:
![g1](https://user-images.githubusercontent.com/59083599/137913059-75905a8f-62b2-44dd-807c-415294e3a469.png)  |  ![b1](https://user-images.githubusercontent.com/59083599/137913098-0d8d0099-0b4f-4594-8a51-34a560fb0289.png)

your tile should be one big mass instead of many pieces

good  |  bad
:-------------------------:|:-------------------------:
![g2](https://user-images.githubusercontent.com/59083599/137913938-6fd20824-d2ec-4775-ac5b-335073c48dd5.png)  |  ![b2](https://user-images.githubusercontent.com/59083599/137913959-5f4c5434-9e35-41d4-84d6-15bfe1091291.png)

your tile should surpass all sides of your frame and not be floating inside

good  |  bad
:-------------------------:|:-------------------------:
![g3](https://user-images.githubusercontent.com/59083599/137914443-298a1b51-ba5b-45a6-8f22-c6340ccc647e.png)  |  ![b3](https://user-images.githubusercontent.com/59083599/137914464-69ca09db-5c8f-44e9-bce7-abd2b949478f.png)

and finally your tile should occupy the whole frame and not leave empty spaces 

good  |  bad
:-------------------------:|:-------------------------:
![g4](https://user-images.githubusercontent.com/59083599/137914978-1c33ed74-6712-4821-b6e4-81fe49990fbd.png)  |  ![b4](https://user-images.githubusercontent.com/59083599/137924695-0de7ce17-bebb-464a-9948-4e88fc2ec0e1.png)

note: i added the black background for people who use the github's light theme to be able to easily see, our shape png has to be transparent for the best result

<br>

## using custom tiles
now that we made our custom tiles, taking above explanations into consideration let's use the `gen_tiles.py` program to make other color variants of it.
```
python3 gen_tiles.py tiles/custom/tile1.png
```
this makes a folder named `gen_tile1` in the folder our `tile1.png` is with variations of colors and black to white saturations of our original tile, now lets use this folder to make a tiled picture

![A](https://user-images.githubusercontent.com/59083599/137919877-4f269735-3697-4ea2-bc90-eb016629229e.png)
```
python3 tiler.py snow.jpg tiles/custom/gen_tile1/
```
![snow-tiled](https://user-images.githubusercontent.com/59083599/137917805-21e47039-ee5c-44f5-9153-4aec3fecfc3c.jpg)

lets make another example, this time i make a copy of my tile and turn it 90 degrees to either side to have vertical and horizontal shapes, use `gen_tiles.py` on each of them and put the results into a folder to have combined effect, we could also use the `ROTATIONS = [0]` option in `conf.py` and change it's value to `ROTATIONS = [90]` after we ran it with the default setting to achieve the same result without making duplicate files.

![B](https://user-images.githubusercontent.com/59083599/137919926-30e97115-8aba-47d8-850b-e9545dc5bd21.png) ![C](https://user-images.githubusercontent.com/59083599/137919941-783027e6-1fcb-471b-85f4-5ac5e0abe9a5.png)
```
python3 tiler.py flower.jpg tiles/custom2/gen_tile+/
```
![flower-tiled](https://user-images.githubusercontent.com/59083599/137919484-901b651c-d6d2-496f-95d1-2673cf77a38c.jpg)

<br>

## change resizing scale
so far we've been using the default resizing scale settings of `RESIZING_SCALES = [0.5, 0.4, 0.3, 0.2, 0.1]` scale of 1 is the exact size of our tile image, so with default settings we are using from 50% of the tile size to 10% of it. lets use it again for comparison purposes and then change it:
```
python3 tiler.py burger.jpg tiles/circles/gen_circle_100/
```
default  |  [0.7, 0.6, 0.5, 0.4]   |
:-------------------------:|:-------------------------:
![burger-tiled](https://user-images.githubusercontent.com/59083599/137949566-3dd47348-5e12-42a4-ae5e-05848888f9f5.jpg) | ![burger-tiled-resize](https://user-images.githubusercontent.com/59083599/137949618-2c65032b-8b47-40c0-8708-717a022a51be.jpg)

<br>

## overlap tiles
by default tiles are not set to overlap but this can be change by setting `OVERLAP_TILES = False` to `True`
```
python3 tiler.py tomato.jpg tiles/clips/gen_clip/
```
default  |  with overlap  |
:-------------------------:|:-------------------------:
![tomato-tiled](https://user-images.githubusercontent.com/59083599/137952016-956bf32d-7933-4440-9186-ea05295689fe.jpg) | ![tomato-tiled-overlap](https://user-images.githubusercontent.com/59083599/137952042-87d033ea-83d5-489d-87eb-ce7b3aeb662c.jpg)

<br>

## changing colors
by default every image is rendered with 32 colors `COLOR_DEPTH = 32` lets change that
```
python3 tiler.py colors.jpg tiles/clips/gen_clip/
```
default  |  8 colors  |
:-------------------------:|:-------------------------:
![colors-tiled](https://user-images.githubusercontent.com/59083599/137954796-ed883959-5b78-447b-88eb-a8b523416bcf.jpg) | ![colors-tiled-8colors](https://user-images.githubusercontent.com/59083599/137954818-98b37cba-daa9-40df-8fc3-ed21a145f2a8.jpg)

<br>

## tilify a video
lets apply what we learned to a video, i have made a example of how to download a free video, make image sequence, apply filter and mux it back [here](https://github.com/junguler/ffmpeg-examples/tree/main/sequence%20-%20manipulate%20%26%20mux%20images)
```
for i in *.jpg ; do python3 ~/git-stuff/tiler/tiler.py $i ~/git-stuff/tiler/tiles/waves/gen_wave/ ; mv out.png T-$i.png ; done  
```
because we are not in the folder tiler.py is, we need to pass it's complete path for the shell to know where it is, we should also change the name of output files because the program always outputs images as `out.png` and if we didn't change them they would have been overwritten

and mux the images
```
cat T-image-000*.png | ffmpeg -framerate 30 -f image2pipe -i - -b:v 8M -preset veryslow tiled_dance.mp4
```
https://user-images.githubusercontent.com/59083599/138157868-bd05d629-0d13-4ec9-b0e1-7452cace5c70.mp4

clip was taken from a royalty free video in [odysee](https://odysee.com/@dirtyworkz:0/prdx-phoenix-(official-video)-copyright:e)

we also applied some compression to our video clip `-b:v 8M` to prevent big output sizes and use a very slow preset to preserve as much details as possible `-preset veryslow`

<br>

## make animated gif out of one picture
tiler doesn't have randomization in itself but we can apply rotations to `conf.py` when we use the `gen_tiles.py` to make different rotations of our tiles, lets convert this image with `ROTATIONS = [0]` and convert the image, then do it with `[90]` `[180]` `[270]` and convert the image each time and rename it, note we remove the colored tiles `gen_tiles.py` makes with each conversion but we could have just added the shapes together to make more frames
```
python3 gen_tiles.py tiles/gif/gif.png
```
and convert
```
python3 tiler.py watch.jpg tiles/gif/gen_gif
```
now that we have our 4 images, lets make an animated gif out of it
```
cat 01.png 02.png 03.png 04.png | ffmpeg -framerate 6 -f image2pipe -i - tiled_watch.gif
```
![tiled_watch](https://user-images.githubusercontent.com/59083599/137982799-c09916cd-3dff-448c-a9ac-224d47c886fc.gif)

<br>

## make gif by changing colors
another example of making a gif file is by changing the colors of our input images, lets use ffmpeg's hue filter for this, and iterate thru 360 degrees of hue
```
for h in {10..360..10} ; do ffmpeg -i city.jpg -vf hue=h=$h $h.jpg ; done
```
`{10..360..10}` our starting hue rotation value is 10 and our ending value is 360 because 0 and 360 are the same value, the 10 at the end tells to our shell that skip every 10 numbers and only do, 10, 20, 30 etc to 360, these generated numbers in our for loop are being passed to `hue=h=` which applies the filter and we also use these to generate the output file names, now lets convert our newly generated images

![city+](https://user-images.githubusercontent.com/59083599/138005786-f775dd6b-8e05-4f3f-8ceb-b0d7011a28ed.gif)
```
for i in *.jpg ; do python3 ~/git-stuff/tiler/tiler.py $i ~/git-stuff/tiler/tiles/times/gen_times ; mv out.png T-$i.png ; done 
```
and mux the images to make a gif file
```
cat $( ls -v T-*.png ) | ffmpeg -framerate 10 -f image2pipe -i - tiled_city+.gif
```
because some of our images have two digits and some have 3 digits we use ls with cat because cat by default doesn't sort numerically.

![tiled_city](https://user-images.githubusercontent.com/59083599/138005707-b9349fb4-3c36-4441-a3bb-964ed2a46fd7.gif)

there are many other ways to make an animated gifs in programs like tiler that don't have any randomizations, including rotating the picture converting it and rotting it back, changing resolutions of the pictures, changing shape sizes and pixel_shift and a bunch of other stuff, everything that is considered a change can result in a new output image ...
