--- 
title: Playing with iTerm's tabs
categories: 
- ruby
- iterm
- mac
layout: post
date: 2015-01-19
---

[iTerm2](https://iterm2.com/) is *the best* terminal emulator currently available on Mac OSX, I use it daily for development and sysadmin work and rarely regret running unstable builds.

One of my favoute features in iTerm is its tabs. As you'd probably expect, &#8984;T opens a tag – with a new shell – and you can drag and detach them just like you would in other applications. 

Earlier today I was reading its documentation and I came across [this page](https://iterm2.com/documentation-escape-codes.html) about the proprietary escape codes it supports. 

Escape codes are the things you've probably used in the past when you set your term's title or colourised your prompt, but you may not have realised that different terminal emulators have their own sets of codes. There's plenty available to read online, I'll let you search if you're interested :)

iTerm lets you clear history, add to the clipboard, tweak themes and change the colour of tabs.

Anyway, I thought it might be fun to programatically change the colour of iTerm tabs, so hacked up a quick ruby script, using the `color-tools` gem to parse CSS colour names. 

Here it is:

<script src="https://gist.github.com/mattfoster/dc2b6133249cc467d898.js"></script>

Run it like this:

    iterm red

or in a for loop … and here's the resulting awesomeness!

![GIF](http://files.hackerific.net/iterm_tab_colours2.gif)

Good fun, and potentially useful if you use colourcoded tabs to keep track of multiple SSH sessions.

In fact, the best way I've found of using this trick is to put something like this in your `~/.ssh/config` file:

    PermitLocalCommand yes

    Host beefy beefy.local
      LocalCommand ~/bin/iterm blue
      
    Host shrimp shrimp
      LocalCommand ~/bin/iterm red
      
This will change the tab to a specific colour after you've logged in to a configured server. Cool hey?! You can change it back manually using `iterm reset`.

