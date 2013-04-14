--- 
title: Gnuplot gets iterators
categories: 
- gnuplot
- iterators
- iteration
layout: post
---
Whilst looking at the [gnuplot website](http://www.gnuplot.info/ "gnuplot homepage"), I discovered the [demo page](http://gnuplot.sourceforge.net/demo_4.3/ "Demo scripts for gnuplot CVS version"), which shows, amongst other things, new features in the CVS version. 

The main that caught my eye was the plot on the right, which shows a few overlaid sinusoids, with the code used to generate them as the key. Here's the code:

    plot for [n=2:10] sin(x*n)/n with filledcurves

That's right, one line for 8 plots! Version 4.3 of gnuplot introduces the `for` keyword, which lets you sweep through numerical parameters and loop through strings. The help (see `help iteration` with 4.3) has a few examples, which I've copied in below:

    plot for [filename in "A.dat B.dat C.dat"] filename using 1:2 with lines
    plot for [basename in "A B C"] basename.".dat" using 1:2 with lines
    set for [i = 1:10] style line i lc rgb "blue"
    unset for [tag = 100:200] label tag

I downloaded and compiled the sources and whipped up a quick example of my own (I couldn't get aquaterm going though). You can see it below:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/5gp6/gnuplot-has-iterators"><img src="http://img.skitch.com/20081110-dhu9jhct8hha9qhpwiutji3cg7.preview.jpg" alt="gnuplot has iterators!" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

I've got preliminary support going in the [Gnuplot TextMate bundle](https://github.com/mattfoster/gnuplot-tmbundle), but I'm still not 100% happy with it yet.
