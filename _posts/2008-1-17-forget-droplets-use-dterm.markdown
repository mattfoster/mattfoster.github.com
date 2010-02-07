--- 
title: Forget droplets, use Dterm!
layout: post
---
A few days ago, on one of my regular [del.icio.us/popular](http://del.icio.us/popular/ "Popular pages on del.icio.us") <strike>procrastination</strike> research trawls, I discovered [DTerm](http://www.decimus.net/dterm.php "DTerm"), a HUD style, context-sensitive, drop down command line thingemy. It's pretty cool, with useful features like 'insert selected items', and 'copy results' and after a couple of updates I can see it being totally great. 

Here's a quick screenshot:  ![Dterm](http://files.my-mili.eu/2008-01-17_dterm1.jpg)

I'd recommend taking at look at their site for a more complete screencast with some useful ideas.

If you've previously used [droplets](http://henrik.nyh.se/2007/10/open-in-textmate-from-leopard-finder) for things like launching [TextMate](http://macromates.com/ "TextMate — The Missing Editor for Mac OS X"), this might be perfect for you, since instead of having to click, you can just bash the hotkeys, and type `mate letter.tex` or whatever. You could also dispense with the [open terminal here](http://henrik.nyh.se/2007/10/open-terminal-here-and-glob-select-in-leopard-finder) droplet all-together. I'm thinking of trying to hack the glob select droplet (above) to work from the command line as well, but I'm not sure how easy that will be.

Here are a couple of other ideas I've had:

 * `du -shx ⇧⌘V` -- to view the size of the currently selected items (works in finder/textmate/etc.).
 * `open .` -- to view the current directory in finder.
 * `⌘↩` -- on it's own to fire up a Terminal in the current working directory.
 * Basically, most things you'd normally switch to the terminal for, you can do with DTerm.

Since I use zsh instead of bash, I found (after talking with Decimus' support) that I need to launch Dterm using:
<pre>
env SHELL=/bin/bash open /Applications/DTerm.app 
</pre>
Otherwise it'll use zsh, which stops tab completion from working properly. Using this method, you could also pass other options, such as `TERM`, which DTerm doesn't currently set itself. The command I'm using at the moment is:
<pre>
env SHELL=/bin/bash TERM=dterm open /Applications/DTerm.app 
</pre>
Give it a try!
