## what is needed to get started?
Triangula is a gui and cli program that takes your image(s) make cool looking triangular and polygonal art out of them. find the github repo [here for gui](https://github.com/RH12503/triangula) and [here for cli](https://github.com/RH12503/Triangula-CLI) the cli version does not come pre-compiled and you have to install golang and compile it yourself, i'll include the linux binary i've made for myself in this repo and if you have a macos or windows binary contact me to include it as well, i also started an issue in the cli repo and we might get and official build as well
 
### quick links
 * [basic usage](https://github.com/junguler/_image-manipulation/tree/main/Triangula#basic-usage)
 * [for loop](https://github.com/junguler/_image-manipulation/tree/main/Triangula#for-loop)
 * [batch converting](https://github.com/junguler/_image-manipulation/tree/main/Triangula#batch-converting)
 * [shape counts](https://github.com/junguler/_image-manipulation/tree/main/Triangula#change-pointsshape-numbers)
 * [polygons](https://github.com/junguler/_image-manipulation/tree/main/Triangula#use-polygans-instead-of-triangles)
 * [iterate an image to make gif](https://github.com/junguler/_image-manipulation/tree/main/Triangula#making-a-animated-gif-out-of-an-still-image)
 * [triangulafy a video](https://github.com/junguler/_image-manipulation/tree/main/Triangula#triangulafy-a-video)
 * [glitch it](https://github.com/junguler/_image-manipulation/tree/main/Triangula#glitch-it)

## what are the differences betwwen triangula and triangle?
these two programs look somewhat the same in first glance but there are enough difference to warrent both existing and we using them both in different cases, here are some of them:
 * triangula tries to produce a more uniformed look with triangle sizes roughly the same size
 * triangula does not overlap these triangles and only push them to different directions
 * triangula wants to more closely recreate the image which makes it very slower than triangle
 * triangula comes with gui option in addition to cli but triangle does not
 * triangula has a two step process for recreating the image but triangle does it in 1 step
 * triangula outpot images that more closely resemble low poly art we see in pop culture
 * triangula's outpots are more cleaner and need less points to be able to make out the image

triangula also gets compared to other programs like primitive and geometrize but i think this comparison is not valid as these programs are not meant to be used for the same purposes

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
this process will go on forever, there is no end point which exits and we have to intrupt it manually with `ctrl + c`, by default every 500 generations (which are calculations triangula makes) saves the information to the json file

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

notice that we didn't specify extension for our outpot image `T-bottle` as the program adds that automatically

here is a one liner of our two commands, lets also remove the json file as we don't need it anymore
```
timeout 20s triangula run -img bottle.jpg -out b.json ; triangula render -in b.json -out bottle -img bottle.jpg png ; rm b.json
```

## for loop
it might get a little annoying having to fill the names every time so we will use a for loop that does it for us
```
for d in knife2.jpg ; do timeout 25s triangula run -img $d -out j.json ; triangula render -in j.json -out T-${d%%.*} -img $d png ; rm j.json ; done
```
![T-knife2](https://user-images.githubusercontent.com/59083599/135857650-5c00a567-3d1e-43ab-ab05-36f286107611.png)

we applied the name of our input image with the for loop as it was the only image we wanted to convert, since we have an image with `.jpg` extension and triangula automatically insert png extension to our image name we use `${d%%.*}` to remove the file extension in the render part and we add a `T-` before it to differentiate the input and outpot images

## batch converting
lets convert all of the images in our folder with a one liner
```
for d in *.jpg ; do timeout 25s triangula run -img $d -out j.json ; triangula render -in j.json -out T-${d%%.*} -img $d png ; rm j.json ; done
```
![T-biker](https://user-images.githubusercontent.com/59083599/135858663-f03fbfc6-338a-4d76-9f44-7eb855f700bc.png)

![T-clayP](https://user-images.githubusercontent.com/59083599/135858852-09cb9ff3-ee85-40c0-bb53-dde17caa8b27.png)

![T-stop](https://user-images.githubusercontent.com/59083599/135858902-cf29ac88-70e3-4ac3-9170-ec038266df5b.png)

![T-umbrella](https://user-images.githubusercontent.com/59083599/135858951-dec0df65-6aac-4ea0-a454-cf391022fe96.png)

## change points/shape numbers
so far we have been using the default settings, lets change that, we will use `-p` switch for this
```
for d in piratesF.jpg ; do timeout 25s triangula run -img $d -out j.json -p 250 ; triangula render -in j.json -out T-${d%%.*} -img $d png ; rm j.json ; done
```
![T-piratesF](https://user-images.githubusercontent.com/59083599/135860752-d48bbd75-0a7c-4611-815f-5a1ab017dafa.png)

```
for d in match.jpg ; do timeout 25s triangula run -img $d -out j.json -p 1000 ; triangula render -in j.json -out T-${d%%.*} -img $d png ; rm j.json ; done
```
![T-match](https://user-images.githubusercontent.com/59083599/135861284-46255a7a-9587-45b5-aaaf-7c789e6f8ad8.png)

```
for d in telephone.jpg ; do timeout 60s triangula run -img $d -out j.json -p 2500 ; triangula render -in j.json -out T-${d%%.*} -img $d png ; rm j.json ; done
```
![T-telephone](https://user-images.githubusercontent.com/59083599/135861933-eb68781b-3dbe-4ebe-946f-fe1b68b18d06.png)

notice we had to increase the timeout timer to 60 seconds as we needed more points to calculate/generate

## output svg
to get svg output instead of png, just omit the png in the command
```
for d in axe2.jpg ; do timeout 25s triangula run -img $d -out j.json -p 500 ; triangula render -in j.json -out T-${d%%.*} -img $d ; rm j.json ; done
```

## use polygans instead of triangles
we need to insert `-s "polygons"` in both run and render commands
```
for d in belt.jpg ; do timeout 25s triangula run -img $d -out j.json -p 1000 -s "polygons" ; triangula render -in j.json -out T-${d%%.*} -img $d -s "polygons" png ; rm j.json ; done
```
![T-belt](https://user-images.githubusercontent.com/59083599/135863708-3a1fbbf7-73a5-42f7-9b47-4dc1288a80ba.png)

## making a animated gif out of an still image
since there is no randomization with the same shape counts we will iterate thru the shape numbers, starting at 50 shapes and convert a frame every 50 frames, so 50, 100, ... 500 shapes
```
for d in {50..100..50} ; do timeout 20s triangula run -img katana3.jpg -out j.json -p $d ; triangula render -in j.json -out T-$d -img katana3.jpg png ; rm j.json ; done
```
mux the images to a gif, because we have both 2 digit and 3 digits numbers and we want to sort them numerically we first use ls in our folder to find every png file and then pipe it to cat and convert it with ffmpeg
```
ls -v *.png | xargs cat | ffmpeg -framerate 10 -f image2pipe -i - katana.gif
```
![katana](https://user-images.githubusercontent.com/59083599/135897696-1176d7c7-53fb-4563-ad43-92cc94225ad0.gif)

if you want to randomize the frames use this command
```
for file in T-*.png ; do mv -- "$file" "$(mktemp --dry-run XXXXXX.png)" ; done
```
![katana++](https://user-images.githubusercontent.com/59083599/135898185-d2fdc49a-936c-49c6-925d-44c0db9a93c7.gif)

## triangulafy a video
lets apply what we learned to a video, i have made a example of how to download a free video, make image sequence, apply filter and mux it back [here](https://github.com/junguler/ffmpeg-examples/tree/main/sequence%2C%20manipulate%20%26%20mux%20images)
```
for d in *.jpg ; do timeout 10s triangula run -img $d -out j.json -p 250 ; triangula render -in j.json -out T-${d%%.*} -img $d png ; rm j.json ; done
```
and mux the images
```
cat T-*.png | ffmpeg -framerate 20 -f image2pipe -i - triangula_lemons.mp4 
```
https://user-images.githubusercontent.com/59083599/135906204-47bb3a61-1cf7-42dc-ad98-999973618fa9.mp4

## glitch it
like i said at the beggining of this page, this program takes an image and makes a json file out of it to produce triangulated images out of, what happens if we supply the same json file over and over for different images? glitch happens

lets use run to make a json file
```
triangula run -img image.jpg -out g.json -p 500
```
now lets loop every image with that same json file 
```
for d in *.jpg ; do triangula render -in g.json -out T-${d%%.*} -img $d png ;  done 
```
and mux the images
```
cat *.png | ffmpeg -framerate 30 -f image2pipe -i - glitch2_dance2.mp4  
```
https://user-images.githubusercontent.com/59083599/135914163-f0f2575c-392c-4569-83c4-10d514ed39cb.mp4
