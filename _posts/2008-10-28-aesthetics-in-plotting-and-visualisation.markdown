--- 
title: Aesthetics in Plotting and Visualisation
categories: 
- matlab
- code
- python
- plot
layout: post
---
I'm fairly sure that aesthetics play a large part in how people view your work
-- ugly *correct* results are probably viewed as being worse than pretty, but
*wrong* results. Aesthetics must play a fairly big role in how people perceive
your work.

I've just finished generating a lot of *quiver* plots for my thesis. A quiver plot is a graph of vectors, illustrating a flow field. My results typically show an image with motion vectors overlaid, all plotted with [Matlab](http://www.mathworks.com/ "The MathWorks - MATLAB and Simulink for Technical Computing"), a piece of software which is very heavily used in academia in the UK (and probably all over the world). 

Matlab quiver plots are ugly, and all of my plotting got me wondering how other system's quiver plots look. In particular, I've started playing with numpy and scipy, so I decided to do a quick comparison between matlab, and [matplotlib](http://matplotlib.sourceforge.net/ "Overview &mdash; Matplotlib v0.98.3 documentation"), the python close of matlab's plotting tools. The results are very interesting.

I generated a quick example motion field, and plotted it with quiver. Then I took screenshots. I used the [Gimp](http://www.gimp.org/ "GIMP - The GNU Image Manipulation Program") on my Linux box, for the matlab example) and [Skitch](http://skitch.com/ "Skitch.com + Skitch = fast and fun screen capture and image sharing.") on my MacBook for the python example.

First, here's the matlab example. This was generated on linux using Matlab 2007a:
<div class="thumbnail"><a href="http://skitch.com/mattfoster/36md/matlab-quiver"><img src="http://img.skitch.com/20081028-e7tjc5ay773fbuxb7p2bra6hsx.preview.jpg" alt="matlab_quiver" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

Here's the matplotlib python example, generated using the [enthought python distribution](http://www.enthought.com/products/epd.php "Enthought Python Distribution :: Products :: Enthought, Inc."). I used colour here because I could: matplotlib's `quiver` supports it out of the box. Matlab's doesn't.
<div class="thumbnail"><a href="http://skitch.com/mattfoster/36jm/figure-1"><img src="http://img.skitch.com/20081028-jnb9fa6irn43pefgrninqb1977.preview.jpg" alt="Figure 1" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

I think the difference between the results is abundantly clear. Matplotlib's
arrows look great, they're shapely and well scaled. Matlab's look like jaggedy
lines in comparison. However, I think the main difference is down to
anti-aliasing. The matplotlib's result looks better because they're smoother and look far more modern the 90s throwback that is matlab's interface (on linux and Mac at least -- I can't speak for Windows).

These results have pretty much convinced me to try my next project using Python and scipy instead of Matlab. Not only is it completely free (EPD is free for academic use, and matplotlib, scipy and numpy are just plan free), the aesthetic is there too. It's almost like python's elegant simplicity ideals spilled over into their plotting engines.
