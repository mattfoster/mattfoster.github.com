--- 
title: 'Running a Kippo Honeypot: Part one. Odd passwords'
categories: 
- honeypot
- hacking
- ssh
- kippo
layout: post
date: 2013-04-15
---

[Bed Against The Wall][1] inspired me to try running [kippo][2], an SSH honeypot on a spare CentOS VPS I ended accidentally paying for. 

So far, I've completed a very basic installation by using an iptables rule to redirect traffic from kippo's default port of 2222 to 22 on the VPS' second IP address, created an unprivileged user to run the kippo scripts then started `kippo.sh` as that user.

At the moment, I'm just watching the logs and I've left the default kippo credentials in place (`root/123456`) for about a week. So far, what's interesting is that:

1. All of the brute force attempts I've seen are from Chinese IPs.
2. A lot of the passwords their tools use are pretty odd.

Point one isn't much of a surprise when you consider how much Chinese culture respects hackers, and how their government pretty much turns a blind eye to external hacking attempts, except when you consider that most organised e-crime is perpetrated by Russian speakers. I suppose this means that what I'm seeing is probably just script kiddies playing, which is slightly disappointing as I hope to catch some more interesting behaviour like attempts to install phishing kits or malware.

However, point two is more interesting because of what I think it means. The most commonly attempted passwords are things you might expect, such as:

	  11 111111     
	  11 abc123
	  11 p@ssw0rd
	  16 password
	  23 123456

Where counts are shown on the left -- as you can see I haven't seen a huge number of attempts yet (around 1.5k so far). Most of  these are just passwords from a standard wordlist, and in fact `123456` is kippo's default root password. However, some of the less frequently attempted passwords are things like:

	  sonny2hack
	  7hur@y@t3am$#@!(*(
	  @!#$%&*Th3@#$!F0RcE%&*@#IS!@#$%!&
	  shadow@@@ubyta336331jumjum
	  sipingteam@orangw
	  Th3Bu1ES@VaDCuMm3RgeLak3T3LL1!!!
	  @#$%TheInfinit0fLife@#$%

Which I think are pretty odd. I haven't managed to find much on these passwords (it's dead easy to find lists of attempted password, but not a lot of analysis), but I suspect that they're either passwords which are typically set by exploits or perhaps [root kits][3] or by other script kiddies' attacks. It's hard to imagine that anyone would actually choose to set their root password to `Th3Bu1ES@VaDCuMm3RgeLak3T3LL1!!!`. 

I also wouldn't be surprised if some of these are tried because initial attacks work by spraying and praying masses of servers with one tool and then scanning with a second in order to exploit the potential success of the first. 

Naturally, my interpretation could be totally off the mark but it looks as though most people even semi-diligent VPS-owners have nothing to worry about from this type of attack… and surely nobody actually uses the password from Space Balls? 

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/a6iW-8xPw3k?rel=0" frameborder="0" allowfullscreen></iframe>



[1]:	http://blog.macuyiko.com/2011/03/running-ssh-honeypot-with-kippo-lets.html "Running A SSH Honeypot With Kippo: Let's Catch Some Script Kiddies"
[2]:	https://code.google.com/p/kippo/
[3]:	http://ubuntuforums.org/showthread.php?t=1597383
