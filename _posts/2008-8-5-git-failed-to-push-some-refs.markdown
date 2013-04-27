--- 
title: "Git: failed to push some refs"
categories: 
- git
- github
- thesis
layout: post
---
I'm keeping my PhD thesis in a private repository on GitHub, because you can never have enough copies. 

A couple of times when I've tried to push, after some fairly major rejigging, I've had the error:

  To git@github.com:mattfoster/thesis.git
   ! [rejected]        master -> master (non-fast forward)
  error: failed to push some refs to 'git@github.com:mattfoster/thesis.git'

Which is obviously quite annoying. [Ed's Elite blog](http://edspencer.net/2008/04/when-git-tells-you-it-failed-to-push.html "Ed's Elite blog: When Git tells you it failed to push some refs") suggests that when this happens you should run `git pull`, manually merge, and then try the push again. ARGH!

A quick google suggested that just using `git push --force` might be easier, and sure enough it is. 

I've no idea if this might have repercussions later on, but I've no reason to expect it will. 

So, as a quick repeat, in case you're skimming:

If you see: `failed to push some refs`, do `git push --force`
 
*Update:* you might find that this breaks some of your history, which could be a problem, especially if you've got people who forked before you did this. Just a quick warning!
