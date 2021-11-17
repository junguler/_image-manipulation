## what is needed to get started?
G'mic is a massive collection of image processing filters combined to a one easy to use gui and cli program that can be installed on gimp, krita etc ... or used on the terminal, it's so big even when i made a markdown specific for showing it with many examples i barely scracthed the surface of what it does and i'm going to showcase one of it's filters here

for the basics of how to use the program look here , now that you are somewhat familier with this program lets do our thing

stylize is a cool filter to applying style transfer to our images, it's the most easy to use and un-complicated implementation of style transfer i have seen that runs localy on your computer without the need for internet or installing extra programs like python, lua or others

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and [here](https://www.rawpixel.com/free-images), there is also some royalty free stock footage from youtube

## explanation of the config and how the program works
| basic | advanced | 
| --- | --- |
| ![basic](https://user-images.githubusercontent.com/59083599/142251747-87337ed0-7a59-4461-addb-bcc2de4bfbed.png) | ![advanced](https://user-images.githubusercontent.com/59083599/142251780-644e1b0a-aa69-4109-b949-4ff65153533f.png) |

the default options in the gui translates to this command in the cli by clicking on the copy command icon on the top right side of the gui
```
fx_stylize 0,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0
```
add a gmic behind the command, specify your input image and output image, styles has a few images embedded into it if you don't want to set an style image

```
gmic input.jpg fx_stylize 2,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o output.jpg
```
the 2 after fx_stylize tells gmic to use the 3rd option in the first gui entry which is the first embedded image style, by default 0 is used which uses the first image as our style so if we want to specify our own style we set that number to 0 and insert 2 images to gmic
```
gmic style.jpg input.jpg fx_stylize 0,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o output.jpg
```

## basic usage (suing built-in styles)
we'll start we some pre-embeded images as styles, this is easiest way to use the filter
```
gmic earth.jpg fx_stylize 32,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o earth_gogh+.jpg
```
| input | style (Picasso: Seated Woman) |  output | 
| --- | --- | --- |
| ![earth](https://user-images.githubusercontent.com/59083599/142257831-d3b92d15-a48b-4236-bc98-b105fad1c71d.jpg) | ![seated-woman](https://user-images.githubusercontent.com/59083599/142258697-e29dc7a4-b063-49ae-8633-aa46ce92ffdd.jpg) | ![earth_gogh1+](https://user-images.githubusercontent.com/59083599/142258296-d0c19057-268a-4b55-aeee-7848abde5fd8.jpg) |

```
gmic statue.jpg fx_stylize 25,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o statue_mondrian+.jpg
```
| input | style (Mondrian: Gray Tree) |  output | 
| --- | --- | --- |
| ![statue](https://user-images.githubusercontent.com/59083599/142259582-c6ac9d8d-4c38-42cd-9c44-22e674addb2b.jpg) | ![gray-tree](https://user-images.githubusercontent.com/59083599/142259637-6a8cdc2d-5580-440c-a3e1-686f23854731.jpg) | ![statue_mondrian+](https://user-images.githubusercontent.com/59083599/142259678-3f184ae3-b7d2-42a4-9e84-53d76bd138b7.jpg) |




