--- 
title: Online Help in the Gnuplot Bundle
categories: 
- gnuplot
- textmate
- bundle
- help
layout: post
---
On of the things that makes [gnuplot](http://www.gnuplot.info/ "gnuplot homepage") so powerful is its dazzling array of options. With this great number of options comes a heavy reliance on the manual, and this has meant that until recently, when I was scripting graphs for my thesis I had to have [TextMate](http://macromates.com/ "TextMate — The Missing Editor for Mac OS X") and a terminal running gnuplot fired up, and keep on switching between them when I needed to get some help.

That's why I decided to add support for gnuplot's built-in help into the [Gnuplot bundle](https://github.com/mattfoster/gnuplot-tmbundle/). One of the many useful things about the gnuplot help is that it looks quite a lot like markdown. In particular, lots of code is delimited by back-ticks and larger snippets are indented, just like markdown requires. This means that it's easy to convert it to HTML, and display it in TextMate's HTML viewer.

The result: select a gnuplot keyword, press ⌃H, and read the output.

![Gnuplot Help](http://files.hackerific.net/2008-05-30_gnuplot_help.jpg)

Another couple of features which I'm too proud of not to mention are:

  * A search bar at the top of every page, allowing you to enter topics if you asked for help on the wrong thing, or read something in the text you want more information on.
  * Linked entries when a search is ambiguous.

I'm currently working on adding links to other topics, such as subtopics, and hopefully that won't be too long coming.

Try it out, and give it a go. Installation instruction can be found on the [Gnuplot bundle](https://github.com/mattfoster/gnuplot-tmbundle/) [Github](http://github.com/ "Secure Git hosting and collaborative development &mdash; GitHub") page.

I'm always open to suggestions or collaborations.
