## what is needed to get started?
Primitive is a cli program that takes your input image(s) make cool looking art with them using basic shapes, find the github page [here](https://github.com/fogleman/primitive), 
primitive does not come with a binary executable by default, you can either install golang and compile it yourself or download the binary version of windows or linux from my repo [here](https://github.com/junguler/easy-primitive-batch)

### quick links
 * [combo](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#combo-examples)
 * [triangle](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#triangle-examples)
 * [rectangle](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#rectangle-examples)
 * [ellipses](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#ellipses-examples)
 * [circle](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#circle-examples)
 * [rotated rectangle](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#rotated-rectangle-examples)
 * [beziers](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#beziers-examples)
 * [rotated ellipses](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#rotated-ellipses-examples)
 * [polygon](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#polygon-examples)
 * [gif making example](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#fun-with-gifs)
 * [iterate with same settings](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#iterate-over-an-image-with-the-same-settings-multiple-times)
 * [iterate with progressive shapes](https://github.com/junguler/_image-manipulation/blob/main/Primitive/README.md#iterate-over-an-image-with-progressing-shape-numbers)

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/)

## explainiation of the switches and how the program works
`-i` imports your source image

`-o` specifies output image

`-n` number of shapes generated for each image, more produced more clear image but is slower

`-m` decides the which shape is used for each images: 0=combo, 1=triangle, 2=rect, 3=ellipse, 4=circle, 5=rotatedrect, 6=beziers, 7=rotatedellipse, 8=polygon . use the number only, for example 1 for triangle

`-r` resizes your input image to 256 pixel by default to make the converting process faster pass 0 to it to skip this process

`-s` decides the width of outpot size, if don't passed it outputs at 1024 pixels witdh

`-a` The opacity (0-255) of each shape added to the output image, default is 128 for half opacity, 255 for full opacity

`-bg` decides the background color, use a hex value, default is average

`-v` to see verbose log of what's happening

more switches are available and you can find them on the original [repo page](https://github.com/fogleman/primitive)

## combo examples
```
primitive -i cheetah.jpg -o c_0.jpg -n 1000 -m 0 -s 1280 -v
```
![c_0](https://user-images.githubusercontent.com/59083599/134971033-2042574c-545c-452b-b3f4-19592dec42af.jpg)

```
primitive -i lion.jpg -o l_0.jpg -n 500 -m 0 -s 1280 -v
```
![l_0](https://user-images.githubusercontent.com/59083599/134971423-39221aa7-505a-4a66-8ec3-49145bead5e2.jpg)

```
primitive -i cow.jpg -o c2_0.jpg -n 250 -m 0 -s 1280 -v
```
![c2_0](https://user-images.githubusercontent.com/59083599/134971626-6c228a14-f4b4-41d9-9c7e-762dda5881df.jpg)

## triangle examples
```
primitive -i monkey.jpg -o m_1.jpg -n 500 -m 1 -s 1280 -v
```
![m_1](https://user-images.githubusercontent.com/59083599/134972132-dbfe66d5-69bb-4e52-833a-8c0960b562f3.jpg)

```
primitive -i flamingo.jpg -o f_1.jpg -n 750 -m 1 -s 1280 -v
```
![f_1](https://user-images.githubusercontent.com/59083599/134972327-1199f59e-8000-4216-b442-c2e8f21a0541.jpg)

```
primitive -i flamingo.jpg -o f_1.jpg -n 750 -m 1 -s 1280 -v
```
![s_1](https://user-images.githubusercontent.com/59083599/134972589-b1671705-2aa1-43b8-b35f-f32a0199ead6.jpg)

## rectangle examples
```
primitive -i zebra.jpg -o z_2.jpg -n 500 -m 2 -s 1280 -v
```
![z_1](https://user-images.githubusercontent.com/59083599/134973168-74b107f8-2cbb-4b4b-a25f-aaaead4de70f.jpg)

```
primitive -i ostrich.jpg -o o_2.jpg -n 250 -m 2 -s 1280 -v
```
![o_2](https://user-images.githubusercontent.com/59083599/134973796-00692ef2-86a3-440e-93f0-dd08689db5f6.jpg)

```
primitive -i camel.jpg -o c_2.jpg -n 1000 -m 2 -s 1280 -v
```
![c_2](https://user-images.githubusercontent.com/59083599/134974054-9683101a-4cdd-4ad3-be77-a106ba7bc641.jpg)

## ellipses examples
```
primitive -i panda.jpg -o p_3.jpg -n 750 -m 3 -s 1280 -v
```
![p_3](https://user-images.githubusercontent.com/59083599/134974745-1b72e668-e744-46a3-b1dd-3773498a9e11.jpg)

```
primitive -i elephant.jpg -o e_3.jpg -n 500 -m 3 -s 1280 -v
```
![e_3](https://user-images.githubusercontent.com/59083599/134975167-5d66f940-1b15-4000-950d-0a8a53af4d7d.jpg)

```
primitive -i chicken.jpg -o c_3.jpg -n 1000 -m 3 -s 1280 -v
```
![c_3](https://user-images.githubusercontent.com/59083599/134975585-931520d8-6c15-421b-85bd-929c4463662f.jpg)

## circle examples
```
primitive -i bunny.jpg -o b_4.jpg -n 1000 -m 4 -s 1280 -v
```
![b_4](https://user-images.githubusercontent.com/59083599/134976622-8e98b641-9d20-42bb-a4af-12492717f630.jpg)

```
primitive -i crab.jpg -o c_4.jpg -n 250 -m 4 -s 1280 -v
```
![c_4](https://user-images.githubusercontent.com/59083599/134977192-96c1d0b4-c996-4613-9d12-5cc9647d5680.jpg)

```
primitive -i dog.jpg -o d_4.jpg -n 500 -m 4 -s 1280 -v
```
![d_4](https://user-images.githubusercontent.com/59083599/134977419-fbac4e68-ba1f-4aff-a766-b4cefc4b6eb7.jpg)

## rotated rectangle examples
```
primitive -i shark.jpg -o s_5.jpg -n 250 -m 5 -s 1280 -v
```
![s_5](https://user-images.githubusercontent.com/59083599/134978886-19e04a2f-0eb6-4f1e-a396-26dd6f41b780.jpg)

```
primitive -i horse.jpg -o h_5.jpg -n 500 -m 5 -s 1280 -v
```
![h_5](https://user-images.githubusercontent.com/59083599/134979064-3e9fd0fc-4558-4bd8-9953-55b0ee69e9d1.jpg)

```
primitive -i penguin.jpg -o p_5.jpg -n 750 -m 5 -s 1280 -v
```
![p_5](https://user-images.githubusercontent.com/59083599/134979287-abc4073a-07e9-40a9-981c-2d4a5d289755.jpg)

## beziers examples
for beziers we also use the `-rep 10` switch which multiplies the number of shapes by 10 for each iteration its adding, this is because lines are harder to make out if not many of them are present

```
primitive -i fox.jpg -o f_6.jpg -n 500 -m 6 -s 1280 -rep 10 -v
```
![f_6](https://user-images.githubusercontent.com/59083599/134980064-1eae1049-1038-4ea5-80e7-0c8f4c17ca19.jpg)

```
primitive -i wolf.jpg -o w_6.jpg -n 250 -m 6 -s 1280 -rep 10 -v
```
![w_6](https://user-images.githubusercontent.com/59083599/134980282-f1a43e0c-2f8d-4758-beb8-7ee9d3ef8bbc.jpg)

```
primitive -i cat.jpg -o c_6.jpg -n 750 -m 6 -s 1280 -rep 10 -v
```
![c_6](https://user-images.githubusercontent.com/59083599/134980528-9b346a37-7159-4cb3-b5ea-1be3432f2cc6.jpg)

## rotated ellipses examples
```
primitive -i hamster.jpg -o h_7.jpg -n 500 -m 7 -s 1280 -v
```
![h_7](https://user-images.githubusercontent.com/59083599/134982088-b1cc44b5-7395-4a3e-a65a-eb9ff9dda5d9.jpg)

```
primitive -i fish.jpg -o f_7.jpg -n 250 -m 7 -s 1280 -v
```
![f_7](https://user-images.githubusercontent.com/59083599/134981631-d40bc43d-c84c-4510-91a4-65a08132ba7b.jpg)

```
primitive -i fish.jpg -o f_7.jpg -n 250 -m 7 -s 1280 -v
```
![g_7](https://user-images.githubusercontent.com/59083599/134981981-af0fbc57-36ef-403e-a76d-073d53c9ee29.jpg)

## polygon examples
```
primitive -i butterfly.jpg -o b_8.jpg -n 250 -m 8 -s 1280 -v
```
![b_8](https://user-images.githubusercontent.com/59083599/134982428-ed22c593-f5f8-4aea-bf09-c1f0e7a9f878.jpg)

```
primitive -i hawk.jpg -o h_8.jpg -n 100 -m 8 -s 1280 -v
```
![h_8](https://user-images.githubusercontent.com/59083599/134982669-962b7272-87be-4ea0-8cfc-66ae7ef82e4e.jpg)

```
primitive -i deer.jpg -o d_8.jpg -n 500 -m 8 -s 1280 -v
```
![d_8](https://user-images.githubusercontent.com/59083599/134982851-1e820bf2-0d91-4fd5-aa4e-0ac26c9577c2.jpg)

## fun with gifs
each time you convert an image with primitive the output is different even with the same setting switches, this makes creating animated gifs very easy, just duplicate your image a few times, convert them with primitive
```
for i in *.jpg ; do echo $i ; primitive -i $i -o p-$i -n 500 -m 0 -v ; done
```
and then mux them together
```
cat p-bird*.jpg | ffmpeg -framerate 5 -f image2pipe -i - bird.gif
```
![bird](https://user-images.githubusercontent.com/59083599/135161040-b15eba7d-8ec3-46a9-bb28-8e3bdde87671.gif)

## iterate over an image with the same settings multiple times
lets convert this image 10 times with the same settings in one command
```
for t in {1..10} ; do echo $t ; primitive -i koala.jpg -o k-$t.jpg -n 500 -m 1 -v ; done
```
and mux the images
```
cat k-* | ffmpeg -framerate 10 -f image2pipe -i - koala.gif
```
![koala](https://user-images.githubusercontent.com/59083599/135194947-18748658-73cc-4a2d-9b28-d02defd3da6b.gif)

## iterate over an image with progressing shape numbers
lets convert this image 100 times with every image having 1 shape count more than the last one, starting at 1 shapes count and ending on 100
```
for t in {1..100} ; do echo $t ; primitive -i spider.jpg -o s-$t.jpg -n $t -m 0 -v ; done
```
and mux the images
```
cat s-* | ffmpeg -framerate 15 -f image2pipe -i - spider.mp4
```
the outpot gif was quite large so i decided to add this as a mp4 video, you can have the video looped forever by right clicking on it and tick on loop

https://user-images.githubusercontent.com/59083599/135197513-41fc5780-aca8-42d0-998a-f57348f6ebaf.mp4

## windows bat file and linux bash script
there is also [my repo](https://github.com/junguler/easy-primitive-batch) with easy to use bat and scripts to make life easier for batch proccessing
