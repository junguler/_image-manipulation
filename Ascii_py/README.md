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
