--- 
title: '2015 Security Tool Roundup'
categories: 
- security
- tools
layout: post
date: 2016-01-11
---

2015 year was an another interesting year for security and some cool utilities
appeared. Rather than cover the same old ground and gush about how amazing
[nmap](https://nmap.org),
[masscan](https://github.com/robertdavidgraham/masscan) and
[shodan](http://shodan.io) are though (not that they're not amazing, of
course), I'd like to highlight a few lesser known tools I've found useful, and
discovered in the last year.

## TLS Prober

One of my favourite security projects last year was undoubtedly [TLS
Prober](https://github.com/WestpointLtd/tls_prober). 

This is a great recon tool which attempts to identify a given SSL stack by
examining its behaviour. For full details, see the
[whitepaper](https://github.com/WestpointLtd/tls_prober/blob/master/doc/tls_prober.md)
included in the project repo.

You can run TLS Prober against lots of different service types, including some using
STARTTLS, and it will give you a list of the most likely SSL stacks, along with
the number of signatures for each match

This can be really useful for OS identification if you can't find `Server`
response headers or other useful indicators, since it can distinguish
Microsoft's SChannel from, say, OpenSSL.

This project hasn't seen as much love as it deserves, but I'm hoping more
people will jump in and provide fingerprints. Currently, for example, I
sometimes see it identify Postfix on CentOS 7 as Fortigate (since apparently
they look identical!).

If you're interested in network recognisance tools you should definitely check
[TLS Prober](https://github.com/WestpointLtd/tls_prober/) out, and submit some
new signatures. It could also prove you with inspiration to help writing tools of your own.

## WAFW00F

[WAFW00F](https://github.com/sandrogauci/wafw00f) is another interesting recon
tool, designed to identify web application firewalls. It does this by making
various HTTP requests and then examining the responses for telltale signs that
certain WAFs are present. Things like cookies, headers, and other responses to
certain stimuli. 

Check it out and submit any handy improvements you might have in mind -- the
developers are [open to pull requests](https://github.com/sandrogauci/wafw00f/commit/cd50b3ada9eb3f839707322875001e79e161580d).

## ncat 

I said I wouldn't mention nmap, but I'll mention one of its projects, ncat.
[ncat](https://nmap.org/ncat/) is the [nmap](https://nmap.org/) project's reimagined
netcat. Use it in most of the places you would usually have used either netcat
or `openssl s_client` in the past. For example, to view an SSH banner:

    ~ % ncat scanme.nmap.org 22
    SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3

Or to cat a file across the network, using encryption:

    cat korg.tiff| ncat -l --ssl -p 1234

This is another tool that's worth a look, and if you have nmap, you probably already
have it installed.

## Finally

There are lots of blogs which cover security tools. One I particularly like is
[darknet.org.uk](http://www.darknet.org.uk/), and I'd recommend giving their post 
[A Look Back At 2015 – Tools & News Highlights](http://www.darknet.org.uk/2016/01/a-look-back-at-2015-tools-news-highlights/)
a look. 

This is a really short list of interesting things I found last year. Please
leave a comment if I'm missing a handy tool you've found useful.
