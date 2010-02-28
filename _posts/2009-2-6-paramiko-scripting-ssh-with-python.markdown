--- 
title: "Paramiko: Scripting SSH with Python "
categories: 
- python
- ssh
- administration
layout: post
---
Python Scriptable SSH 

For a simple way of remotely administering machines, over SSH, with *Python*, have a look at [paramiko](http://jessenoller.com/2009/02/05/ssh-programming-with-paramiko-completely-different/ "jessenoller.com - SSH Programming with Paramiko | Completely Different"). You can grab it using `easy_install`, which can itself be grabbed from [PyPi](http://pypi.python.org/pypi/setuptools "Python Package Index : setuptools 0.6c9"), and installed using `sudo sh easy_install_filename.egg`.

Here's a simple script I rustled up, based on the tutorial. It fires up [mediatomb](http://mediatomb.cc/ "MediaTomb - Free UPnP MediaServer"), on my server `microwave`:

<script src="http://gist.github.com/59318.js"></script>

If you don't like using password-less `sudo`, don't worry, it can cope with that too. That's what the second half of the gist above does.

So, if you use SSH for any kind of repetitive system administration, give the 
[article](http://jessenoller.com/2009/02/05/ssh-programming-with-paramiko-completely-different/ "jessenoller.com - SSH Programming with Paramiko | Completely Different") a read, and give paramiko a try.
