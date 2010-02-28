--- 
title: "TextMate Command: Add comments to end of line"
categories: 
- textmate
- python
- command
- comment
layout: post
---
After reading [this message](http://www.nabble.com/insert-end-of-line-comments-td20993813.html "Nabble - textmate users - insert end-of-line comments") on the textmate-users mailing list, I decided to have a go at writing a command to add comment chars to the ends of lines. Here's what I ended up with:

<script src="http://gist.github.com/35668.js"></script>

To use it, create a command in TextMate's bundle editor, then make a new command, and set the input and output dropdowns to look like this:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/6xkj/end-of-line-comments"><img src="http://img.skitch.com/20081214-xhyj3h6echprtqprm5jeymgbg1.preview.jpg" alt="end-of-line-comments" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

Finally, set up scope selections (e.g. `source.python, source.shell`, …), and a key binding if you want one.
