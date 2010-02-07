--- 
title: MEX Support in Octave
layout: post
---
I used to be a fairly heavily [Octave](http://www.octave.org/ "Octave") user,
but when I started my PhD I had to use MATLAB for some specific toolboxes. I
found this quite annoying, because I think MATLAB is big, and slow, and clunky
(and leaks memory). So I'm quite happy to report that I think that this might
be about to change.

On December 21 2007, Octave 3 was released. Now, I'm not sure if this is
relevant to this post, but it did prompt me to upgrade, and since I was
playing with some MEX (MATLAB external interface) files, I decided to see if I
could make them work with Octave.

Well, I could. And that's the cool thing -- I didn't have to change anything.
I just typed `mex morpho.cpp` and out popped an object file. There was no fuss
at all, and no difference from MATLAB. I think this is a really good
development for Octave, as it plugs what I've always found to be a fairly big
gap between Octave and MATLAB's functionality. I'll be trying this with some
of my other MEX stuff, and I'll report back here with any new findings -- I'm
expecting it all to go fairly smoothly though!
