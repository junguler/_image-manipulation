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

# showing how the program works in a visual way by showing each step an image goes thru
