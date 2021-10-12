## what is needed to get started?
ascii_py is a cool python cli program that takes you images and makes cool looking ascii art out of them, find the github repo [rep](https://github.com/ProfOak/ascii_py),
installing ascii_py is very easy, just install python3 and run a simple pip command, there is also compiled linux binary on the repo [here](https://github.com/ProfOak/ascii_py/tree/master/bin)

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and some royalti free stock footage from youtube

## explanation of the switches and how the program works
| Flag | Description |
| --- | --- |
| `-o`, `--out` | the filename you want your final image saved as |
| `-w`, `--words` | use words to create your image |
| `-s`, `--step` | choose the distance of your characters |
| `-d`, `--density` | converts the image based on visual density |
| `-t`, `--terminal` | print ascii image to terminal |
| `-h`, `--help` | show help message and exit |

## basic usage
```
ascii_py basketball.jpg -o b-ball.jpg
```
![b-ball](https://user-images.githubusercontent.com/59083599/136875612-ae06a87a-b10e-4d05-8aca-2cd6913d1a1d.jpg)

## density based
use a wide range of characters to show density of the picture, this is the best option this program has imo
```
ascii_py men.jpg -d -o workers.jpg
```
![workers](https://user-images.githubusercontent.com/59083599/136875929-d4c3f274-22e8-42eb-a7f6-00aba1e9d5a0.jpg)
```
ascii_py ab4.jpg -d -o abstract.jpg
```
![abstract](https://user-images.githubusercontent.com/59083599/136876249-aef33d21-2881-401f-a4dc-25884fbdd584.jpg)

## change distane between characters
```
ascii_py bicycle.jpg -d -s 10 -o bicy.jpg
```
![bicy](https://user-images.githubusercontent.com/59083599/136876414-6ef9df9e-ca5c-4f3c-ba08-c584b62dea8d.jpg)
```
ascii_py harleyD.jpg -d -s 15 -o harlD.jpg
```
![harlD](https://user-images.githubusercontent.com/59083599/136876717-14d77d6e-4213-478d-a705-05153c614ae9.jpg)

## use your own characters or words
this option takes your characters and use it to draw the picture, it's not a randomized or image based options tho, it repeats everything you add to it, spaces are empty characters in the image. so we either want to pass one character only to fill the whole image with it or add certain strings to replicate the effect.
```
ascii_py ab7.jpg -w "/" -s 5 -o abst+.jpg
```
![abst+](https://user-images.githubusercontent.com/59083599/136877614-1722ccfc-55c8-4648-bcc0-497888050e64.jpg)
```
ascii_py sunset.jpg -w "\|/-_" -s 5 -o suns.jpg
```
![suns](https://user-images.githubusercontent.com/59083599/136877829-083e8869-2ce9-4c53-89ec-1a40cb866c31.jpg)
