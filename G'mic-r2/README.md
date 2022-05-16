this is the second part of my showcase of G'mic filters, these are not by any means the only good filters G'mic has but it's a sample of what i find interesting and cool looking

## our source clip
https://user-images.githubusercontent.com/59083599/168679060-e408eb73-3d33-47f6-b216-d5509d160f9e.mp4

## angoisse anguish
```
for i in *.jpg ; gmic $i samj_Angoisse 1,5,0,0.8,100,2,4,1,250 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168679314-f72b4688-2688-4b6f-ad19-8e30190dba9c.mp4

## auora
```
for i in *.jpg ; gmic $i gcd_aurora 3,0.2,0 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168679531-7f51cc8c-2214-404b-95e6-1e2363ed55cd.mp4

## black crayon graffityi
```
for i in *.jpg ; gmic $i fx_crayongraffiti2 124,40,2.5,0.25,20,1,1,2,0 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168679623-0276ce70-d959-4d8a-b180-32cfb391d69a.mp4

## blockism
```
for i in *.jpg ; gmic $i fx_blockism 3,1.6,0.5,64,0.75,46,0,0,0 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168679824-47b43508-b240-4875-abc8-1958fee827d1.mp4

## comicbook
```
for i in *.jpg ; gmic $i cl_comic 6,2,0,1,1,15,15,1,10,20,6,2,0,0,0,0,0,0,50,50 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168679926-5af84a8c-f2e2-4336-a071-11a38f512750.mp4

## cutout
```
for i in *.jpg ; gmic $i fx_cutout 12,0,10,1,0,50,50 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168680040-e2d6d661-4553-4ba8-92c2-445064f6eb05.mp4

## felt pen
```
for i in *.jpg ; gmic $i fx_feltpen 2000,75,1,0.1,20,5,0,50,50 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168680141-eb88b893-f9d3-42f4-80d5-6275efb05d4f.mp4

## kuwahara
```
for i in *.jpg ; gmic $i fx_kuwahara 5,5,0,0,0,50,50 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168680329-f3ff6144-684d-4761-b915-3cdcb5d4351d.mp4

## jpeg artifacts
```
for i in *.jpg ; gmic $i fx_jpeg_artefacts 18,0,50,50 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168680389-4a2d37ba-2a3e-4173-ad8f-ca051fc6fce4.mp4

## oldschool 8bits
```
for i in *.jpg ; gmic $i fx_8bits 24,1000,16,0,50,50 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168680449-8d8f7792-ef83-4b26-be9d-5f17b9f914db.mp4

## pixel sort
```
for i in *.jpg ; gmic $i fx_pixelsort 1,0,0,1,0,65,0,0,0 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168680612-c01cce9f-ec63-45e0-aa95-f6e149cd7474.mp4

## self glitching
```
for i in *.jpg ; gmic $i fx_pixelsort 1,0,0,1,0,65,0,0,0 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168680685-944a5c8a-6757-4fb3-94bb-5337f22f1f56.mp4

## halftone shapes
```
for i in *.jpg ; gmic $i iain_halftone_shapes 10,0,0,0,0,0,0 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168680841-0b6f02d1-26ce-45e7-a57d-00868b92ea86.mp4

## 3d elevation
```
for i in *.jpg ; gmic $i fx_elevation3d 400,1,1024,1024,0.8,0,0,0,45,0,0,-100,0.5,0.7,2,1,0 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168681030-2d1fd402-93fa-4ccf-a546-64ae7875aeb1.mp4

## depth map construction
```
for i in *.jpg ; gmic $i fx_tk_depthmap 0,20,0,0,0,0,0,0,0,0 -o g-$i ; done
```
https://user-images.githubusercontent.com/59083599/168681181-fdddb276-127f-496e-b15f-a62273b3ce99.mp4

