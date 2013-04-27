--- 
title: Stitching scientific movies with qt_tools
categories: 
- matlab
- movie
- graph
- quicktime
layout: post
---
Recently, I've been generating gazillions of sequences of pngs that I've saved from MATLAB. The filenames look like:

`interesting_image_<01--nn>.png`

What I really want is movies, but I really don't like using MATLAB's flakey movie generation code, it produces low quality output with ginormous files, and is really slow. This is where and [Quicktime Pro](http://www.apple.com/quicktime/ "Apple - QuickTime") comes in. By allowing you to open sequences of images, and then save them as movies, it's half way to a nice solution, but it still involves too many clicks, and tends to over-compress my nice clean pngs.

Now enter [qt_tools](http://www.omino.com/sw/qt_tools/ "qt_tools"). a pretty nifty package which builds on the usefulness of QuickTime, and makes its magic available via the command line. But not just normal magic, this is *advanced* magic! Not only can you perform all of your movies making tasks on the command line, you can also choose the video and audio compressor to use. I choose png compression, because my images are already pngs, and I want them to look nice. To see what image compression methods are available to you, try:

`qt_thing --type='imco'`

If your system's anything like mine, the list will be pretty large (30 entries for me). As well as choosing image compression, you can pick your favourite audio compression (I see 16, try `qt_thing --type='scom'`), and finally the type of container to put it all in (I see 28 with `qt_thing --type='spit'`). Wrapping all of this usefulness together, I ended up with a command line like this: 

`qt_export --sequencerate=1 interesting_image_01.png --video=png,1 --audio=0 --replacefile interesting_movie.mov`

Which is pretty cool, and does what I want. Finally, I decided to wrap this up in a quick script, and ended up with this:

<script src="http://gist.github.com/5021.js"></script>

A quick and easy way to squish image sequences into movies.
