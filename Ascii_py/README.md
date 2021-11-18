## what is needed to get started?
ascii_py is a cool python cli program that takes you images and makes cool looking ascii art out of them, find the github [repo](https://github.com/ProfOak/ascii_py),installing ascii_py is very easy, just install python3 and run a simple pip command:
```
python3 -m pip install ascii_py
```
there is also compiled linux binary on the repo [here](https://github.com/ProfOak/ascii_py/tree/master/bin)

<br>

### quick links
 * [basic usage](https://github.com/junguler/_image-manipulation/tree/main/Ascii_py#basic-usage)
 * [density](https://github.com/junguler/_image-manipulation/tree/main/Ascii_py#density-based)
 * [distance](https://github.com/junguler/_image-manipulation/tree/main/Ascii_py#change-distane-between-characters)
 * [custom characters](https://github.com/junguler/_image-manipulation/tree/main/Ascii_py#use-your-own-characters-or-words)
 * [iterate over an image](https://github.com/junguler/_image-manipulation/tree/main/Ascii_py#iterate-over-an-image)
 * [asciify a video](https://github.com/junguler/_image-manipulation/tree/main/Ascii_py#asciify-a-video)

<br>

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and some royalty free stock footage from youtube

<br>

## explanation of the switches and how the program works
| Flag | Description |
| --- | --- |
| `-o`, `--out` | the filename you want your final image saved as |
| `-w`, `--words` | use words to create your image |
| `-s`, `--step` | choose the distance of your characters |
| `-d`, `--density` | converts the image based on visual density |
| `-t`, `--terminal` | print ascii image to terminal |
| `-h`, `--help` | show help message and exit |

<br>

## basic usage
```
ascii_py basketball.jpg -o b-ball.jpg
```
![b-ball](https://user-images.githubusercontent.com/59083599/136875612-ae06a87a-b10e-4d05-8aca-2cd6913d1a1d.jpg)

<br>

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

<br>

## change distane between characters
```
ascii_py bicycle.jpg -d -s 10 -o bicy.jpg
```
![bicy](https://user-images.githubusercontent.com/59083599/136876414-6ef9df9e-ca5c-4f3c-ba08-c584b62dea8d.jpg)
```
ascii_py harleyD.jpg -d -s 15 -o harlD.jpg
```
![harlD](https://user-images.githubusercontent.com/59083599/136876717-14d77d6e-4213-478d-a705-05153c614ae9.jpg)

<br>

## use your own characters or words
this option takes your characters and use it to draw the picture, it's not a randomized or image based options tho, it repeats everything you add to it, spaces are empty characters in the image. so we either want to pass one character only to fill the whole image with it or add certain strings to replicate the effect.
```
ascii_py ab7.jpg -w "/" -s 5 -o abst+.jpg
```
![abst+](https://user-images.githubusercontent.com/59083599/136877614-1722ccfc-55c8-4648-bcc0-497888050e64.jpg)
```
ascii_py sunset.jpg -w "\|/-_" -s 5 -o sun+.jpg
```
![sun+](https://user-images.githubusercontent.com/59083599/136878131-77a84629-9d48-4af6-9cdd-e6866d09538e.jpg)

<br>

## iterate over an image
sometimes we want to make an animated gif but we only have one image to work with, if the program applies random values to conversions we would just feed the same image many times to make animated gifs but in the case of this program that does not seem to be the case.

we still have the option to modify our image somehow so the program see's it differently, lets apply that logic to an image and convert it to different resolutions
```
for i in {500..1500..50} ; ffmpeg -i cloud.jpg -vf scale=$i:-1 C-$i.jpg
```
what we did above is we started at 500 height and every frame added 50 to that to get to the 1500 frame in the 30th file, now let's feed these to ascii_fy
```
for i in *.jpg ; do ascii_py music.jpg -d -o B-$i.jpg ; done 
```
the name of each file is added to to B- to make the name of our output image, now let's resize all of our images to 1280 width so ffmpeg does not compress everything to the lowest common denominator
```
for i in B-*.jpg ; do ffmpeg -i $i -vf scale=1280:280 C-$i.jpg ; done 
```
notice that every time we convert these images we append different words for them, this is done for the case of easily cating them for conversion which is our last part
```
ls -v *.jpg | xargs cat | ffmpeg -framerate 10 -f image2pipe -i - cloud.mp4 
```
we use ls to pipe file names to cat because we have 3 and 4 digit names in our images and if we only used cat the order would have not been numerical

https://user-images.githubusercontent.com/59083599/136886149-05e9ffbb-69bf-4b8a-b894-3240233501bd.mp4

you can also randomize file names to make this gif file less uniform
```
for file in *.jpg ; do mv -- "$file" "$(mktemp --dry-run XXXXXX.jpg)" ; done 
```
https://user-images.githubusercontent.com/59083599/136887039-1d972588-38c2-4065-aa89-02e7883a8fd9.mp4

<br>

## asciify a video
lets apply what we learned to a video, i have made a example of how to download a free video, make image sequence, apply filter and mux it back [here](https://github.com/junguler/ffmpeg-examples/tree/main/sequence%2C%20manipulate%20%26%20mux%20images)
```
for i in *.jpg ; do ascii_py $i -d -o A-$i ; done 
```
and mux them to a video, note we also apply compression to this video to avoid very large outport size, without any compression the output size would be 150_mb, with the default ffmpeg compression it would have been 23_mb but we force bitrate to stay at 8mb and use veryslow preset to retain as much details as we can and end up with a 6.6_mb file that looks very similar to the uncompressed file
```
cat A-image-00* | ffmpeg -framerate 30 -f image2pipe -i - -b:v 8M -preset veryslow ascii_run.mp4
```
https://user-images.githubusercontent.com/59083599/137029432-715b26be-5a74-4d2b-9d2d-b1fd9c1a4876.mp4
