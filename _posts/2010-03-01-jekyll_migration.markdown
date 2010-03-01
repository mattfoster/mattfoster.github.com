--- 
title: Jekyll Migration and GitHub Hosting
categories: 
- blog
- site
- github
- hosting
layout: post
---

I've been working on moving my blog to GitHub, and I've ported it to [Jekyll](http://wiki.github.com/mojombo/jekyll "Home - jekyll - GitHub"). This means it should be faster and more secure than Mephisto, which was always stuck several versions behind the current release. 

It should be obvious to any past visitors that I've had a go at redesigning the site. The new design is based on [mojombo's](http://github.com/mattfoster/mattfoster.github.com "mattfoster's mattfoster.github.com at master - GitHub")) and as so as with his repository everything but the `_posts` directory is MIT licensed.

Whilst getting everything set up I had to make some changes and tweaks to some scripts to get the behaviour I wanted. I'll list these below.

First off is my [Rakefile](http://github.com/mattfoster/mattfoster.github.com/blob/master/Rakefile "Rakefile at master from mattfoster's mattfoster.github.com - GitHub"). This is used to build `tags.html`, since as far as I can see, there's no easy way to enumerate tags in Jekyll 0.5.7 (and I can't use a custom for for GitHub hosting). My Rakefile is based on one I found at [http://gist.github.com/143571](http://gist.github.com/143571 "gist: 143571 -  GitHub"), and uses Jekyll to loop through the blog's categories and generate lists. I've opted to sort the list by the number of posts in each tag, and added some JavaScript to collapse the lists. Anchors take the place of individual tag pages in Mephisto and other engines. 

Next, Jekyll ships with converters for importing posts from various blogging engines. The Mephisto script didn't support tagging, so I hacked the SQL to pull out the tags too. Here's a gist of my modified code:

<script src="http://gist.github.com/318743.js"></script>

I'm certain that the SQL could be simplified fairly easily by someone who isn't so much of an MySQL newbie.

I googled for information on Jekyll sitemaps, and found a useful post on [squarepush](http://squarepush.com/articles/2009/08/10/jekyll-sitemap-xml/ "Pushing Squares - Jekyll Sitemaps") containing just what I needed. I ended up with the following:

<script src="http://gist.github.com/318844.js"></script>

This does exactly what you'd expect.

Finally, a minor change which I hope will not cause too many problems is the Jekyll permalink setting. I've added:

    permalink: /:year/:month/:day/:title

To my `_config.yml`. In order to paths as close as possible to my URL scheme on Mephisto. This might cause a few problems in cases where the year or month names are only one digit long; Jekyll pads them with a leading zero, whereas Mephisto didn't. Hopefully this won't manifest as anything more serious then broken links.
