## what is needed to get started?
ascii-image-converter is a cli program that takes your image(s) make cool looking ascii art out of them on the terminal and externally. find the github repo [here for gui](https://github.com/TheZoraiz/ascii-image-converter) download the binary version for your os [here](https://github.com/TheZoraiz/ascii-image-converter/releases/tag/v1.11.0) put it in your @PATH and open the terminal. this program is mainly designed to output the ascii art in the terminal but i'm more interested in getting external outputs from it, check the [README.md](https://github.com/TheZoraiz/ascii-image-converter/blob/master/README.md) of the original repo for more detailed visual representation of the program in the terminal

## source material
everything is downloaded from a royalty free image website [here](https://free-images.com/) and some royalti free stock footage from youtube

## explanation of the switches and how the program works
| Flag | Description |
| --- | --- |
| `-C`, `--color` | display and output with colors from original image |
| `-b`, `--braille` | use braille characters instead of ascii |
| `--threshold` | set threshold value to compare for braille art when converting each pixel into a dot |
| `--dither` | apply dithering on image to make braille art more visible |
| `--color-bg` | if any of the coloring flags is passed, this flag will transfer its color to each character's background. instead of foreground. However, this option isn't available for --save-img and --save-gif |
| `-d`, `--dimensions` | set the width and height for ascii art in CHARACTER lengths, for example: --dimensions width,height like this: -d 60,30|
| `-W`, `--width` | set width of ascii art. Height is calculated according to aspect ratio |
| `-H`, `--height` | set height of ascii art. Width is calculated according to aspect ratio |
| `-m`, `--map` | pass a string of your own ascii characters to map against, it must start from darkest character and end with lightest, there is no limit to number of characters, here is an example of a 7 character string: -m " .-=+#@" |
| `-g`, `--grayscale` | display and outpot ascii art in grayscale colors |
| `-n`, `--negative` | display and outpot ascii art in negative colors |
| `-c`, `--complex` | print the image with a wider array of ascii characters for more detailed lighting density, sometimes improves accuracy |
| `-f`, `--full` | print ascii art that fits the terminal width while maintaining aspect ratio |
| `-x`, `--flipX` | flip the ascii art horizontally on the terminal |
| `-y`, `--flipY` | flip the ascii art vertically on the terminal |
| `-s`, `--save-img` | saves the ascii as a PNG image with the name image_name-ascii-art.png |
| `--save-txt` | saves the ascii art as a TXT file with the name image_name-ascii-art.TXT |
| `--save-gif` | Saves the imported GIF as an ascii art GIF with the name image_name-ascii-art.gif , experimental |
| `--save-bg` | this flag takes an RGB value that sets the background color in saved png and gif files |
| `--font` | this flag takes path to a font .ttf file that will be used to set font in saved png or gif files |
| `--font-color` | this flag takes an RGB value that sets the font color in saved png and gif files as well as displayed ascii art in terminal |
| `--only-save` | don't print ascii art on the terminal if some saving flag is passed |
| `--formats` | display supported input formats |

note: for the sake of keeping the table orginized, the description is not as verbose as the original repo page.

## basic usage
```
ascii-image-converter yin_yang.jpg -s . -W 64 --only-save
```
![yin_yang-ascii-art](https://user-images.githubusercontent.com/59083599/136243139-541425e3-82d0-4222-9cf9-c1ed8f3e7796.png)

`-s .` output external image `-W 64` set 64 character width `--only-save` to not print the ascii art in the terminal

### with color
```
ascii-image-converter rubikQ.jpg -C -s . -W 96 --only-save
```
![rubikQ-ascii-art](https://user-images.githubusercontent.com/59083599/136244404-95ad4260-1e7f-4f2b-b8bb-5e429703a110.jpg)

```
ascii-image-converter sneaker.jpg -C -s . -W 128 --only-save
```
![sneaker-ascii-art](https://user-images.githubusercontent.com/59083599/136244547-8cf39735-1578-4c05-855c-9c84a6fe2b4b.jpg)

## using custom characters
using the `-m` flag we can use our own string of characters
```
ascii-image-converter paint2.jpg -C -s . -W 104 --only-save -m "-_\|/"
```
![paint2-ascii-art](https://user-images.githubusercontent.com/59083599/136245496-4627865c-4014-435e-9425-ce9f7828c512.jpg)

```
ascii-image-converter sofa.jpg -C -s . -W 96 --only-save -m "[]{}|()"
```
![sofa-ascii-art](https://user-images.githubusercontent.com/59083599/136248549-f60c32fe-089e-4e83-a7f1-02de30f0cbb9.jpg)

```
ascii-image-converter newspaper.jpg -C -s . -W 200 --only-save -m ".oO01"
```
![newspaper-ascii-art](https://user-images.githubusercontent.com/59083599/136247425-2e30dac0-4ef8-4cd3-a3f0-5e80f5c5fee4.jpg)

## using nerd fonts
[nerd fonts](https://www.nerdfonts.com/#home) are a collection of free and open sort fonts that have many extra glyphs patched into them, download one of them [here](https://www.nerdfonts.com/font-downloads), use windows compatible mono varient even if you are in linux like me or on macos, lets rename it to `NerdMono.ttf` so it's easier to link and put inside the folder you want to convert your images on. we'll use the `--font` flag to use it.
```
ascii-image-converter github.png -C -s . -W 48 --only-save -m "" --font NerdMono.ttf
```
![github-ascii-art](https://user-images.githubusercontent.com/59083599/136251225-edfe33a8-ab77-409c-873a-4baf43abcf7f.png)

the glyph probably doesn't show in this markdown file but if you copy the link it will work

## braille art
```
ascii-image-converter earth.jpg -C -s . -W 96 --only-save -b --dither
```
![earth-ascii-art](https://user-images.githubusercontent.com/59083599/136256903-0545bc11-273b-4c8a-985f-bf274a72c81b.jpg)


### more examples coming soon, we'll also go over making animated gifs and videos too