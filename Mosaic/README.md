## what is needed to get started?
mosaic is a really amazing program that takes you input images and makes roman style mosaics out of them, find the github repo [here](https://github.com/yobeatz/mosaic)
and look [here](https://towardsdatascience.com/how-to-generate-roman-style-mosaics-with-python-11d5aa021b09) for a post to goes in-depth on how the program was designed and works

### quick links
 * [how it works](https://github.com/junguler/_image-manipulation/tree/main/Mosaic#showing-how-the-program-works-in-a-visual-way-by-showing-each-step-an-image-goes-thru)
 * [basic usage](https://github.com/junguler/_image-manipulation/tree/main/Mosaic#basic-usage)
 * [change tile size](https://github.com/junguler/_image-manipulation/tree/main/Mosaic#change-tile-size)
 * [respect frame of the image](https://github.com/junguler/_image-manipulation/tree/main/Mosaic#respecting-frame-of-the-image)
 * [change tile angles](https://github.com/junguler/_image-manipulation/tree/main/Mosaic#changing-tile-angles)
 * [randomize tile placement](https://github.com/junguler/_image-manipulation/tree/main/Mosaic#randomize-tile-placement)
 * [change edge detection mode](https://github.com/junguler/_image-manipulation/tree/main/Mosaic#change-edge-detection-mode)
 * [mosaicify a video](https://github.com/junguler/_image-manipulation/tree/main/Mosaic#mosaicify-a-video)

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and some royalty free stock footage from youtube

## explanation of the config and how the program works
customizing config is done by changing values in the `mosaic.py` file so we will make a copy of the original file to have an offline copy to be able to compare configs if there is need for it

| config | default | description |
| --- | --- | --- |
| half_tile | 12 | half size of mosaic tile, between 4 and 30 |
| GAUSS | 3 | blurs image before edge detection, between 0 and 8 |
| EDGE_DETECTION | 'HED' | the method for edge detection, either 'HED' or 'DiBlasi' |
| WITH_FRAME | True | control about guidelines along image borders, either True or False |
| RAND_SIZE | 0.3 | portion of tile size which is added or removed randomly during construction |
| MAX_ANGLE | 40 | max construction angle for tiles along roundings, between 30 and 75 |
| GAP_CHAIN_SPACING | 0.5 | spacing of gap filler chains, between 0.4 and 1.0 |
| MAKE_CONVEX | True | break concave into more realistic polygons, either True or False |
| COLOR_SCHEMA | ['nilotic',] | leave empty to plot all available or choose from 'wise_men', 'fish', 'cave_canem', 'nilotic', 'rooster', 'carpe_diem', 'Hyena' |

in the line [15](https://github.com/yobeatz/mosaic/blob/main/mosaic.py#L15) of the 'mosaic.py' there is a line that decides the name of our input image,
lets change it to ``fname = r'input.jpg'`` so we have a unified way of inputing our image to the program

and we comment out lines [33](https://github.com/yobeatz/mosaic/blob/main/mosaic.py#L33) and [45](https://github.com/yobeatz/mosaic/blob/main/mosaic.py#L45) with # so the program only opens one gui window with our output image

we also change the value of line [96](https://github.com/yobeatz/mosaic/blob/main/mosaic.py#L96) from ``return_svg=False`` to ``return_svg=True`` so the program outputs an svg file for us on exit

## showing how the program works in a visual way by showing each step an image goes thru
we commented out all of these steps except the final step but it might be a good idea to show them because the program goes thru all of them to make the final output file

step_1 original  | step_2 edges
:-------------------------:|:-------------------------:
![original](https://user-images.githubusercontent.com/59083599/139756417-88d74dec-c385-40c1-96be-bc5e0f61fcdd.jpg) | ![edges](https://user-images.githubusercontent.com/59083599/139756486-c7ab5cb8-c6e5-4914-bb2e-cdaf4758d317.jpg)
step_3 distances | step_4 guidelines
![distances](https://user-images.githubusercontent.com/59083599/139756544-172c8a6e-96a0-4803-9ac4-3b77ff0954c9.jpg) | ![guidelines](https://user-images.githubusercontent.com/59083599/139756621-e742efea-9110-4fbe-9a31-a457edbf3035.jpg)
step_5 gradient | step_6 angles_0to180
![gradient](https://user-images.githubusercontent.com/59083599/139756673-332c1325-7548-451e-b15b-a76ed4386289.jpg) | ![angles_0to180](https://user-images.githubusercontent.com/59083599/139756875-479d0bb9-e321-42c4-a445-a12b8290622c.jpg)
step_7 polygons_chains | step_8 used_up_space
![polygons_chains](https://user-images.githubusercontent.com/59083599/139756942-598077c7-46da-4647-9266-c9a24c174702.jpg) | ![used_up_space](https://user-images.githubusercontent.com/59083599/139756980-038e8162-07b3-46c7-a8b3-7784d4e9219f.jpg)
step_9 distance_to_tile | step_10 filler_guidelines
![distance_to_tile](https://user-images.githubusercontent.com/59083599/139779737-fcdce48e-c083-406d-a534-4425119ea49e.jpg) | ![filler_guidelines](https://user-images.githubusercontent.com/59083599/139757111-704bd4bd-79d1-47da-9c5a-9601a1fc25a4.jpg)
step_11 polygons_filler | step_12 polygons_cut
![polygons_filler](https://user-images.githubusercontent.com/59083599/139757184-eaa9a2b5-fe46-42de-ba00-cb956ec9e1e6.jpg) | ![polygons_cut](https://user-images.githubusercontent.com/59083599/139757242-8fc8ed37-8d88-411c-bd33-4a1e9d10c7c5.jpg)
step_13 final | step_14 final_recolored 'fish'
![final](https://user-images.githubusercontent.com/59083599/139757302-d3857b0f-0969-42b8-8eb3-b1acff47c4d8.jpg) | ![final_recolored](https://user-images.githubusercontent.com/59083599/139758088-fd89f475-0b9a-4d89-a4d6-b7d0df0c959b.jpg)

## basic usage
the way the program works is it opens a gui window that lets you change some settings and output an image from it too, we are mostly interested in re-creating the same effect multiple times so we changed the default settings so the program outputs a svg file for us named 'output.svg' so we close the window as soon as it opens and the output file gets generated, just cd into the folder you have your image on and rename it to `input.jpg` and run the program
```
python3 ~/git-stuff/mosaic/mosaic.py
```
because we are on a different folder than `mosaic.py` is we need to pass it's full path to our shell, now convert the svg file to png specifing it's width to be 1280 pixels for this example
```
ffmpeg -i output.svg -vf scale=1280:-1 mos-eiffel.png
```
![mos-eiffel](https://user-images.githubusercontent.com/59083599/139759167-605d88fe-7305-4d90-ba4f-6c2b8ae91fa0.png)

another example

![mos-baloon](https://user-images.githubusercontent.com/59083599/139759442-5002def3-1dac-4fc2-950a-e8e140825331.png)

## change tile size
so far we've been using the default size of 12 for tile sizes, lets use a smaller size of 6 for this, change the value in the `mosaic.py` to ``half_tile = 6``

![mos-road](https://user-images.githubusercontent.com/59083599/139760213-f701610c-8120-4246-b71b-66bf9690ea87.png)

now with 4 which is te lowest value possible, this takes quite a bit longer to make too since the program seems to be only using one core of my cpu

![mos-mime](https://user-images.githubusercontent.com/59083599/139763287-0a0abbbe-f023-435d-9a87-cba78f04392f.png)

note because our image is vertical we change our ffmpeg command to set for 720 pixels for it's height
```
ffmpeg -i output.svg -vf scale=-1:720 mos-mime.png
```
setting the number higher than the default 12 (16 for this example) we use an image that can afford to lose most of it's details and still be recognizable

![mos-fire](https://user-images.githubusercontent.com/59083599/139851339-5031d4c9-fda0-4657-a73a-04c1628c6bcb.jpg)

comparing different tile sizes with the same image

original  | half_tile = 6 
:-------------------------:|:-------------------------:
![original](https://user-images.githubusercontent.com/59083599/139945917-6a6de556-6044-4bb8-b31a-84b916fa7c66.jpg) | ![wm-6](https://user-images.githubusercontent.com/59083599/139945953-c6d76750-8ada-45ac-bd02-4d08911321bb.jpg) 
half_tile = 12 | half_tile = 20
![wm-12](https://user-images.githubusercontent.com/59083599/139946050-7b5f7b37-d3fa-43cd-a2ed-6f4481e5aada.jpg) | ![wm-20](https://user-images.githubusercontent.com/59083599/139946110-35821dff-1bbc-420d-bab1-1e35282d6ff7.jpg)

## respecting frame of the image
by default mosaic aligns the tiles starting at the edges of the screen and then comes to the middle, if we set this option to false the tiles are aligned at the border of the objects inside our image, let's show both side by side

WITH_FRAME = True | WITH_FRAME = False
:-------------------------:|:-------------------------:
![moon-frame](https://user-images.githubusercontent.com/59083599/139770158-df4024b0-3855-4ff8-8fbe-68693ea1d22d.png) | ![moon-no-frame](https://user-images.githubusercontent.com/59083599/139770247-2f1621e9-cd3e-4276-9b04-d1da3b3d8707.png)

## changing tile angles
set the maximum degree a tile is able to rotate to create the image (default value is 40), higher value produces smoother image with less tiles

MAX_ANGLE = 30 | MAX_ANGLE = 75
:-------------------------:|:-------------------------:
![30](https://user-images.githubusercontent.com/59083599/139771255-7f62209d-b3bd-4d65-a514-240c196ad87e.png) | ![75](https://user-images.githubusercontent.com/59083599/139771290-7d48c002-b17c-4b8d-94bc-435a75d199d9.png)

## randomize tile placement
by default mosaic applies ``RAND_SIZE = 0.3`` randomization to placement of tiles, lets change that for comparison
RAND_SIZE = 0.3 | RAND_SIZE = 3.0
:-------------------------:|:-------------------------:
![random-0-3](https://user-images.githubusercontent.com/59083599/139958096-e9e584b9-1151-4b78-a63c-fb110351e675.png) | ![random-3-0](https://user-images.githubusercontent.com/59083599/139958637-a304125a-4e8d-4932-8954-ba157ba604ff.png)

## change edge detection mode
the default edge detection method mosaic uses is HED but there is an alternative called DiBlasi, here is how they look compared to each other

EDGE_DETECTION = 'HED' | EDGE_DETECTION = 'DiBlasi'
:-------------------------:|:-------------------------:
![HED](https://user-images.githubusercontent.com/59083599/139771969-e49c3741-7f71-4001-a4ee-5e00c0e1c1c5.png) | ![DiBlasi](https://user-images.githubusercontent.com/59083599/139771984-e2c8834d-fd99-4bd6-98f3-1faf78695f2c.png)

## recoloring our output image
mosaic is able to apply recoloring to our converted images, lets showcase them with a colorful image

normal | 
:-------------------------:|
![t-nomal_colors](https://user-images.githubusercontent.com/59083599/139965688-ae01fa75-6d7d-45a0-8319-d1bb11af0eed.jpeg) |
wise_men | 
![t-wise_man](https://user-images.githubusercontent.com/59083599/139965722-ff63f22b-89ef-48ac-95b9-a191e0ae5441.jpeg) |
fish | 
![t-fish](https://user-images.githubusercontent.com/59083599/139965808-627653c5-35df-4fda-b3ff-aab8e4d54a51.jpeg) |
cave_canem | 
![t-cave_canem](https://user-images.githubusercontent.com/59083599/139965838-8d33d3dc-6103-45cc-971a-abdce5529a1d.jpeg) |
nilotic | 
![t-nilotic](https://user-images.githubusercontent.com/59083599/139965859-1cb7d13e-f737-4377-be40-b23d41c35683.jpeg) |
rooster |
![t-rooster](https://user-images.githubusercontent.com/59083599/139965890-2faa4e40-4294-4731-8608-3b144f29bdab.jpeg) |
carpe_diem |
![t-carpe_diem](https://user-images.githubusercontent.com/59083599/139965937-12ef191c-2f1c-4536-98ad-e433e198ca8a.jpeg) |
Hyena |
![t-Hyena](https://user-images.githubusercontent.com/59083599/139965967-cdd7f058-005e-415f-9b3e-d836e233a49a.jpeg) |

## mosaicify a video
lets apply what we learned to a video, i have made a example of how to download a free video, make image sequence, apply filter and mux it back [here](https://github.com/junguler/ffmpeg-examples/tree/main/sequence%2C%20manipulate%20%26%20mux%20images)
```
for i in *.jpg ; do cp $i input.jpg ; python3 ~/git-stuff/mosaic/mosaic.py ; rm input.jpg ; mv output.svg $i.svg ; done 
```
first we assign every jpg file to our for loop, duplicate them one by one and name them input.jpg, convert the image using mosaic and remove the duplicated file and finally rename output.svg to the same name as our initial input so it's not overwritten by the next output file. note that you have to manually close the gui window each time as i don't know enough python to make this automatic

now that we have our image sequemce converted and in svg format lets convert it to png setting it's width to 1280 pixels
```
for i in *.svg ; do ffmpeg -i $i -vf scale=1280:-1 o-$i.png ; done 
```
and convert to a video
```
cat o-*.png | ffmpeg -framerate 20 -f image2pipe -i - mosaic-liberty.mp4
```
https://user-images.githubusercontent.com/59083599/139774925-d6aff776-6e83-485f-b6fb-76d069b7aff4.mp4
