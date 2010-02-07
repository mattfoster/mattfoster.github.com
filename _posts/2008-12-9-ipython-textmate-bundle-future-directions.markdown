--- 
title: "IPython TextMate Bundle: Future Directions"
layout: post
category: textmate
---
IPython Server
--------------

Now that the IPython TextMate bundle has been around for a little while, and
has struck a chord with the TextMate wielding, IPython hacking community, I
decided that now might be a good time to sum up a few of my ideas for the
future.

I've really been heartened by the response and enthusiasm of the IPython community, and of particular note is the work by Brain Granger. [Brian](https://launchpad.net/~ellisonbg) is currently working on a [Twisted](http://twistedmatrix.com/trac/ "Twisted") based editor server for TextMate (and other editors too), with a block based protocol for robust communications. You can find some initial work in [Launchpad](https://code.launchpad.net/~ellisonbg/ipython/textmate-server), and grab it using bazaar using: 

    lp:~ellisonbg/ipython/textmate-server

Just be aware that this branch/link might not be around for long. 

My top priority for the bundle with regards to this is the creation of a client library, probably also based on Twisted. It would be great to have this core library included in IPython, so it can be called on by other editors.

Core Bundle Content
-------------------

I think that the core of the bundle is fairly coherent (at least for me!),
with the most useful commands appearing at the top of the list. I ideally though, all communications with IPython should be done through the server, so the debugging commands need work in that respect.

My top priority for this area is the implementation of a more user-friendly preferences / config. method. Here's my initial stab at creating a `nib`. I now need to work out how best to hook it up with `tm_dialog`, to store the preferences. Hopefully recent changes to dialogs in TM will make this easier.

<div class="thumbnail"><a href="http://skitch.com/mattfoster/79d6/ipython-preferences"><img src="http://img.skitch.com/20081209-8b84jym8fpiam2632jyptqr84m.preview.jpg" alt="IPython Preferences" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

Snippets / Scipy
----------------

A lot of IPython users, myself included, are using IPython for scientific computing and number crunching. For that reason, decent support for scientific python libraries is essential.

Thanks to Ben Racine, we've got some decent snippets for [scipy](http://www.scipy.org/ "SciPy -")/[numpy](http://numpy.scipy.org/ "Numpy Home Page")/[pylab](http://matplotlib.sourceforge.net/ "Overview &mdash; Matplotlib v0.98.3 documentation"), and we're adding more fairly regularly. Feel free to send me your ideas, and I'll be sure to implement them if I can.

Documentation and Demos
-----------------------

The bundle documentation is fairly complete, and since it's combined with the README, it's fairly easy to maintain. This is a good thing.

Demo-wise, so far there's only the first [screencast](http://www.vimeo.com/2281439 "IPython TextMate Bundle Demo on Vimeo") I made. I'm extremely surprised to see it has over 200 views, so I'm planning on making more short and sweet screencasts, which we can hopefully integrate with the bundle's help.

You Contributions
-----------------

Are very, very welcome. Please join the [google group](http://groups.google.com/group/ipython-tmbundle/ "ipython-tmbundle |
  Google Groups"), or if you're a gihubber, you can fork the [bundle](http://github.com/mattfoster/ipython-tmbundle/), make your own changes and send me a pull request. Only with help can we make this bundle all it can be.
