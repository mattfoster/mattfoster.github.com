--- 
title: History meme redux...
categories: 
- zsh
- shell
- unix
- linux
layout: post
---
Following on from [ones zeros majors and minors](http://ozmm.org/posts/git_bash_aliases.html) and [Panasonic Youth](http://robsanheim.com/2008/04/16/history-meme-onwards/), I humbly present my top 10 zsh commands: 

		matt@pyxis ~ $ history 0 | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | \ sort -rn | head 
		2151 l 
		1376 cd 
		631 git 
		463 echo 
		343 open 
		341 mate 
		279 sudo 
		258 gnuplot 
		243 ll 
		241 rm 

Interestingly, it's quite different on my work linux box: 

		1437 ls 
		1009 cd 
		315 svk 
		289 sudo 
		203 vim 
		189 rm 
		182 grep 
		178 mv 
		133 gvim 
		131 feh 

And it depends on what I'm up to at any given time :)
