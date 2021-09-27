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
