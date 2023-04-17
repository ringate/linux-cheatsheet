convert & mogrify
=================

The `convert` and `mogrify` programs are a member of the ImageMagick suite of tools. Use it to convert between image formats as well as an image, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much more. `mogrify` similar to `convert` except the original image file is overwritten with any changes you request.

Command Formats
---------------
### convert
`convert <input-options> input-file <output-options> output-file`

### mogrify
`mogrify <options> input-file`


Common Usages
-------------

### Image Resize

##### Resize width as `60px`
```
$ convert logo.png -resize 60 logo-w60.png
```

##### Resize height as `80px`
```
$ convert logo.png -resize x80 logo_h80.png
```

##### Specified size
```
$ convert logo.png -resize 640x480 logo2.png
```


### Image Format Convert

##### Convert PNG with transparent background
* Default come with black color background
  ```
  $ convert logo.png logo.jpg
  ```
* Export as white color background
  ```
  $ convert logo.png -background white -flatten logo.jpg
  ```

##### Convert PDF as JPG image with high resolution
* `ebook.pdf[0]` : `[0]` mean page 1
```
$ convert -density 300 -trim ebook.pdf[0] -quality 100 -flatten -sharpen 0x1.0 ebook_page1.jpg
```

##### Convert with sRGB color profile, resize to width `150px` and export as RGB colorspace
* `srgb.icc` : Needed [Color Profile](http://www.color.org/srgbprofiles.xalter) File
```
$ convert logo_cmyk_2000px.jpg -profile srgb.icc -colorspace RGB -quality 100 -resize '150>' logo_rgb_150px.jpg
```


Make Animated GIF
-----------------
##### PNG slide images to GIF
```
$ convert -delay 5 -loop 0 -alpha set -dispose previous slide_*.png loading.gif
```

##### Convert with resize
```
$ convert -resize 180x120 +antialias -delay 6 -loop 0 -alpha set -dispose previous slide_*.png loading.gif
```

##### Extract GIF to single slide GIF
```
$ convert loading.gif slide_%d.gif
```


mogrify Usages
--------------

##### Update all JPG images as `80%` Compression
```
$ mogrify -quality 80% *.jpg
```

##### Update all images from colorspace `CMYK` to `RGB`
```
$ mogrify -colorspace RGB *.jpg
```


Reference Links
---------------
* [Resize whole folder of images](https://even.li/imagemagick-sharp-web-sized-photographs/)
* [Common photoshop workflows with imagemagick](http://nick-tomlin.com/2013/03/16/replacing-common-photoshop-workflows-with-imagemagick/)
* [Photoshop "save for web" by imagemagick](http://stackoverflow.com/questions/12152372/how-can-i-get-photoshops-save-for-web-quality-with-imagemagick)
* [imagicmagick command list](http://www.imagemagick.org/script/convert.php)
* [Command line can be as simple as this](http://www.imagemagick.org/script/command-line-processing.php)
