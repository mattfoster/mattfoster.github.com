--- 
title: "Quick hack: Samsung SGH-F400 and iSync"
layout: post
---
*Warning*: this is properly hackerific! 

I just got a Samsung SGH-F400, instead of what I really wanted (an iPhone), because [Orange](http://www.orange.co.uk/ "Orange UK Home Page") dropped my line rental so much to get me to stay.

It arrived today, and one of the first things I tried, was getting it to sync, with iSync. Which didn't work.

I got a copy of the [novamedia](http://www.novamedia.de/ "nova media | Use a cell phone with your Macintosh Computer: Manage files, Sync, SMS and mobile Internet") plug-ins, for my SGH-D500, so I've plenty of Samsung plug-ins laying around, but not one for this. so I decided to see what a bit of quick hacking would do for me.

Here's what I did:

  * Fire up a terminal, and navigate to `/Library/PlugIns`, there are rather a lot of things in there.
  * Now open up `Samsung-F490.phoneplugin`. This is just a bundle, so in my case, I just did: `mate Samsung-F490.phoneplugin` to open in it as a project in TextMate.
  * Open up `MetaClasses.plist`, go to line 11 and duplicate it. In TextMate you can hit  `⇧⌘L 11`, then `⇧⌘D` to do this. 
  * Change the `490` to `400`.
  * That's it. 

Now if you make the phone discoverable, and enable secure mode, you should be able to add it to iSync, and copy your contacts across. The icon will be wrong, but it works!
