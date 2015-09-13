--- 
title: 'TextMate 2 and the Gnuplot bundle'
categories: 
- gnuplot
- textmate
- bundle
layout: post
date: 2015-09-13
---

Since finishing my PhD and leaving the world of academia I've moved from doing most dev work locally using [TextMate](https://macromates.com/) to using remote VMs and using [vim](http://www.vim.org/). I've also spent less time hacking outside of work, and so a few of the projects I used to spend a fair amount of time on have fallen by the wayside.

One of these poor languishing projects was the Gnuplot TextMate bundle. A lot has happened to TextMate in the six years(!) that have passed since I first started hacking on the bundle, with the main event being the appearance of TextMate version 2.0!

After a couple of mails about getting the bundle working on TM2, I found some time to have a play, and I'm now pleased to report that most bundle functionality now **works in TextMate 2**.

As before, you can find the bundle on github: https://github.com/mattfoster/gnuplot-tmbundle/

Please see the README for installation instructions.

## Converting to TM2

Converting the bundle wasn't too difficult, and most of the problems were caused by the fact that most of the 'Bundle Support' code is still written to use Ruby 1.8. Thankfully, there's a wrapper `ruby18` you can use, so many problems can be fixed by switching shebang lines from:

    #! /use/bin/env ruby
	
to
	
    #! /use/bin/env ruby18

as the Bundle Support `plist` adds the `ruby18` wrapper to TextMate's path.

The `TM_BUNDLE_PATH` variable seems to have been replaced, but you can now use paths relative to `TM_BUNDLE_SUPPORT` instead.

I also made a few changes to set the working directory used when running GnuPlot, and some miscellaneous other tweaks. The result is that most, but not all, of the functionality should now work.

If you find something missing, or broken, please file an [issue](https://github.com/mattfoster/gnuplot-tmbundle/issues) on GitHub, and I'll look at sorting it. 

The main thing I noticed while playing with this is that the community surrounding TextMate seems to have dissipated somewhat. This is probably because some many new and shiny editors have appeared, with Sublime Text and Atom among the most popular. 