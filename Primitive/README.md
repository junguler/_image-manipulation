## what is needed to get started?
Primitive is a cli program that takes your input image(s) make cool looking art with them using basic shapes, find the github page [here](https://github.com/fogleman/primitive), 
primitive does not come with a binary executable by default, you can either install golang and compile it yourself or download the binary version of windows or linux from my repo [here](https://github.com/junguler/easy-primitive-batch)

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/)

## explainiation of the switches and how the program works
`-i` imports your source image

`-o` specifies output image

`-n` number of shapes generated for each image, more produced more clear image but is slower

`-m` decides the which shape is used for each images: 0=combo, 1=triangle, 2=rect, 3=ellipse, 4=circle, 5=rotatedrect, 6=beziers, 7=rotatedellipse, 8=polygon . use the number only, for example 1 for triangle

`-r` resizes your input image to 256 pixel by default to make the converting process faster pass 0 to it to skip this process

`-s` decides the width of outpot size, if don't passed it outputs at 1024 pixels witdh

`-bg` decides the background color, use a hex value, default is average

`-v` to see verbose log of what's happening

## combo examples
```
primitive -i cheetah.jpg -o c_0.jpg -n 1000 -m 0 -s 1280 -v
```
![c_0](https://user-images.githubusercontent.com/59083599/134971033-2042574c-545c-452b-b3f4-19592dec42af.jpg)

