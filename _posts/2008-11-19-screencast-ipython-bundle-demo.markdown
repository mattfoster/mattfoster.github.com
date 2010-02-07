--- 
title: "Screencast: IPython Bundle Demo"
layout: post
category: textmate
---
I'm very pleased to announce that the IPython TextMate bundle is in a state
where it can actually be used – you can probably consider it to be a pre-beta.

To celebrate this, I've made a simple [screencast][1] demoing some of the
basic features. 

<object width="600" height="376"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=2281439&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=00ADEF&amp;fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=2281439&amp;server=vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=00ADEF&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="600" height="376"></embed></object><br /><a href="http://vimeo.com/2281439">IPython TextMate Bundle Demo</a> from <a href="http://vimeo.com/user750148">Matt Foster</a> on <a href="http://vimeo.com">Vimeo</a>.

This screencast can also be [downloaded](http://www.vimeo.com/download/video:86235851?e=1227097770&amp;h=084bca36e3fcbbddffbbbe0c63dc6a49), and I hope to give a quick overview of some of the more advanced features in a follow-up.

The main features of the bundle are:

 * Communication with IPython via the extension ipy_vimserver. This
means the bundle should work right out of the box: just run `import ipy_vimserver; ipy_vimserver.setup('session')`, and you can connect.
   * running the current file in IPython
   * running the current line / selection in IPython
   * running the current file / selection / line in IPython with the
profiler enabled
   * growl notification of salient points
   * rudimentary syntax highlighting of ipythonrc files, including
warnings about broken comments
   * commands for editing the ipythonrc file and .ipython directory
   * built in help
   * access from a single key binding.

The bundle can be downloaded from [GitHub][2] or installed via GetBundles. For
installation help, see the [README][3].

We'd love to hear your feedback, so please send comments, suggestions
and feedback to either the [ipython-dev list](http://projects.scipy.org/mailman/listinfo/ipython-dev "IPython-dev Info Page") (please prefix the subject
with `[TextMate]`), or the [ipython-tmbundle google group](http://groups.google.com/group/ipython-tmbundle/ "ipython-tmbundle |
  Google Groups") (just reply to
this email).

Thanks!

[1]: http://www.vimeo.com/2281439
[2]: http://github.com/mattfoster/ipython-tmbundle/
[3]: http://github.com/mattfoster/ipython-tmbundle/tree/master/README.md
