--- 
title: "Z-shell productivity: the prompt and title"
categories: 
- zsh
- shell
- github
- prompt
layout: post
---
I've recently been playing with a cool project on GitHub:
[zshkit](https://github.com/bkerley/zshkit/) . It's a basically just way of organising
your [zsh](http://www.zsh.org/ "Zsh") config files, but it's inspired me to
look at improving my shell productivity and I hope to post a few times about
this.

One of the many changes I made to [my fork](https://github.com/mattfoster/zshkit/) of
zshkit, is to minimise the prompt. It's something I've not really considered
before, and I've pretty much always used something a lot like
[gentoo](http://www.gentoo.org/ "Gentoo Linux -- Gentoo Linux News")'s
default. Here's a screenshot of my new prompt and title:

![Minimalist Prompt](http://img.skitch.com/20081012-m21ferbnp6b9bmu5trga8abjsj.jpg)

The top line shows the prompt when outside of a 
[git](http://git.or.cz/ "Git - Fast Version Control System") repository and the bottom shows how it looks
from within one. Normally, it shows the current directory on the left and the
last command's exit status (a yellow `$` means a failure). When I'm inside a
git repository, it shows the current branch, with the branch name coloured
cyan when the repository is clean and magenta when there are pending changes.

This only really works when coupled with a decent title in your terminal. Whilst looking around, I found [_why's](http://dotfiles.org/~_why/.zshrc "dotfiles.org | _why | .zshrc") which seems to work really well and is what you can see at the top of the screenshot. The next step would seem to be _why's [screenrc](http://dotfiles.org/~_why/.screenrc "dotfiles.org | _why | .screenrc"), but I don't really ever use screen, despite being aware of the awesomeness.

My prompt is it github, with everything else:

  * [`prompt_git_setup`](http://github.com/mattfoster/zshkit/tree/63d38051352965db063f7495818bef5905cfa7a4/func/prompt_git_setup "func/prompt_git_setup at 63d38051352965db063f7495818bef5905cfa7a4 from mattfoster's zshkit &mdash; GitHub")
  * to use it, you need something like this: [`git-prompt`](http://github.com/mattfoster/zshkit/tree/63d38051352965db063f7495818bef5905cfa7a4/06_git "06_git at 63d38051352965db063f7495818bef5905cfa7a4 from mattfoster's zshkit &mdash; GitHub")
  * and something like this in your rc files:
  
        autoload promptinit && promptinit && prompt git
 
It's probably easier to [fork your own zshkit](http://github.com/bkerley/zshkit/fork) and go from there.
