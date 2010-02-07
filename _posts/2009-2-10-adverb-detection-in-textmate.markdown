--- 
title: Adverb Detection in TextMate
layout: post
category: textmate
---
After seeing [lifehacker](http://lifehacker.com/240522/lifehacker-code--the-ly-detector-greasemonkey-user-script), I was inspired to add an adverb detector to TextMate's markdown grammar, since that's the format I use to write blog posts. 

Far from being a couple of hours work, this was dead simple, and involved adding a couple of tiny bits to the grammar, here's how to do it:

First, fire up TextMate's `Bundle Editor`, press `⌃⌥⌘B`. Then scroll to markdown, expand it, and find the Markdown Language grammar. This will be marked with a small grey `L`. Add the following to the `repository` section:

		adverb-detector = {
			name = 'invalid.adverb';
			match = '(?!\b(supply|apply|family|only|prolly|folly|sully|rally|waverly|reply|early|probably)\b)\b(\w+ly)\b';
		};

Now scroll to the section headed `inline`, and add:

		{	include = '#adverb-detector'; },

To the `patterns` part. Finally, check you have a rule called `Invalid` in your TextMate theme, with the scope selector `invalid`. This rule is used to highlight a multitude of sins, so it's probably already in your theme. Mine looks like this:

<div class="thumbnail"><a href="http://skitch.com/mattfoster/brgqd/invalid-selector"><img src="http://img.skitch.com/20090210-fu4tuujj2inxge1994f3mfxx1m.preview.jpg" alt="invalid_selector" /></a><br /><span style="font-family: Lucida Grande, Trebuchet, sans-serif, Helvetica, Arial; font-size: 10px; color: #808080">Uploaded with <a href="http://plasq.com/">plasq</a>'s <a href="http://skitch.com">Skitch</a>!</span></div>

<img src="http://img.skitch.com/20090210-b42mb5qkccbqa2xg6gib53361q.png" alt="adverb_detection.mdown"/>
