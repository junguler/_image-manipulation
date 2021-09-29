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
