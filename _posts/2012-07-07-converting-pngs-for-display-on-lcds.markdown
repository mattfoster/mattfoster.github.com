---
title: Converting PNGs for display on small LCDs
categories: 
- LCD
- OLED
- arduino
layout: post 
--- 

I backed a recent [Kickstarter](http://www.kickstarter.com) project to allow
[Sabernetics](http://sabernetics.com) to create and sell small I2C powered OLED
displays -- the small number of IO lines required by I2C makes it an excellent
bus for embedded stuff, and I love things with blue LEDs so backing the project
was a no-brainer :)

The boards just arrived, so I decided to have a play by wiring one up to an Arduino and giving it a poke. 

Frist, I grabbed the code samples from the [Sabernetic site](http://sabernetics.com/store/0-84-oled-display-96x16/), 
and after a quick look I noticed that it's based on Adafruit's 
[OLED Display Library](https://github.com/adafruit/Adafruit_SSD1306).

One of the things I like about the demo code is that it draws bitmap
icons, as well as circles, lines and rectangles. Icons are particularly cool so
I immediately decided to make my own and set about understanding how they're constructed.

Adafruit has some great tutorials on using OLED displays including how to create icons using 
[LCD Assistant](http://ladyada.net/products/oled12864/), but after seeing the example code I 
wanted to try create my own without using Windows, so decided to have a go at hacking up a 
script to do it for me.

Here's my first attempt. The result is not even close to being as complete as Adafruit's 
screenshots suggest that LCD Assistant is, but it seems to work fine for 16 x 16 pixel
images. I'll need to put some work into dealing with other images sizes, and to
do that I'll probably end up rewriting it using the Ruby
[NArray](http://narray.rubyforge.org/) library, or Python's [numpy](http://numpy.scipy.org/).
Both of these also have the advantage that they aren't Perl ;-)

<script src="https://gist.github.com/3068015.js"> </script>

To test it, I downloaded the icon set which is used by Bootstrap,
[GLYPHICONS](http://glyphicons.com/), converted a few to 16 x 16 pixels PNGs
and ran them through my script. Why these icons? Well, everything else on the
Web uses bootstrap, so I decided to do the same!

To use the script, make sure you have the correct CPAN modules installed (use your
system's package manager if you can), then call it with something like:

        perl lcd_icon.pl --filename input_png_image.png

and paste the resulting output into an array in the Arduino environment. The
OLED examples use something like this:

        static unsigned char __attribute__ ((progmem)) twitter_bmp[]={  
            0xff,0xff,0xff,0xff,0xff,0x0f,0x3f,0xbf,0xbf,0xbf,0xbf,0xff,0xff,0xff,0xff,0xff,
            0xff,0xff,0xff,0xff,0xff,0xf0,0xf7,0xe7,0xe7,0xe7,0xe7,0xff,0xff,0xff,0xff,0xff,
        };

and then code like this to do the actual drawing:

        display.drawBitmap(0, 0, twitter_bmp, 16, 16, 1);

<a href="http://www.flickr.com/photos/mattfoster/7522787560/" title="Sabernetics Icons by mattfoster, on Flickr"><img src="http://farm9.staticflickr.com/8147/7522787560_4d652fed50.jpg" width="500" height="418" alt="Sabernetics Icons"></a>

I had some interesting problems with PNGs which hadn't been processed by
ImageMagick's convert utility before use, and I haven't attempted to handle
images whose sizes aren't multiples of 8 pixels. Still, you may find this
script useful in your hackery. 
