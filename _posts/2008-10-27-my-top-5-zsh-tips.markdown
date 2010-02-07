--- 
title: "My top 5 ZSH tips! "
layout: post
---
Since reading [this question](http://stackoverflow.com/questions/43321/worth-switching-to-zsh-for-casual-use#83754 "Worth switching to zsh for casual use? - Stack Overflow") on [stackoverflow](http://stackoverflow.com/ "Stack Overflow") I've been intrigued by zsh, and looking at cool things it can do to make my life easier. I decided to jump on the top-*n* things bandwagon and publish a quick list of zsh bits I find really useful.

Here's a quick list of my top five tips:

  1. Try using zsh's awesome `for` loops: 
  <pre>for file (prefix*) $file:s/prefix/new_prefix/</pre>
  or if you want more than one command in the body, try: 
  <pre>for file (prefix*) {one; two; three}</pre>
  2. Use numerical ranges for operating on batches of files:
  <pre>{0..10}</pre> 
  will give you a range of values, which you can use in a loop (`for n ({0..10})`), and 
  <pre><0-10></pre> lets you match ranges of digits in filename globs.
  3. Use variable replacements to quickly munch filenames <pre>$variable:s/thing/other_thing/g</pre> But alas, there's no support for regular expressions in these.
  4. Try globbing instead of using find: 
  <pre>\*\*/\*.png</pre> will find all `png` files beneath your current directory. You can use this in a loop too:
  <pre>for f (\*\*/\*.txt) {echo $f}</pre>
  5. Use [zsh-lovers](http://grml.org/zsh/zsh-lovers.html "ZSH-LOVERS(1)") to find out more. There's far too much to zsh for me to be able to list it all here. My first stop is usually this man page, and it's usually all I need.
  
  * **Bonus!** Google for zshrc config files. Try [github](http://github.com/ "Secure Git hosting and collaborative development &mdash; GitHub") and [dotfiles](http://www.dotfiles.com/ "dotfiles.com: home") first. 

