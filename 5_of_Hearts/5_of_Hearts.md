## 5 of Hearts

This time using find to discover a flag is not so trivial, in fact the pic is not the real ones.

```
root@ip-10-0-101-252:~# find /* -name '*.png' | grep hearts
/lost+found/3_of_hearts.png
/var/www/html/drupal/sites/default/files/styles/large/public/field/image/5_of_hearts.png
/var/www/html/drupal/sites/default/files/styles/thumbnail/public/field/image/5_of_hearts.png
/var/www/html/drupal/sites/default/files/field/image/5_of_hearts.png
```

![Fake Flag](./img/img1.png)

Using Exiftool we have a little hint:

```
Stone:Flags syrion$ exiftool 5_of_hearts.png 
ExifTool Version Number         : 10.65
File Name                       : 5_of_hearts.png
Directory                       : .
File Size                       : 497 kB
File Modification Date/Time     : 2017:12:06 12:19:58+01:00
File Access Date/Time           : 2017:12:06 12:30:27+01:00
File Inode Change Date/Time     : 2017:12:06 12:21:37+01:00
File Permissions                : rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 500
Image Height                    : 700
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Tag 5 of hearts                 : iVBORw0KGgoAAAANSUhEUgAAAfQAAAK8CAYAAAAZNU0WAAAAAXNSR0IArs4c6QAAQABJREFUeAHsvQecX8lV51udc5C61cpxosOATVwMNsFkP++CWT6Gt8suLB/AvCUsyYTPsh/AwIM1uyzZZBYesMvaBJtgY2PPjCbPSBqlGUkjaUZxlGNLnbvf93vqf1v/bvVoZuzB05qp6nDvrVvh1Kl7z6/OqVN1G9LLGPbu3Ts4PtXwxpmGmTsaU7pjJv5mVkBSTwN/aSb1ENf6Mp...
```

The actual flag is in the base64 data:

`exiftool 5_of_hearts.png | grep tag | cut -d " " -f 22 | base64 -D > real_5_of_hearts.png`

![Flag](./img/img2.png)

`MD5 = 1862c5dac75e43bb8d530d54575592b7`
