--- 
title: Getting a working Gnuplot for the TextMate bundle
categories: 
- gnuplot
- textmate
- bundle
- github
layout: post
---
I've been looking at getting a good build of "gnuplot":http://gnuplot.info/ with everything I need for the bundle, and so I've tried various versions. 

My currently recommended way of getting "gnuplot":http://gnuplot.info/ is this:

    fink install gnuplot-nox
    
This will automatically build and install a gnuplot with pdflib and "aquaterm":http://sourceforge.net/projects/aquaterm/ support, as well as everything else you're likely to need. This only thing that it misses out it X11 support, which I don't want and you probably don't either! Aquaterm is a lot more convenient, and fast. Unfortunately, there's isn't a binary build of this in `fink` yet, but fingers crossed that there will be soon.

I've put this information in a "wiki":http://github.com/mattfoster/gnuplot-tmbundle/wikis/best-gnuplot-for-osx page on "GitHub":http://github.com/. I'll try and keep that up to date with my current recommendation. 
