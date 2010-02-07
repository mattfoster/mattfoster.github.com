--- 
title: Making 'home' and 'end' behave in Leopard's Terminal.app
layout: post
---

I don't remember ever having the `home` or `end` keys working the way I like them in `Terminal.app`, but I was recently playing with the new settings interface, and I found the keyboard section. The default, 'basic' profile looks like this:

![Terminal Settings](http://blog.my-mili.eu/files/Settings-1.jpg)

Where the 'Action' column is the key-code, or action that gets emitted when a given key
is pressed. The default for the 'end' key is: 

![Terminal Settings - End](http://blog.my-mili.eu/files/2007-11-20_terminal_settings_end.jpg)

That quite simply means move to the end of the window (or as far down as possible). 
The 'home' key's default is the opposite of this. Pretty useless, right?

I've used [zsh](http://www.zsh.org/ "Zsh") for a while now (I'll put my newest configs on the web in a while), and so I'm used to a good amount of control, and power, and I'm also used to my home and end keys doing what I expect. On other systems I've used [zkbd](http://www.openbsd.org/cgi-bin/man.cgi?query=zkbd&sektion=4 "Manual Pages: zkbd(4)"), which maps key-codes to actions, but until recently my home and end keys didn't emit codes. That's because they just zoom to the start or end of the buffer.

Here's how I fixed it, and made home and end work again:

First, make yourself a profile, and flip into the keyboard segment of the settings. 
Choose 'end', and press 'edit', you'll get something which looks like this:

![Terminal action settings](http://blog.my-mili.eu/files/2007-11-20_terminal_action_settings.jpg)

You need to choose `send string to shell`, and make the text entry look like mine.
To do that, type `Control + [`, which ought to give you the `\033`, and follow it by another `[`, a `4` and a tilde `~`. That should be the end key sorted. Now, you need to do the same for the 'home' key, only instead of the `4`, use a `1`. 

Now, provided you have your shell set up correctly, it should work!
