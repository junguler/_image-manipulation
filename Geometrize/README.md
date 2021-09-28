## what is needed to get started?
Geometrize is a cli and gui program that takes your input image(s) make cool looking art with them using basic shapes, find the github page [here](https://github.com/Tw1ddle/geometrize) for gui, [here](https://github.com/Tw1ddle/geometrize-lib-example) for cli,
unlike primitive geometrize come with a binary executable for cli and gui out of the box, find them [here](https://www.geometrize.co.uk/) for gui and [here](https://s3.amazonaws.com/geometrize-lib-example-bucket/index.html) for the cli

## what are the differences betwwen primitives and geometrize?
from the first look these two programs might look familiar but there are enough differences to not consider geometrize just a re-write and i'll try to point some of them here
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

## quadratic bezier example
```
geometrize -i apple.jpg -o a-qb.jpg -s 5000 -t quadratic_bezier
```
![a-qb](https://user-images.githubusercontent.com/59083599/135091234-c41a5ecd-2d33-4f36-a104-af89f0fe1e2b.jpg)

## polyline example
```
geometrize -i kiwi.jpg -o k-pl.jpg -s 2500 -t polyline
```
![k-pl](https://user-images.githubusercontent.com/59083599/135092055-95c4754f-417c-4d4a-b80e-3e092c727b6d.jpg)

## line example
```
geometrize -i clementine.jpg -o c-li.jpg -s 3750 -t line
```
![c-li](https://user-images.githubusercontent.com/59083599/135092968-2308b55e-2d43-4412-ad21-02226b529e17.jpg)

if you found these files are outputed at a very large sizes, just pass them once thru ffmpeg to compress them
```
ffmpeg -i c-li.jpg c-li2.jpg
```
a 1.5 mb image became 500 kb with hardly any noticable artifcating

## combining 2 different shapes
```
geometrize -i peach.jpg -o p-2.jpg -s 250 -t "triangle rotated_rectangle"
```
![p-2](https://user-images.githubusercontent.com/59083599/135086245-b4cd5369-aee3-47df-ae5c-3e229d86b955.jpg)

```
geometrize -i grapes.jpg -o g-2.jpg -s 500 -t "circle ellipse"
```
![g-2](https://user-images.githubusercontent.com/59083599/135086855-e3032566-5ca2-497b-8111-f201cb3577c7.jpg)

```
geometrize -i banana.jpg -o b-2.jpg -s 750 -t "rectangle triangle"
```
![b-2](https://user-images.githubusercontent.com/59083599/135089254-79fae2bf-3f4a-46b3-9097-75072a5f8027.jpg)

## combining 3 or more different shapes
```
geometrize -i watermelon.jpg -o w-3+.jpg -s 750 -t "rectangle circle triangle"
```
![w-3+](https://user-images.githubusercontent.com/59083599/135094343-98b5832b-8d6f-4fdb-a783-0c7b3de616fa.jpg)

```
geometrize -i pineapple.jpg -o p-3+.jpg -s 500 -t "rotated_rectangle polyline rotated_ellipse"
```
![p-3+](https://user-images.githubusercontent.com/59083599/135094748-8e94eeb6-a81f-4cbc-93f2-7ee121048582.jpg)

```
geometrize -i fig.jpg -o f-3+.jpg -s 1000 -t "triangle polyline line quadratic_bezier"
```
![f-3+](https://user-images.githubusercontent.com/59083599/135095727-2421c9e7-840f-459c-a8c4-54c62b3a849f.jpg)

## fun with gifs
unlike primitives, geometrize does not randomize each conversion which is a pickle for gif makers when working with a single image, not to worry tho as i have my own tricks up my sleeps. an image that is rotated 1 degree or even less to it's either side is seen as a completely different image by geometrize, here i made 2 extra copy of my image and rotated one to -1 degree and the other to +1 degree and made a gif
```
cat *.jpg | ffmpeg -framerate 5 -f image2pipe -i - mango.gif
```
![mango](https://user-images.githubusercontent.com/59083599/135105843-58cb55e3-6095-4051-96f7-a0947b885a37.gif)
