## what is needed to get started?
mosaic is a really amazing program that takes you input images and makes roman style mosaics out of them, find the github repo [here](https://github.com/yobeatz/mosaic)
and look [here](https://towardsdatascience.com/how-to-generate-roman-style-mosaics-with-python-11d5aa021b09) for a post to goes in-depth on how the program was designed and works

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

in the we comment out lines [33](https://github.com/yobeatz/mosaic/blob/main/mosaic.py#L33) and [45](https://github.com/yobeatz/mosaic/blob/main/mosaic.py#L45) with # so the program only opens one gui window with our output image

we also change the value of line [96](https://github.com/yobeatz/mosaic/blob/main/mosaic.py#L96) from ``return_svg=False`` to ``return_svg=True`` so the program output and svg file for us on exit

## showing how the program works in a visual way by showing each step an image goes thru
we commented out all of these steps except the final step but it might be a good idea to show them because the program goes thru all of them to make the final output file

original  | edges
:-------------------------:|:-------------------------:
![original](https://user-images.githubusercontent.com/59083599/139756417-88d74dec-c385-40c1-96be-bc5e0f61fcdd.jpg) | ![edges](https://user-images.githubusercontent.com/59083599/139756486-c7ab5cb8-c6e5-4914-bb2e-cdaf4758d317.jpg)
distances | guidelines
![distances](https://user-images.githubusercontent.com/59083599/139756544-172c8a6e-96a0-4803-9ac4-3b77ff0954c9.jpg) | ![guidelines](https://user-images.githubusercontent.com/59083599/139756621-e742efea-9110-4fbe-9a31-a457edbf3035.jpg)
gradient | angles_0to180
![gradient](https://user-images.githubusercontent.com/59083599/139756673-332c1325-7548-451e-b15b-a76ed4386289.jpg) | ![angles_0to180](https://user-images.githubusercontent.com/59083599/139756875-479d0bb9-e321-42c4-a445-a12b8290622c.jpg)
polygons_chains | used_up_space
![polygons_chains](https://user-images.githubusercontent.com/59083599/139756942-598077c7-46da-4647-9266-c9a24c174702.jpg) | ![used_up_space](https://user-images.githubusercontent.com/59083599/139756980-038e8162-07b3-46c7-a8b3-7784d4e9219f.jpg)
distance_to_tile | filler_guidelines
![used_up_space](https://user-images.githubusercontent.com/59083599/139757059-36545cea-25d5-4944-9185-ab1882295f1f.jpg) | ![filler_guidelines](https://user-images.githubusercontent.com/59083599/139757111-704bd4bd-79d1-47da-9c5a-9601a1fc25a4.jpg)
polygons_filler | polygons_cut
![polygons_filler](https://user-images.githubusercontent.com/59083599/139757184-eaa9a2b5-fe46-42de-ba00-cb956ec9e1e6.jpg) | ![polygons_cut](https://user-images.githubusercontent.com/59083599/139757242-8fc8ed37-8d88-411c-bd33-4a1e9d10c7c5.jpg)
final | final_recolored 'fish'
![final](https://user-images.githubusercontent.com/59083599/139757302-d3857b0f-0969-42b8-8eb3-b1acff47c4d8.jpg) | ![final_recolored](https://user-images.githubusercontent.com/59083599/139758088-fd89f475-0b9a-4d89-a4d6-b7d0df0c959b.jpg)

## basic usage
the way the program works is it opens a gui window that lets you change some settings and output an image from it too, we are not interested in re-creating the same effect multiple times so we changed the default settings so the program outputs a svg file for us named 'output.svg' so we close the window as soon as it opens and the output file gets generated, just cd into the folder you have your image on and rename it to `input.jpg`
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
![mos-mountain](https://user-images.githubusercontent.com/59083599/139768165-688e6037-8e89-4ba3-86aa-e131addac028.png)
