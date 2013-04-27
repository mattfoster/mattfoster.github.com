--- 
title: Learning Perl (and Perlcritic for TextMate)
categories: 
- textmate
- learning
- perl
layout: post
---
Now, don't just leave straight away, but I'm learning [perl](http://www.perl.org/ "The Perl Directory - perl.org"). I know I've only just started waxing lyrical about python, but bear with me, I've not got any plans to dump anything else: I just need to learn perl for work. (If you read on in this post, you'll find some ruby code, too!)

So, armed with some of the ideas from comments on my [last post](/2009/02/15/best-practices-and-patterns "hackerific: Best Practices and Patterns"), I've tried to build make use of some of the most trendy web resources to help me on my way. Ideally, I'd like to pick up on best practices as I go along.

![information overload](http://farm4.static.flickr.com/3397/3293063926_736d8c02ba.jpg?v=0)

So far though, I'm not having a huge amount of luck. I've worked through [learning perl](http://oreilly.com/catalog/9780596001322/ "Learning Perl | O'Reilly Media"), and I've finished reading it feeling like I don't know anything like the whole story. To be perfectly honest, I'm quite surprised at the complexity of what seems like a small language!

I've got a huge pile of books to help though, so I'm going to start digging through [programming perl](http://oreilly.com/catalog/9780596000271/ "Programming Perl | O'Reilly Media"), and setting myself programming goals. My aim is to work out how to write simple modules and unit tests by the end of next week. I'd also like to find some [rake](http://rake.rubyforge.org/ "Rake -- Ruby Make")/[paver](http://www.blueskyonmars.com/projects/paver/ "Paver: Easy Scripting for Software Projects &mdash; Paver v0.8 documentation") equivalent, and work out how to effectively use `Devel::REPL` (which [stackoverflow](http://stackoverflow.com/ "Stack Overflow") helped me find.) 
Soon I'll have my automation / test safety net at the ready, so things can proceed a little faster.

Whilst casting around, I found [Perl::Critic](http://search.cpan.org/dist/Perl-Critic/ "Elliot Shank / Perl-Critic - search.cpan.org"), a module (and front-end) for checking your code's adherence to best practices (incidentally, there's a great book called [perl best practices](http://oreilly.com/catalog/9780596001735/ "Perl Best Practices | O'Reilly Media") -- another one on the pile!). 

I decided to write a TextMate command for the perl bundle to run code through `perlcritic`, since there isn't one. After a little help from the bundle developers mailing list, I came up with the following:

<script src="http://gist.github.com/67095.js"></script>

To run this, you will *need* a new copy of the TextMate Support directory. I'd suggest using GetBundles. I've sent a patch to the perl bundle to the ML, but in the mean time, if you paste the above code into a bundle command, set the scope to `source.perl`, and trigger to `⇧⌘C`, you should get it working fine.

**Update**: I've just started reading programming perl, and I wish I'd started with it! I'm already feeling like I'm learning more useful stuff than was contained in learning perl. I guess I'm not the target audience of that, but I wish I'd known last week!
