--- 
title: More Chaco
layout: post
---
I've been doing a little bit more tweaking with chaco, learning how to use groups and containers. The [docs](http://code.enthought.com/projects/chaco/docs/html/quickstart.html "Quickstart &mdash; Chaco v3.0.0 documentation") are great, if a bit incomplete, so I ended up looking at various examples.

I've updated my [simple AM demo](http://my-mili.eu/2008/11/5/exploration-with-chaco "hackerific: Exploration with Chaco") so that it now shows the frequency content of the signal (calculated on the fly, using an FFT).

The running program looks like this:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/46fj/am-demo-with-fft"><img src="http://img.skitch.com/20081107-xrt7is9r3t39q7g3r31smsmeue.preview.jpg" alt="AM Demo with FFT" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

I'd still like to add zooming and area selections to the x-axis, and tidy the plots up a bit, but it's looking good.

The code used to generate this coolness was:

<script src="http://gist.github.com/22822.js"></script>

Short and sweet.
