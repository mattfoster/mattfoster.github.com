--- 
title: Bluetooth Device Scanning
categories: 
- bluetooth
layout: post
---

During the middle of January 2010, I (inadvertently) left a bluetooth inquiry scanner running for about four days. I live on a fairly busy street in Bath, so during that time I collected information on almost 1500 bluetooth gadgets, ranging from headsets and car handsfree kits, to phones, PDAs and computers. This article is about some of the patterns I've found in the data. But first, some background.

Bluetooth enquiry scans can provide a huge amount of information about discoverable bluetooth devices. I use 
[btscanner](http://www.pentest.co.uk/cgi-bin/viewcat.cgi?cat=downloads&section=01_bluetooth "Downloads") for to look for bluetooth devices, and whilst it can sometimes be a little flakey, I've had good results. btscanner outputs one directory for each device is finds, inside each directory is a file containing useful information, and another containing the times at which the device was seen. Among the most useful information is the bluetooth address of the device. 

Bluetooth addresses look exactly like ethernet MAC addresses and serve the same purpose. They also use the same OUI, which I've talked about the OUI database in a [previous post](/2010/04/04/oui), so I won't go into any more detail here. 

I analysed the data I collected with some simple shell and (work in progress) ruby scripts. After that, I used Gnuplot to make some bar graphs. Here's the number of devices made by different manufacturers:

![Bluetooth Manufacturer Frequencies](/images/posts/jan_by_manufacturer.png)

This shows just how common Nokia devices are in the UK, and suggests that they tend to leave Bluetooth enabled by default. This differs from Apple and Android phones which are configured to leave Bluetooth disabled to conserve battery.

When I looked at the list of manufacturers, I noticed that TomTom was near the top, so decided to delve a little further and plot the the frequencies of the device classes too. Class designations are quite granular, so smart phone is distinct from mobile phone, and PDA is distinct from laptops:

![Bluetooth Class Frequencies](/images/posts/jan_by_class.png)

Sure enough GPS is the third most popular class. But hands free is surprisingly prevalent too. This begs the question why are these devices discoverable? If they're acting as hands free kits, there's certainly no need. And if it's for keeping them up to date, there's definitely no need leave it enabled whilst driving. People could connect and play audio!

In my next post, I'll try and pull out some more interesting bluetooth data, including device names. I've also collected some more recent data, so it might be interesting to see if the trends have changed.
