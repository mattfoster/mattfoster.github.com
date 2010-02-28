--- 
title: Gnuplot Bundle for TextMate
categories: 
- gnuplot
- textmate
- bundle
layout: post
---
I've recently started developing a [Gnuplot](http://www.gnuplot.info/ "gnuplot homepage") bundle for [TextMate](http://macromates.com/ "TextMate — The Missing Editor for Mac OS X"), and I've decided to host it on [GitHub](http://github.com/ "Secure Git hosting and collaborative development &mdash; GitHub"). Like a lot of people, I've recently started using Git instead of [SVK](http://svk.bestpractical.com/ "HomePage - SVK Wiki"), my previous choice of distributed VCS and [SVN](http://subversion.tigris.org/ "subversion.tigris.org"), so hosting on GitHub seemed a natural choice; plus how could I possibly ignore their cool [network graphs](http://github.com/Caged/gitnub/network)?! 

Gnuplot is an incredibly versatile and complex piece of graphing software which runs on a lot of different platforms, and can output even more different formats. I use it a lot at work (in [publications](http://files.my-mili.eu/interp_rev.pdf), for example), and so I decided it was about time my favourite Mac editor had better support for it. 

Of particular note are(/will be) autocompletion of terminal types, settings and plot commands; as well as snippets, and the ability to run your commands from TextMate and view the output in [aquaterm](http://sourceforge.net/projects/aquaterm/ "SourceForge.net: AquaTerm (Mac OS X graphics terminal)"). I'm looking forward to making it as useful as I can, and collaborating with anyone who fancies giving me a hand.

![gnuplot_bundle_shot](http://files.my-mili.eu/2008-04-18_gnuplot_bundle_shot1.jpg)

You can grab the bundle from GitHub using the following commands:

<pre>
cd ~/Library/Application\ Support/TextMate/Bundles
git clone git://github.com/mattfoster/gnuplot-tmbundle.git Gnuplot.tmbundle
osascript -e 'tell app "TextMate" to reload bundles'
</pre>

Feel free to jump in and help out--- I'm new to writing TextMate bundles.
