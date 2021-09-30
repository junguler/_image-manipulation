## what is needed to get started?
Triangle is a very fast and efficient program that takes your image(s) make cool looking polygonal art out of them. find the github repo 
[here](https://github.com/esimov/triangle).
download the binary executable for you os [here](https://github.com/esimov/triangle/releases) and put it somewhere in your $PATH to be accessable 
from everywhere in the terminal
and lets go.

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/)

## explanation of the switches and how the program works
| Flag | Default | Description |
| --- | --- | --- |
| `in` | n/a | Source image |
| `out` | n/a | Destination image |
| `blur` | 4 | Blur radius |
| `pts` | 2500 | Maximum number of points |
| `noise` | 0 | Noise factor |
| `th` | 20 | Points threshold |
| `sobel` | 10 | Sobel filter threshold |
| `solid` | false | Use solid stroke color (yes/no) |
| `wf` | 0 | Wireframe mode (0: without stroke, 1: with stroke, 2: stroke only) |
| `stroke` | 1 | Stroke width |
| `gray` | false | Output in grayscale mode |
| `web` | false | Open the SVG file in the web browser |
| `bg` | ' ' | Background color (specified as hex value) |
| `c` | system spec. | Number of files to process concurrently (workers)

## basic usage
```
triangle -in thread.jpg -out th.jpg
```
![th](https://user-images.githubusercontent.com/59083599/135362340-03f17cb5-704b-41ff-9ffc-d755afea491c.jpg)

specify point numbers
```
 triangle -in hanger.jpg -out ha.jpg -pts 500
```
![ha](https://user-images.githubusercontent.com/59083599/135362476-5577a3f0-020b-4060-96ac-84625a939e61.jpg)

```
triangle -in lamp.jpg -out la.jpg -pts 1000
```
![la](https://user-images.githubusercontent.com/59083599/135362572-31506188-c9a6-458e-9627-b8777302a1a2.jpg)

## with strokes
for adding strokes we need 2 flags, first is `-wf` which is set to 0 by default which is without stroke so set it to 1 for having strokes, and `-stroke` for specifing how think the stroke must be.
```
triangle -in chair.jpg -out ch.jpg -pts 1000 -wf 1 -stroke 3
```
![ch](https://user-images.githubusercontent.com/59083599/135362924-e5cd542a-e4e1-4ad4-a0ca-ea21e763aab8.jpg)

```
triangle -in keys.jpg -out ke.jpg -pts 3000 -wf 1 -stroke 1
```
![ke](https://user-images.githubusercontent.com/59083599/135363060-e553049a-31f4-4286-809e-082c1711ce29.jpg)

## strokes only
same as above but this time we set `-wf` to 2 for stroke only and also make the stroke lines bigger to make it easier to make out the image
```
triangle -in cd.jpg -out cd+.jpg -pts 1000 -wf 2 -stroke 10
```
![cd+](https://user-images.githubusercontent.com/59083599/135363494-9fbecb92-cece-4b42-9c54-af8b0b77e10a.jpg)

```
triangle -in sunglasses.jpg -out su.jpg -pts 2000 -wf 2 -stroke 15
```
![su](https://user-images.githubusercontent.com/59083599/135363732-c878a882-b3d0-47d4-88fc-f025cb298e41.jpg)

## blur
the higher the blur value the more washed out the polygons will look but the overal image is easier to make out
```
triangle -in licenceP.jpg -out lp-1b.jpg -pts 1000 -blur 1
```
![lp-1b](https://user-images.githubusercontent.com/59083599/135364392-8f6fe809-01d0-4cc1-a449-ad7f7ce19a82.jpg)
```
triangle -in licenceP.jpg -out lp-10b.jpg -pts 1000 -blur 10
```
![lp-10b](https://user-images.githubusercontent.com/59083599/135364460-e779b927-49b4-471c-bbe3-e24141d6f85a.jpg)
```
triangle -in licenceP.jpg -out lp-25b.jpg -pts 1000 -blur 25
```
![lp-25b](https://user-images.githubusercontent.com/59083599/135364469-68c036e4-4ab8-4adc-ba16-9504b4605f53.jpg)

## sobel filter
the higher the value the less detail the image have
```
triangle -in clamp.jpg -out cl-s50.jpg -pts 1000 -sobel 50
```
![cl-s50](https://user-images.githubusercontent.com/59083599/135364805-547eda35-6a79-49f2-8d02-0565e5799ff8.jpg)
```
triangle -in clamp.jpg -out cl-s250.jpg -pts 1000 -sobel 250
```
![cl-s250](https://user-images.githubusercontent.com/59083599/135364821-f2fbe148-c10a-447f-9b35-3188016f4ed2.jpg)

## points threshold
less is more polygonal and trianglated, more is longer and more uniform
```
triangle -in pen.jpg -out pe-t1.jpg -pts 1000 -th 1
```
![pe-t1](https://user-images.githubusercontent.com/59083599/135365066-a0f58ca3-eeaf-4108-ab23-45ae4555b4d9.jpg)
```
triangle -in pen.jpg -out pe-t100.jpg -pts 1000 -th 100
```
![pe-t100](https://user-images.githubusercontent.com/59083599/135365075-e8529674-c8fe-4634-b891-e077909eda7f.jpg)

## noise
```
triangle -in socks.jpg -out so-n100.jpg -pts 500 -noise 50
```
![so-n100](https://user-images.githubusercontent.com/59083599/135365320-77ee675b-a319-4599-96e4-78b77daf8ecc.jpg)

## gifs|videos, iterate over an image with the same settings multiple times
```
for t in {01..10} ; do echo $t ; triangle -in button.jpg -out b-$t.jpg -pts 750 ; done
```
and mux the images
```
cat b-*.jpg | ffmpeg -framerate 8 -f image2pipe -i - button.mp4
```
https://user-images.githubusercontent.com/59083599/135365795-7aa35cbb-5b38-4a91-b6cf-79759e128f81.mp4

## iterate over an image with progressing shape numbers
lets convert this image 100 times, starting with 1 shape and then 6 and 11 and 16 etc to get to 500 shapes in the 100th picture ...
```
for t in {001..500..5} ; do echo $t ; triangle -in headphones.jpg -out h-$t.jpg -pts $t ; done
```
and mux the images
```
cat h-*.jpg | ffmpeg -framerate 15 -f image2pipe -i - headset.mp4
```
https://user-images.githubusercontent.com/59083599/135366867-92af9368-7f0b-4b42-a85c-694e5876ef0f.mp4
