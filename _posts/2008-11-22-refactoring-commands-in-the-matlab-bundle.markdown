--- 
title: Refactoring Commands in the MATLAB Bundle
categories: 
- textmate
- bundle
- matlab
- github
- svn
- refactoring
layout: post
---
Sometimes, after seeing a few things, concepts collide (like icebergs, perhaps), and I come up with ideas I think are cool. Here's one of those:

<object width="600" height="376"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=2307006&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=00ADEF&amp;fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=2307006&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=00ADEF&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="600" height="376"></embed></object><br /><a href="http://vimeo.com/2307006">Refactoring with the MATLAB bundle</a> from <a href="http://vimeo.com/user750148">Matt Foster</a> on <a href="http://vimeo.com">Vimeo</a>.

For those of you who prefer some code, say you have a big long ugly line of code. You know it's bad, but it works and you don't want to break it. Here's an example, very, very loosely based on some Matlab code I saw at work:

<script src="http://gist.github.com/27893.js"></script>
 
The obvious thing to do, is pull out that evil range `-pi:0.1:pi`. With the new 'Introduce variable' command (bound to `⌃⇧C`, by default), you can do this be selecting any on of them, and running the command.  

You'll see a dialogue box asking you for a name for you new variable, and after you press OK, you'll see the following:

<script src="http://gist.github.com/27895.js"></script>

Much better. You can also repeat the process to further simplify the line, and the command will insert the new variable before the first instance it finds. Cool hey?!

This command is also general enough that is should work for most languages that use assignments based on `=`. For more info on this concept, see [refactoring.com](http://www.refactoring.com/catalog/introduceExplainingVariable.html "Refactoring: Introduce Explaining Variable"), which I shall also be scouring for more ideas.
