--- 
title: Bluetooth Survey January 2011
categories: 
- bluetooth
- survey
layout: post
---

Last year (in my last post!), I had fun scanning for bluetooth devices on a
busy road in Bath, UK (where I happen to live), so this year I decided to
repeat the experiment.

This year, instead of running btscanner, which logs results as a directory per
device, I decided to go with running `hcitool inq` on my debian server, and
catting the results into a text file. This unsophisticated approach has the
advantages that I get timestamps along with my data, and generate less radio
chatter (which was interfering with my wireless network :().

Here's what I found when I ran my analysis code.

First, like last year, here's a graph showing the frequency of different manufacturers.

![Bluetooth Manufacturer Frequencies](/images/posts/jan2011_by_manufacturer.png)

Once again, Nokia, Samsung and Sony Ericsson are top, but this year sees RIM
jump in popularity to fourth place (from seventh). 

Perhaps the most interesting addition to this year's graph is 'Contintenal 
Automotive Systems', if I'm correct, these are bluetooth tyre pressure sensors
which allow remote inquiries!

Graphing by class shows a similar story to last year as well, although the
proportion of 'smart' phones and hands free devices has increased.

![Bluetooth Class Frequencies](/images/posts/jan2011_by_class.png)

Finally, since this years' data contains lots of timestamps, I decided to
create a time series, showing which classes were visible at any given time.
Here's a time series I made by binning the results into 30 minute intervals:

![Bluetooth Class Frequencies](/images/posts/jan2011_class_time_series.png)

You can clearly see the daily cycle, and it's pretty easy to tell when there's
most traffic.

I haven't yet looked at how many of these devices I saw more that once.
Bluetooth represents a large and (I believe) completely untapped source of
potential tracking data. If I can see and uniquely identify <i>at least</i> one
device per minute from my living room, what could a network of bluetooth
enabled CCTV cameras, distributed throughout a city see? At the very least,
something like this could be used to automatically measure crowd density, and
at most it could be used to track individuals.

Mitigation: ensure your phone isn't discoverable! As more people shift to using
'Smart' phones, the risk of tracking drops, since these devices tend to not be
discoverable. Sat Navs and car accessories seem to be moving in the opposite
direction, which means that tracking cars gets easier whilst tracking people
gets harder.
