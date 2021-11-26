# G'mic (stylize)
G'mic is a massive collection of image processing filters combined to a one easy to use gui and cli program that can be installed on gimp, krita etc ... or used on the terminal, it's so big even tho i already made a markdown file specific for showing it with many examples i barely scratched the surface of what it does and i'm going to showcase one of it's filters here

for the basics of how to use the G'mic look [here](https://github.com/junguler/_image-manipulation/tree/main/G'mic) , now that you are somewhat familiar with this program lets do our thing

stylize is a cool filter for applying style transfer to our images, see [here](https://discuss.pixls.us/t/style-transfer-soon-in-gmic/10009) for a deep dive of the filter documented by G'mic, stylize is the most easy to use and un-complicated implementation of style transfer i have seen that runs locally on your computer without the need for internet or installing extra programs like python, lua or others

note: images that are linked in this markdown file are compressed to make loading the page faster, for the uncompressed versions go to the examples folder

<br>

### quick links
 * [basic usage](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#basic-usage-using-built-in-styles)
 * [basic usage using custom styles](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#basic-usage-using-our-own-images-as-styles)
 * [scale styles](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#scale-style-image-to-produce-different-results)
 * [specify smoothness](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#specify-smoothness)
 * [respect gradients](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#respect-gradients)
 * [fun with gifs](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#fun-with-gifs)
 * [stylizify a video](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#stylizify-a-video)
 * [glitch it](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#glitch-it)
 * [batch processing](https://github.com/junguler/_image-manipulation/tree/main/G'mic(stylize)#batch-processing)

<br>

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and [here](https://www.rawpixel.com/free-images), there is also some royalty free stock footage from youtube

<br>

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

<br>

## basic usage (using built-in styles)
we'll start we some pre-embedded images as styles, this is easiest way to use the filter
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

<br>

## basic usage (using our own images as styles)
```
gmic tree.jpg lighthouse.jpg fx_stylize 0,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o Light_tree.jpg ; rm *000000.jpg
```
this command outputs two images, `Light_tree_000000.jpg` which is the same as our input image and `Light_tree_000001.jpg` which is what we actually want so for further commands we add a remove command at the end of our command to remove this un-needed file like this `; rm *000000.jpg` the `;` add the remove command to our gmic command to make it a one liner

| input | style |  output | 
| --- | --- | --- |
| ![lighthouse](https://user-images.githubusercontent.com/59083599/142261240-04c46041-153a-49e7-bc67-1f53dc5f9c09.jpg) | ![tree](https://user-images.githubusercontent.com/59083599/142261261-96e40765-9668-417f-be2d-2750423147c7.jpg) | ![Light_tree_000001+](https://user-images.githubusercontent.com/59083599/142262867-65fb5b74-48b4-450f-87e6-f920d79b0fc1.jpg) |
| ![genie](https://user-images.githubusercontent.com/59083599/142262316-a205e42c-11bd-4a49-af5b-edaf0fc167cb.jpg) | ![skyscraper](https://user-images.githubusercontent.com/59083599/142262433-e4deb6ce-8786-46dc-9291-46268bdb395d.jpg) | ![genie_sky_000001+](https://user-images.githubusercontent.com/59083599/142262911-2c182840-0a4d-49bf-8025-b5a1c1e562bf.jpg) |
| ![x-ray](https://user-images.githubusercontent.com/59083599/142265080-a3f49d5c-2284-44f6-9354-4e1cbc8bfd2b.jpg) | ![colorss](https://user-images.githubusercontent.com/59083599/142265108-71d1b61d-519e-465d-b599-4b8a944b6f80.jpg) | ![x-ray_color_000001+](https://user-images.githubusercontent.com/59083599/142265142-c6d6f7a7-4f1b-40f5-942a-ba700e48cf8a.jpg) |

<br>

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
  
<br>

## specify smoothness
smoothness decides how much styles uses the style image to recreate the input image, the higher the smoothness the less the style image is used and the output image effected

<div align="center">
  
| input | style |
| --- | --- |
| ![flower5](https://user-images.githubusercontent.com/59083599/142274659-0a2a782a-656c-475d-b5a4-dd7ac56e96da.jpg) | ![ice](https://user-images.githubusercontent.com/59083599/142275517-9b37a72b-ebbe-40f4-87e7-f09625497dac.jpg) | 
| smoothness 0 | smoothness 5 |
| ![l-smooth_0_000001](https://user-images.githubusercontent.com/59083599/142275804-8d23337c-f9bd-441c-a0d5-a1ee8ec74300.jpg) | ![l-smooth_5_000001](https://user-images.githubusercontent.com/59083599/142275851-861cce24-b9a6-4d04-ae5f-3e801e030ab9.jpg) |

</div>
  
<br>

## respect gradients
by default stylize only takes 20% (1 out 5) of gradients into the effect, this part of the filter works in tandem with the smoothness option but won't mix them here because we want to showcase it on it's own

<div align="center">
  
| input | style |
| --- | --- |
| ![tincan](https://user-images.githubusercontent.com/59083599/142278864-78ff6cff-512a-4872-9447-5f008b61f0eb.jpg) | ![wall](https://user-images.githubusercontent.com/59083599/142278899-6dfb86e5-7ae3-4691-9706-4a5d650c0b12.jpg) | 
| gradients 0 | gradients 5 |
| ![l-gradient_0_000001](https://user-images.githubusercontent.com/59083599/142279142-9cf64207-6d14-4076-a15d-70dbb27ba331.jpg) | ![l-gradient_5_000001](https://user-images.githubusercontent.com/59083599/142279166-fe70c030-1fa4-4d5b-a9dc-3d99700403e8.jpg) |

</div>
  
<br>

## other config knobs and choices
there is simply too many options to go over, i'm not sure how effective they are and how much they might show up in result outputs as i didn't have the time to test them, but i'll make sure to include them if they caught my attention

<br>

## fun with gifs
making a animated gif with stylize is just as easy as still images, we just need a `for` loop for batch processing, if you don't have a image sequence of your gif file you can make one like this 
```
ffmpeg -i my.gif -vsync 0 S-%4d.jpg
```
the above command pads 4 zeros to our images after `S-` , each gif file is limited to 500 frames but we add an extra 0 at the beginning to make life easier for our for loop and the conversion of our stylized sequence to gif again 

now for converting our newly made image sequence
```
for i in S-0*.jpg ; do gmic crochet.jpg $i fx_stylize 0,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o G-$i.jpg ; rm *000000.jpg ; done
```
now make the animated gif
```
cat G-*.jpg | ffmpeg -framerate 30 -f image2pipe -i - -preset veryslow crochet_face.gif
```

| input |  output | 
| --- | --- |
| ![face-low](https://user-images.githubusercontent.com/59083599/142287222-4892d2a4-6963-457a-93b0-f0b141cd6441.gif) | ![crochet_low](https://user-images.githubusercontent.com/59083599/142287356-4fba04cb-bd6d-435c-9160-41b0e558bfe1.gif) |

for the style image go to the gif folder inside examples, these gifs were significantly compressed using gifsicle to make their size way smaller and are not representative of the actual result quality

<br>

## stylizify a video
lets apply what we learned to a video, i have made a example of how to download a free video, make image sequence, apply filter and mux it back [here](https://github.com/junguler/ffmpeg-examples/tree/main/sequence%2C%20manipulate%20%26%20mux%20images)
```
for i in *.jpg ; do gmic neon.jpg $i fx_stylize 0,5,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o G-$i.jpg ; rm *000000.jpg ; done 
```
as you can see the process is similar to gif making, we just want to make a video instead, videos have the advantage of applying a uniform compression to each frame and produce amazing quality images with a really small output size
```
cat G-*.jpg | ffmpeg -framerate 30 -f image2pipe -i - -preset veryslow guitar-neon.mp4
```
https://user-images.githubusercontent.com/59083599/142411781-b9f9ffa8-7a29-4f15-9437-2f1e59364201.mp4

here is another example at half speed

https://user-images.githubusercontent.com/59083599/142415370-838f1fd1-a66d-4370-b1cb-fc6139ee577c.mp4

<br>

## glitch it
we've been trying to re-create the input images as best as we can and get a clear result, lets change all of that and destroy the input

the easiest way you can go about this is using a frame out of an image sequence as the style image

```
for i in *.jpg ; do gmic 0468.jpg $i fx_stylize 0,6,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o G-$i.jpg ; rm *000000.jpg ; done
```

https://user-images.githubusercontent.com/59083599/142775522-d84679bf-dee3-4f5e-ab9a-3e89242c5b76.mp4

<br>

using a glitched image as style

https://user-images.githubusercontent.com/59083599/142775599-9cf014d1-1e78-46a2-ac6e-2de7a00c4268.mp4

<br>

use a pixelated or a very small image as style

https://user-images.githubusercontent.com/59083599/142776987-c4e304e7-403c-4e77-b954-df675867145e.mp4

<br>

use a blank noise image as style

https://user-images.githubusercontent.com/59083599/142778275-acd9864c-c722-4a3a-8ecb-5040e5dc6956.mp4

<br>

use a dithered gradient as style

https://user-images.githubusercontent.com/59083599/142779160-f6b6f1ef-2395-4e82-a05b-123cf10b7405.mp4

<br>

use G'mic's own pixel sort filter for style

https://user-images.githubusercontent.com/59083599/143520455-6f8708f3-711d-4166-884c-e7e799328c4e.mp4

<br>

use G'mic's own charcoal filter for style

https://user-images.githubusercontent.com/59083599/143523908-1f1c3787-d131-4116-87d7-8282a2a362d2.mp4

<br>

## batch processing
it's kind of hard to know how an image might look without converting it first, when in doubt, stylize them all!

```
for i in *.jpg ; do gmic $i statue_of_liberty.jpg fx_stylize 0,6,0,0,0.5,2,3,0.5,0.1,3,3,0,0.7,1,0,1,0,5,5,7,1,30,10,2,1.85,0 -o G-$i.jpg ; rm *000000.jpg ; done
```

| ![S-statue_liberty_landmark_close_1](https://user-images.githubusercontent.com/59083599/142790652-97212168-4296-45db-b998-fb79d0363a81.jpg) | ![S-G-wood_texture_material_3d jpg_000001](https://user-images.githubusercontent.com/59083599/142790659-f2970414-c199-42eb-b7e8-8f336d66cbd3.jpg) | ![S-G-wood_texture_burned_fire jpg_000001](https://user-images.githubusercontent.com/59083599/142790665-d5b7f5ff-facd-4c27-b103-1d29c3ea001a.jpg) | ![S-G-wall_texture_background_stones-b_2 jpg_000001](https://user-images.githubusercontent.com/59083599/142790669-18e6350d-729f-40ef-a29b-f30ee05b8106.jpg) |
|---|---|---|---|
| ![S-G-trunk_bark_texture_background jpg_000001](https://user-images.githubusercontent.com/59083599/142790672-cb7d3e6c-d7a6-4140-8657-66b2bcb81acf.jpg) | ![S-G-texture_wood_wood_texture_0 jpg_000001](https://user-images.githubusercontent.com/59083599/142790675-bf78ddb2-d8a5-4fba-a872-59bebbc6f0ec.jpg) | ![S-G-texture_wood_paint_grain_2 jpg_000001](https://user-images.githubusercontent.com/59083599/142790677-502d4a9d-ce80-4780-ae51-286785705b4d.jpg) | ![S-G-texture_white_black_pattern jpg_000001](https://user-images.githubusercontent.com/59083599/142790678-1dddacb7-04f5-46de-a4e2-2fac4b15a716.jpg) |
| ![S-G-texture_weave_background_macro jpg_000001](https://user-images.githubusercontent.com/59083599/142790680-5b934360-496c-4168-9d6c-49f979597783.jpg) | ![S-G-texture_structure_composition_1680613 jpg_000001](https://user-images.githubusercontent.com/59083599/142790682-73f3a6cb-abee-486f-bc63-7b899808ecc0.jpg) | ![S-G-texture_straw_hut_970479 jpg_000001](https://user-images.githubusercontent.com/59083599/142790685-8d06f333-46c1-451f-aa09-a0b4f186e53b.jpg) | ![S-G-texture_pattern_beautiful_bright jpg_000001](https://user-images.githubusercontent.com/59083599/142790687-fe5458c6-0dc5-4eb7-a6c5-5d11c8d1ec9f.jpg) |
| ![S-G-texture_oil_water_blue jpg_000001](https://user-images.githubusercontent.com/59083599/142790690-1c84afcb-55ac-4511-88b0-3731dcdd5221.jpg) | ![S-G-texture_metal_background_model jpg_000001](https://user-images.githubusercontent.com/59083599/142790695-9c6c2a69-58d2-46cf-a9eb-333b7fb29722.jpg) | ![S-G-texture_leaf_ruffled_sheet jpg_000001](https://user-images.githubusercontent.com/59083599/142790698-062507a6-3262-4e8e-b8d9-da6722f7f46a.jpg) | ![S-G-texture_grid_graphic_abstract jpg_000001](https://user-images.githubusercontent.com/59083599/142790699-505b75a3-e6b2-4f0e-9c62-c175fcded4ee.jpg) |
| ![S-G-texture_green_plant_lettuce jpg_000001](https://user-images.githubusercontent.com/59083599/142790701-d87d26c8-f103-4144-b8a5-14607dcc96de.jpg) | ![S-G-texture_facade_shielding_steel jpg_000001](https://user-images.githubusercontent.com/59083599/142790702-465a5a15-b2b2-471c-91fb-f084893c5e89.jpg) | ![S-G-texture_fabric_fabric_texture jpg_000001](https://user-images.githubusercontent.com/59083599/142790705-39dd9551-b634-40c7-bcbf-a8262f258a83.jpg) | ![S-G-texture_dried_seeds_decoration jpg_000001](https://user-images.githubusercontent.com/59083599/142790708-960d3da7-5b0b-417b-a941-ce7b6b240081.jpg) |
| ![S-G-texture_bench_chair_white jpg_000001](https://user-images.githubusercontent.com/59083599/142790711-1b6490a7-691f-4252-a2dc-dfde617d9055.jpg) | ![S-G-strawberry_texture_fruit_healthy jpg_000001](https://user-images.githubusercontent.com/59083599/142790715-3674fecb-5dd4-4ac8-8333-37333c82cfb1.jpg) | ![S-G-stone_texture_background_stones_1 jpg_000001](https://user-images.githubusercontent.com/59083599/142790717-b15e50f7-899a-41e7-a8cc-b7910ae09572.jpg) | ![S-G-stone_ruins_texture jpg_000001](https://user-images.githubusercontent.com/59083599/142790718-78a36fc8-7d85-4f7f-ae53-66496a39c2ae.jpg) |
| ![S-G-scale_texture_background_green jpg_000001](https://user-images.githubusercontent.com/59083599/142790720-851081ff-bb60-461d-a527-7d044b1bcae1.jpg) | ![S-G-pineapple_texture_macro_pattern jpg_000001](https://user-images.githubusercontent.com/59083599/142790722-4d647c8a-5ac1-44d3-849e-6bbbd72a0888.jpg) | ![S-G-pattern_texture_blocks_wood jpg_000001](https://user-images.githubusercontent.com/59083599/142790727-9122d185-0d41-4fb5-b9c3-051a4ebdaac9.jpg) | ![S-G-mosaic_texture_blue_yellow jpg_000001](https://user-images.githubusercontent.com/59083599/142790729-3b94ad10-c361-4bb9-84c4-eff9e502f45c.jpg) |
| ![S-G-model_texture_pattern_427979 jpg_000001](https://user-images.githubusercontent.com/59083599/142790732-68e220e2-b847-44c9-b3d3-97a767723a64.jpg) | ![S-G-leaves_texture_scroll_area jpg_000001](https://user-images.githubusercontent.com/59083599/142790737-a1b47ecd-fa00-48c3-9e7c-59aafa7ea5c9.jpg) | ![S-G-grunge_texture_square_pattern jpg_000001](https://user-images.githubusercontent.com/59083599/142790740-73706a3e-5bc0-4144-ab96-8ccadab7c65d.jpg) | ![S-G-gravel_texture_grass_rocks jpg_000001](https://user-images.githubusercontent.com/59083599/142790741-aca294db-18ea-4128-8998-7cdabfa72e19.jpg) |
| ![S-G-gravel_texture_0 jpg_000001](https://user-images.githubusercontent.com/59083599/142790742-8643c402-f6c5-46a2-9416-225c041569cf.jpg) | ![S-G-colorful_texture_scarf_pattern jpg_000001](https://user-images.githubusercontent.com/59083599/142790743-e85c4f0d-cc9c-4a81-b1c7-6275c2952c00.jpg) | ![S-G-cobbles_grey_texture jpg_000001](https://user-images.githubusercontent.com/59083599/142790745-11432be9-5a93-457f-968d-2ccfc397db48.jpg) | ![S-G-cable_texture_yellow_black jpg_000001](https://user-images.githubusercontent.com/59083599/142790749-f5948dd1-a8e6-4f13-86a3-f4da4a4331ad.jpg) |
| ![S-G-braid_texture_background_model jpg_000001](https://user-images.githubusercontent.com/59083599/142790753-f0cdb0e3-f41b-4ba0-8518-ea860ca80c5b.jpg) | ![S-G-bokeh_texture_lights_bright jpg_000001](https://user-images.githubusercontent.com/59083599/142790754-fbb9c8e0-3784-4745-a4d8-7d63faf114f4.jpg) | ![S-G-basket_texture_pattern_weave jpg_000001](https://user-images.githubusercontent.com/59083599/142790756-7ca95735-e056-445a-9ecc-10ae65db0b29.jpg) | ![S-G-bamboo_texture_pattern_wood jpg_000001](https://user-images.githubusercontent.com/59083599/142790759-e01c6350-c9c3-4e8d-b0fc-a78aecc64451.jpg) |
| ![S-G-background_texture_textile_pattern jpg_000001](https://user-images.githubusercontent.com/59083599/142790760-dae1bfc9-3c48-4697-845c-01bb3f05254e.jpg) | ![S-G-background_texture_design_layer_13 jpg_000001](https://user-images.githubusercontent.com/59083599/142790763-0963e854-c178-4938-8159-9056e2b64f56.jpg) | ![S-G-background_texture_bricks_wall jpg_000001](https://user-images.githubusercontent.com/59083599/142790765-ba2745c7-4f3f-4ad3-842f-d62c3b30545c.jpg) | ![S-G-background_texture_banana_braid jpg_000001](https://user-images.githubusercontent.com/59083599/142790770-7d273f71-f89c-4505-8c93-97fab26a3c71.jpg) |
