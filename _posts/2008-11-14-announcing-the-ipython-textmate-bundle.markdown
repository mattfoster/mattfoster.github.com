--- 
title: Announcing the IPython TextMate Bundle
layout: post
category: textmate
---
After being shown the huge potential of mixing [TextMate](http://macromates.com/ "TextMate — The Missing Editor for Mac OS X") with [IPython](http://ipython.scipy.org/moin/ "FrontPage - IPython") via a [little applescript](http://ipython.scipy.org/moin/Cookbook/UsingIPythonWithTextMate), I started work on the [IPython TextMate](http://github.com/mattfoster/ipython-tmbundle "mattfoster's ipython-tmbundle at master &mdash; GitHub") bundle. I also set up a [google group](http://groups.google.com/group/ipython-tmbundle/), and talked to the ipython-users mailing list. Their response was great, and they've allowed us to discuss the project on the [ipython-dev](http://projects.scipy.org/mailman/listinfo/ipython-dev "IPython-dev Info Page") list, if we tag message subjects with `[TextMate]`. There's also a possibility that we can distribute the bundle with IPython in the future!

Current features in the bundle are mostly related to interaction with IPython in a Terminal (specifically `Terminal.app`), and make use of applescript, and include:

 * running the current file in IPython 
 * running the current line / selection in IPython
 * running the current file / selection / line in IPython with the profiler enabled
 * toggling the state of the debugger (setting this to `ON` will switch into the debugger when an exception occurs)
 * entering the debugger
 * adding breakpoints to the current file 
 * removing those breakpoints
 * growl notification of salient points
 * rudimentary syntax highlighting of `ipythonrc` files, including warnings about broken comments (you can't have a directive and a comment on the same line)
 * commands for editing the `ipythonrc` file and `.ipython` directory 
 * built in help

Most of these functions are accessed by pressing (⌃⇧I), which gives you a list from which you can select the item you wish to activate. This is similar to the Git / Svn bundles. This means you need only remember one shortcut.

<div class="thumbnail"><a href="http://skitch.com/mattfoster/5w6w/re-ipython-menu"><img src="http://img.skitch.com/20081114-8c2399ishtusbsd9tqh3pfi97j.preview.jpg" alt="Re: ipython_menu" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

You can grab this now, from [GitHub](http://github.com/mattfoster/ipython-tmbundle "mattfoster's ipython-tmbundle at master &mdash; GitHub") or [GetBundles](http://svn.textmate.org/trunk/Review/Bundles/GetBundles.tmbundle/). Please send feedback, ideas or comments to the [ipython-dev](http://projects.scipy.org/mailman/listinfo/ipython-dev "IPython-dev Info Page") mailing list, the google group, or directly to me.
