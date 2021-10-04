## what is needed to get started?
Triangula is a gui and cli program that takes your image(s) make cool looking triangular and polygonal art out of them. find the github repo [here for gui](https://github.com/RH12503/triangula) and [here for cli](https://github.com/RH12503/Triangula-CLI) the cli version does not come pre-comiled and you have to install golang and compile it yourself, i'll include the linux binary i've made for myself in this repo and if you have a macos or windows binary contact me to include it as well, i also started an issue in the cli repo and we might get and official build as well

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/)

## gui version
there is a gui version available with simplified usage [here](https://github.com/RH12503/triangula/releases/tag/v1.2.0) while perfectly usable i'm more interested in the cli version as we want to be able to re-produce same types of results automatically and batch convert them

![T_gui](https://user-images.githubusercontent.com/59083599/135850973-abd1274e-92f4-46f1-99cd-2a503739b552.jpg)

## explanation of the switches and how the program works
triangula cli is made of two seperate sub commands, first one is `run` which takes your image and makes a json file out of the information inside it, this is the main step we are interested in, here are the switches for it

| Flag | Default | Description |
| --- | --- | --- |
| `--img`,  `--image` | n/a | the image file to triangulate |
| `--out`,  `--output` | n/a | the file to write output to |
| `-p`,  `--points` | 300 | the number of points to use in the triangulation |
| `-s`,  `--shape` | "triangles" | the type of shape to use, either triangles or polygons |
| `-m`,  `--mut`, `--mutations` | 2 | the number of mutations to make |
| `-v`,  `--variation` | 0.3 | the variation each mutation causes |
| `--pop`,  `--size`, `--population` | 400 | the population size in the algorithm |
| `-c`,  `--cache` | 22 | the cache size as a power of 2 |
| `-b`,  `--block` | 5 | the size of the blocks used when rendering |
| `--cut`,  `--cutoff` | 5 | the size of the blocks used when rendering |
| `-r`,  `--reps` | 500 | the number of generations before saving to the output file |
| `-t`,  `--threads` | 0 | the number of threads to use or 0 to use all cores |

second step is `render` which takes the input image and applies the information from the json file to it and convert it to an svg or png picture, here are the switches for that

| Flag | Description |
| --- | --- |
| `-i`,  `--in`,  `--input` | the .json file containing the points to be rendered |
| `-o`,  `--out`,  `--output` | the name of the file to be outputted |
| `--img`,  `--image`| the image to use |
| `-s`,  `--shape`| the type of shape to use, either triangles or polygons (default: "triangles") |

## basic usage
```
triangula run -img bottle.jpg -out b.json
```
this process will go on forever, there is no end point which exists and we have to intruppt it manually with `ctrl+c`, by default every 500 generations (which are calculations triangula makes) saves the information to the json file

![run+](https://user-images.githubusercontent.com/59083599/135856002-baa8d9ae-5ab9-4663-90cb-ff09a78860e9.jpg)

we can automate this with the `timeout` command, we just specify how long we want this command to last, let do it for 20 seconds
```
timeout 20s triangula run -img bottle.jpg -out b.json
```
now render the image to png with render command
```
triangula render -in b.json -out T-bottle -img bottle.jpg png 
```
![bottle](https://user-images.githubusercontent.com/59083599/135856516-71402ea8-1d2f-45d1-ac68-7ab12fe96890.png)

notice that we didn't specify extension for our outpot image T-bottle as the program adds that automatically

here is a one liner of our two command, we also remove the json file as we don't need it anymore
```
timeout 20s triangula run -img bottle.jpg -out b.json ; triangula render -in b.json -out bottle -img bottle.jpg png ; rm b.json
```
