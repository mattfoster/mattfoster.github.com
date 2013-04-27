--- 
title: "Python and Science\xE2\x80\xA6 The Way Forward?"
categories: 
- matlab
- python
- scientific computing
layout: post
---
Every now and then, I get really annoyed with
[MATLAB](http://www.mathworks.com/ "The MathWorks - MATLAB and Simulink for Technical Computing")/[Octave](http://www.gnu.org/software/octave/ "Octave").
The clumsiness of the language, and the way it makes you write so much throw
away code are two particular annoyances, but the main thing that irks me is
that it couldn't be more different than my favourite language,
[Ruby](http://www.ruby-lang.org/ "Ruby Programming Language").

So every now any then, I go on a foray, to see whether the tools I need are
around yet, so I can move closer to dumping MATLAB, and bask in OO glory. I'd
love to have the time to write everything I need from scratch, but
unfortunately I don't, so instead I end up hacking on things that interest me,
and try not to embark on projects I don't have time for.

To give some idea of what I need, here's an example of typical workflow, with
MATLAB:
  
  * Create or load up some image data. This gives me matrices out.
  * Do some processing, using image processing toolbox, including image morphology etc.
  * Extract boundaries, and convert them into some handy spline representation for manipulation.
  * Plot some image data with overlaid boundaries.
  * etc…
  
Whilst I realise that nothing here is particularly complex, it's fairly fast to do in MATLAB, and very slow to do in compiled languages. Things like [ruby-gsl](http://rb-gsl.rubyforge.org/ "Ruby/GSL") are starting to close the gap, in terms of scientific functionality for ruby, but there are still big gaps in other functionality. Gaps that seem to have been filled by [python](http://www.python.org/ "Python Programming Language -- Official Website"). 

So maybe it's time for me to look at python, and [sage](http://www.sagemath.org/ "Sage: Open Source Mathematics Software"), which already has these things.

I'll report back if anything happens!
  
