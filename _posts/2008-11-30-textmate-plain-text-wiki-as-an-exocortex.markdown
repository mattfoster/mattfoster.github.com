--- 
title: TextMate Plain Text Wiki as an Exocortex
categories: 
- textmate
- bundle
- wiki
- markdown
layout: post
---
I got a copy of [Pragmatic Thinking and Learning](http://www.pragprog.com/titles/ahptl "The Pragmatic Bookshelf | Pragmatic Thinking and Learning") when it came out a while ago, and I just finished reading it. I really wish I'd read it *before* I embarked on a PhD!

As my [girlfriend](http://charliebeldon.com) pointed out, it is basically a psychology textbook, with an onus on learning, but it's presented in that great informal, geek-accessible style that you'll probably only have come across in other pragmatic programmers books. 

I have to admit that reading it in bed probably wasn't the best place, since it made following the advice like "If your software isn't set up with a safety net (version control, unit testing and automation), you need to get that implemented right away. Put the book down. I'll wait." slightly harder to follow, but I still got a heck of a lot out of it, including the idea of an [exocortex](http://en.wikipedia.org/wiki/Exocortex "Exocortex - Wikipedia, the free encyclopedia"). 

An exocortex is basically an external information-processing memory device *thing* which augments your brain. Charles Stross' novel [Accelerando](http://www.accelerando.org/ "Accelerando!") (which is available online) will help explain, if you're interested. For now though, we have to make do with (normal) computers to augment us, so that basically means wikis.

Inspired by a couple of screenshots in Pragmatic Thinking and Leaning, I searched the web for a wiki that runs inside of [TextMate](http://macromates.com/ "TextMate — The Missing Editor for Mac OS X"), and stored everything in flat files. I found [Plain Text Wiki](http://interconnected.org/home/more/2007/05/textmate-wiki/ "Index of /home/more/2007/05/textmate-wiki"), a bundle which did some of what I wanted, including exporting to HTML, and following links by pressing `⌅`

I created a [fork on GitHub](http://github.com/mattfoster/plaintextwiki-tmbundle/tree/master "mattfoster's plaintextwiki-tmbundle at master &mdash; GitHub"), and set about modifying it. Changes I've made include fixing the backend to work on my Mac, copying the matkdown language grammar into it (since TM's markdown grammar isn't really extensible), and a wiki mapper.

For the mapper, I've used [nodebox](http://nodebox.net/ "NodeBox | Home"), and a short script to generate nodebox code and fire it up. The results look like this (and are animated in nodebox):

<div class="thumbnail"><a href="http://skitch.com/mattfoster/7dh9/wikimap"><img src="http://img.skitch.com/20081130-js5ubri5tg3ta1kr46j391xe2i.preview.jpg" alt="wikimap" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

Feel free to fork it yourself. I've got lots of ideas, like moving to a git based wiki system (like [git-wiki](http://github.com/sr/git-wiki/tree/master)), auto-publishing, and using a templating system.
