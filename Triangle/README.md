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
triangle -in sunglasses.jpg -out su.jpg -pts 1000 -wf 2 -stroke 15
```
![su](https://user-images.githubusercontent.com/59083599/135363580-2ccbd7a8-1d6a-4df3-a5e8-f5a2fe63cb9e.jpg)
