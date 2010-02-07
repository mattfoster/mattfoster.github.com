--- 
title: My MacHeist Release Estimate
layout: post
category: software
---
Like a lot of mac users, I get excited about MacHeist, and why not, it's fun and a good bargain.

Since we're snowed out of work, and a MacHeist Bundle release seems imminent, I decided to hack up a quick script to find out how wide the progress bar thing is, and use that to estimate the release time. Here's what I've been up to for the last half hour or so:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/bd2ut/macheist-mainframe"><img src="http://img.skitch.com/20090206-nd331ywttf11ypf684ehdr5scr.preview.jpg" alt="MacHeist: Mainframe" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

I used [BeautifulSoup](http://crummy.com/software/BeautifulSoup "Beautiful Soup: We called him Tortoise because he taught us.") with [urllib2](http://docs.python.org/library/urllib2.html "urllib2 — extensible library for opening URLs &mdash; Python v2.6.1 documentation") and a tiny regular expression, and here's the result:

<script src="http://gist.github.com/59370.js"></script>

I'm running it in a simple shell loop:

      while true; do sleep 60; python heist_parse.py >> heist_countdown; done 
	
Which is collecting the width every minute (that doesn't seem too often).

Now that I've had this loop running for a while I've got 34 data points, so I can do a bit of simple linear regression, with [scipy](http://www.scipy.org/ "SciPy -"). Here's a graph:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/bd2ik/macheist-release-estimate"><img src="http://img.skitch.com/20090206-8cess4fmajn5b741bgf1w8mqkg.preview.jpg" alt="macheist_release_estimate" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

And here's the code used to do the regression, and generate the plot.

<script src="http://gist.github.com/59382.js"></script>

It's important to remember that this is based on the assumption that the bar is full up at **500** pixels wide. This may or may not be reasonable.
 
If it is though, I'd tentatively estimate that the bundle will be release at **3AM (GMT) on the 7th Feb 2009**. You read it here first!

**Update:** Well, it looks like they cheated! Here's a graph of the bar's length with time:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/bd49m/rounded-up"><img src="http://img.skitch.com/20090206-k9eynh3auxkny255jttwtdafcm.preview.jpg" alt="Rounded up!" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

As you can probably see, it was rounded up. Ahh well. So much for the estimate!
