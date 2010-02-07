--- 
title: ZSH Abbreviations
layout: post
categories: 
 - zsh
---
Abbreviations are ZSH feature I just stumbled across, whilst proselytising about [GRML](http://grml.org/ "grml.org - Linux Live-CD for sysadmins and texttools-users"), a cool linux distro. 

Here's a snippet to show you the [ultimate power](http://www.realultimatepower.net/ "Are you ready to get pumped") they offer:

<script src="http://gist.github.com/51050.js"></script>

OK, so it may not make much sense as it stands, but bear with me. Suppose you want to get some information about the size of the directory tree you're in. Now, you want to use something like `du -sch`, traditionally, you might have `alias da='du -sch'` in a config. file, but what if you want to edit it at the last minute. The abbreviation lets you do just that. If you type `da,.`, the `,.` trigger expands the abbreviation to give you `du -sch` on the command line, and then you can further edit the command, to add that extra `x`, or whatever, afterwards. This is obviously a somewhat contrived example, but the effort saving, productivity enhancing idea is still there, and it fits in well with the [ZSH](http://www.zsh.org/ "Zsh") philosophy, or my version of it at least. 

To see what I mean, look at the `magic-space` command. If you use:

		bindkey ' ' magic-space 

Then use history, or some other shell expansion, it will be fully expanded when you hit space. Did you miss the colon on the end of that `scp` command three lines ago? No problem, hit `!-3␣`, add it, and hit return. It feels similar to the abbreviation mechanism above, and is very powerful too.

It's worth noting that the [original sighting](http://github.com/strcat/dotfiles/blob/ea3521faeb94d91ae84186b00d2a660ef6bdac48/zsh/zshmisc "zsh/zshmisc at ea3521faeb94d91ae84186b00d2a660ef6bdac48 from strcat's dotfiles - GitHub") of this trick doesn't seem to be compatible with the 'magic-space', since it rebinds space. 

You can find all of this, and more, in my [zshkit](http://github.com/mattfoster/zshkit).
