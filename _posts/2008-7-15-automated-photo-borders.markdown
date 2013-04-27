--- 
title: Automated Photo Borders
categories: 
- code
- ruby
- imagemagick
- photos
- border
layout: post
---
If you've ever wanted to automatically add a coloured border to an image, then this ruby script might come in handy. 

`add_border.rb` does exactly what you expect; it adds a border. You can specify the outer and inner sizes, and the colour of the inner border between. By default, this colour will be the *average* RBG value, giving you an awesome look by default.

To use it, just run `ruby ./add_border.rb`, or `chmod +x` it, and run `./add_border.rb`. Available arguments are:
  
  * `--help` or `-h` for help.
  * `--color`, or `-c` to specify the border colour
  * `--inner`, or `-i` for the inner (coloured) border thickness
  * `--outer` or `-o` for the outer (black) border thickness
  * remaining arguments are considered filenames to process.

The script will output files whose names are the same, but with `_border` added before the filetype suffix, so that `my_image.jpg` would become `my_image_border.jpg`.

You can get it from:
  
  * [svn](http://svn.hackerific.net/svn/border/ "border - Revision 1: /")
  * Github (preferred) as I probably won't update SVN anymore.
	
`add_border.rb` requires [RMagick](http://rmagick.rubyforge.org/ "RMagick Download Page").

Note: I lost the original description page when I nuked my site. So this is a new one.
