## what is needed to get started?
Geometrize is a cli and gui program that takes your input image(s) make cool looking art with them using basic shapes, find the github page [here](https://github.com/Tw1ddle/geometrize) for gui, [here](https://github.com/Tw1ddle/geometrize-lib-example) for cli,
unlike primitive geometrize come with a binary executable for cli and gui out of the box, find them [here](https://www.geometrize.co.uk/) for gui and [here](https://s3.amazonaws.com/geometrize-lib-example-bucket/index.html) for the cli

## what are the differences betwwen primitives and geometrize?
from the first look these two programs might look familiar but there are enough differences to not consider geometrize just a re-write and i'll try to point some of thme here
 * geometrize was inspired by primitives
 * geometrize was written in C and C++ bht primitives was written in golang
 * geometerize comes with gui and cli version for windows, linux and ios but primitves only has a gui version for ios (it's multiplatform on the cli)
 * geometrize allows you to combine different shapes together but primitives does not, it has a combo mode for using all available shapes tho
 * geometrize gives you more control for opacity of each shape and number of candidate shapes to go thru before deciding a shape, it's more accurate but slower than primitives 

since there are similarities between the two programs i try to focus on the difference geometrize has to primitives and focus more on combining different shapes and only show new things geometrize has

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/)

## explainiation of the switches and how the program works
`-i` imports your source image

`-o` specifies output image

`-t` the types of shapes to use, multiple shapes are usable: rectangle, rotated_rectangle, triangle, ellipse, rotated_ellipse, circle, line, quadratic_bezier, polyline

`-s` number of shapes generated for each image, more produces more clear image but its slower, default value is 250

`-c` number of candidate shapes per shape added to the output image, default is 50

`-m` maximum number of times to mutate each candidate shape, default is 100

`-a` The opacity (0-255) of each shape added to the output image, default is 128 for half opacity, 255 for full opacity

## using 2 different shapes
```
geometrize -i peach.jpg -o p-2.jpg -s "250" -t "triangle rotated_rectangle"
```
![p-2](https://user-images.githubusercontent.com/59083599/135086245-b4cd5369-aee3-47df-ae5c-3e229d86b955.jpg)
