## what is needed to get started?
G'mic is a massive collection of image processing filters combined to a one easy to use gui and cli program that can be installed on gimp, krita etc ... or used on the terminal, it's so big even when i made a markdown specific for showing it with many examples i barely scracthed the surface of what it does and i'm going to showcase one of it's filters here

for the basics of how to use the program look [here](https://github.com/junguler/_image-manipulation/tree/main/G'mic) , now that you are somewhat familier with this program lets do our thing

stylize is a cool filter for applying style transfer to our images, it's the most easy to use and un-complicated implementation of style transfer i have seen that runs localy on your computer without the need for internet or installing extra programs like python, lua or others

images that are linked in this markdown file are compressed to make loading the page faster, for the uncompressed versions go to the examples folder

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

## basic usage (using built-in styles)
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

## basic usage (using our own images as styles)
```
gmic tree.jpg lighthouse.jpg fx_stylize 0,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o Light_tree.jpg ; rm *000000.jpg
```
this command outputs two images, `Light_tree_000000` which is the same as our input image and `Light_tree_000001.jpg` which is what we actually want so for further commands we add a remove command at the end of our command to remove this undded file like this `; rm *000000.jpg` the `;` add the remove command to our gmic command to make it a one liner

| input | style |  output | 
| --- | --- | --- |
| ![lighthouse](https://user-images.githubusercontent.com/59083599/142261240-04c46041-153a-49e7-bc67-1f53dc5f9c09.jpg) | ![tree](https://user-images.githubusercontent.com/59083599/142261261-96e40765-9668-417f-be2d-2750423147c7.jpg) | ![Light_tree_000001+](https://user-images.githubusercontent.com/59083599/142262867-65fb5b74-48b4-450f-87e6-f920d79b0fc1.jpg) |
| ![genie](https://user-images.githubusercontent.com/59083599/142262316-a205e42c-11bd-4a49-af5b-edaf0fc167cb.jpg) | ![skyscraper](https://user-images.githubusercontent.com/59083599/142262433-e4deb6ce-8786-46dc-9291-46268bdb395d.jpg) | ![genie_sky_000001+](https://user-images.githubusercontent.com/59083599/142262911-2c182840-0a4d-49bf-8025-b5a1c1e562bf.jpg) |
| ![x-ray](https://user-images.githubusercontent.com/59083599/142265080-a3f49d5c-2284-44f6-9354-4e1cbc8bfd2b.jpg) | ![colorss](https://user-images.githubusercontent.com/59083599/142265108-71d1b61d-519e-465d-b599-4b8a944b6f80.jpg) | ![x-ray_color_000001+](https://user-images.githubusercontent.com/59083599/142265142-c6d6f7a7-4f1b-40f5-942a-ba700e48cf8a.jpg) |

## scale style image to produce different results
by default stylize sets your style image to 75% of it's size and uses it to re-create the input image, you can set this operation to none or make the resizing smaller or bigger depending on your style image, the default value is a good start point and might be fine for your case but we'll still show the differences here

changing style scale is done by changing the second number we pass to fx_stylize filter, it starts at 0 and ends at 10

<div align="center">

| input | style |
| --- | --- |
| ![car](https://user-images.githubusercontent.com/59083599/142270495-8fb30e96-8baf-4269-a74c-7af1a12f8629.jpg) | ![magnet](https://user-images.githubusercontent.com/59083599/142270540-af5af17d-6fa7-4bd7-80bc-5baf7a3dcd6a.jpg)
| 10% scale (1) | 50% scale (4) |
| ![l-scale-10_000001](https://user-images.githubusercontent.com/59083599/142270795-fb81face-c795-486a-9dfb-8c2aa64d791e.jpg) | ![l-scale-50_000001](https://user-images.githubusercontent.com/59083599/142270844-0d57bd3e-338d-4b3b-a67b-5693184e5ca8.jpg) | 
| 150% scale (7) | 300% scale (10) |
| ![l-scale-150_000001](https://user-images.githubusercontent.com/59083599/142270961-4ea352ac-b033-42c3-afe4-9420c95bc327.jpg) | ![l-scale-300_000001](https://user-images.githubusercontent.com/59083599/142270995-e5d9b4c4-f691-4a5a-b449-a8a65235550f.jpg) |

</div>
  
# specify smoothness
smoothness decides how much styles uses the style image to recreate the input image, the higher the smoothness the less the style image is used and the output image effected

<div align="center">
  
| input | style |
| --- | --- |
| ![flower5](https://user-images.githubusercontent.com/59083599/142274659-0a2a782a-656c-475d-b5a4-dd7ac56e96da.jpg) | ![ice](https://user-images.githubusercontent.com/59083599/142275517-9b37a72b-ebbe-40f4-87e7-f09625497dac.jpg) | 
| smoothness 0 | smoothness 5 |
| ![l-smooth_0_000001](https://user-images.githubusercontent.com/59083599/142275804-8d23337c-f9bd-441c-a0d5-a1ee8ec74300.jpg) | ![l-smooth_5_000001](https://user-images.githubusercontent.com/59083599/142275851-861cce24-b9a6-4d04-ae5f-3e801e030ab9.jpg) |

</div>
  
# respect gradients
by default stylize only takes 20% (1 out 5) of gradients into the effect, this part of the filter works in tandom with the smoothness option but won't mix them here because we want to showcase it on it's own

<div align="center">
  
| input | style |
| --- | --- |
| ![tincan](https://user-images.githubusercontent.com/59083599/142278864-78ff6cff-512a-4872-9447-5f008b61f0eb.jpg) | ![wall](https://user-images.githubusercontent.com/59083599/142278899-6dfb86e5-7ae3-4691-9706-4a5d650c0b12.jpg) | 
| gradients 0 | gradients 5 |
| ![l-gradient_0_000001](https://user-images.githubusercontent.com/59083599/142279142-9cf64207-6d14-4076-a15d-70dbb27ba331.jpg) | ![l-gradient_5_000001](https://user-images.githubusercontent.com/59083599/142279166-fe70c030-1fa4-4d5b-a9dc-3d99700403e8.jpg) |

</div>
  
#### this page is under construction and un-finished
