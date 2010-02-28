--- 
title: MATLAB Interpolation Toolkit
categories: 
- matlab
- interpolation
- toolkit
layout: post
---

During the course of my PhD, I've spent quite a lot of time examining methods of interpolating scattered data. By *scattered*, I mean something that looks like this:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/bbh88/plasma-scatter"><img src="http://img.skitch.com/20090121-bi3xaxn1i7n9p9tuk7tsf9f9hg.preview.jpg" alt="plasma_scatter" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

Or alternatively, like a very, very gappy image. This type of data is very common in geoscience, and so interpolating it so it looks more like this:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/bbh8d/plasma-nn-surf"><img src="http://img.skitch.com/20090121-xkhghakmudr437kmid3npmh49x.preview.jpg" alt="plasma_nn_surf" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

Is a common activity. As well as examining common methods of interpolating scattered data, such as cubic, linear and nearest neighbour methods, I've looked at natural neighbour interpolation, radial basis function interpolation, everyone's favourite kriging and a less common methods known as adaptive normalised convolution (ANC).

In order to do meaningful comparisons, I needed working implementations of these, and so ended up writing my own versions of ANC, radial basis function interpolation and kriging. I also wrote a wrapper to [Pavel Sakov's natural neighbour interpolation](http://www.sciencecentral.com/site/501114 "Pavel Sakov's Software - Natural Neighbours Interpolation  Orthogonal Grid Generation  Quadratic Programming, developed for marine engineering applications using Linux by Pavel Sakov.").

I've just released these functions as a toolkit for [Matlab](http://www.mathworks.com/ "The MathWorks - MATLAB and Simulink for Technical Computing"), with a BSD license. You can find the download links on the [toolkit's homepage](http://mattfoster.github.com/matlab-interpolation-toolkit "mattfoster/matlab-interpolation-toolkit @ GitHub"), which also gives the commands you need to clone the repository.

To build the toolkit, you'll need a working build environment, with make, gcc and python 2.5 as well as a copy of Matlab. I've tested the kit on Debian/Ubuntu Linux with Matlab 2007a and Mac OS X (10.5). If you're using a Mac, you'll need XCode installed.

You'll probably need to tell make where your mex binary is (MEX is Matlab's external interface builder). To do this, run:

	make MEX=/path/to/mex
	
You'll find mex inside your Matlab installation, under the `bin/` directory. On linux, it may be symlinked into `/usr/local/bin`.

Once make has run, you'll find a directory called `toolkit`, which contains the interpolation toolkit. Copy this folder somewhere appropriate, and add it to your Matlab path, by running:

	addpath('/path/to/toolkit')
	
Within Matlab. You can then run `help toolkit`, for some help and examples of how to test the methods.

I'd recommend using natural neighbour interpolation everywhere you would previously have used matlab's `griddata` function. You can find more information on interpolation in my publications, which you can read and download [here](http://work.hackerific.net/papers.html "Matthew Foster's Publications").
