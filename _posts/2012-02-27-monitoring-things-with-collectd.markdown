---
title: Monitoring Things with collectd 
categories: 
- monitoring
- power
- cacti
- collectd
- sysadmin
layout: post 
--- 

I've had a cacti server for some time, but I recently decided to experimnent with collectd. In this post, I'll talk about how I ported my CurrentCost montoring code to work with collectd.

## What's wrong with cacti?

For a home user who just wants to monitor my router, power usage, and the odd arduino controlled thermometer, cacti is fine, but the limitations are fairly obvious:

* Cacti is buggy – really buggy. I've seen it totally eat the device/graph tree when adding a new node, and had to restore the database table from a backup to fix it :S.
* Cacti is [pretty insecure](http://www.cvedetails.com/vendor/7458/Cacti.html "Cacti : Products and vulnerabilities"), there was even an SQL injection on the [login page](http://www.cvedetails.com/vulnerability-list/vendor_id-7458/year-2011/opsqli-1/Cacti.html "Cacti : Security vulnerabilities")!
* Cacti is written in PHP. 
* Cacti uses a central server, with a poller that runs out of a 5 minutely cronjob (by default). 
* Cacti is really hard to set up.

This contents of list are definitely enough to make me want to find an alternative.

## What's good about collectd?

collectd doesn't really replace [Cacti](http://www.cacti.net/ "Cacti: The Complete RRDTool-based Graphing Solution") (it has no real web interface), but it does fix lots of cacti's problems. In particular it allows you to create arbitrarily complex monitoring topologies (cool phrase!) in which your hosts push data to your monitoring servers rather than the other way around. It requires very little in the way of configuration (the network plugin listens for pretty much anything), is configured using text files (yay!), and you can stream as much data as you like to your monitoring server and it'll save pretty much all of it.

I haven't written about setting up monitoring with cacti in past, but actually grabbing data from something is usually the easy bit. To do that, you just need to write a script which outputs the information you want cacti to consume. The hard part is jumping through the hoops of adding your script to cacti. [Here's](https://gist.github.com/377704) an example script; you'll need to read cacti's docs to see how to hook your own scripts up.

Getting data into collectd can be a little more complex if you use the network plugin, because it expects you to use its own protocol. Thankfully, the [docs](http://collectd.org/documentation.shtml "Documentation &ndash; collectd &ndash; The system statistics collection daemon") are pretty good, and the [language and plugin](http://collectd.org/wiki/index.php/Table_of_Plugins "Table of Plugins - collectd Wiki") support is even better. 

## CurrentCost monitoring

I decided to port my CurrentCost monitoring script to collectd, and since the monitoring scripts I already have are written in ruby (and I'm lazy), I decided to use [ruby-collectd](https://github.com/astro/ruby-collectd), and [Daemons](http://daemons.rubyforge.org/ "Daemons").

The CurrentCost has an RJ11 socket on the back which is actually a serial port (at 57600 baud 8N1). CurrentCost sell adapters for these (mine has a Prolific PL203), so it's dead easy to plug the thing into a computer. I use the [serialport](http://ruby-serialport.rubyforge.org/ "Ruby-serialport") gem to connect to this and read the data.

Every six seconds, the CurrentCost monitor outputs a single line of XML, like this:

    <msg><src>CC128-v0.12</src><dsb>00656</dsb><time>13:43:51</time><tmpr>18.5</tmpr><sensor>0</sensor><id>00077</id><type>1</type><ch1><watts>01005</watts></ch1></msg>

My script uses `rexml/document` to parse this, on the off-chance that some of the other data could become useful in future. Accessing the parsed data is then done using xpath expressopns, like this:

    xml.elements['//tmpr'].text.to_f
    xml.elements['//ch1/watts'].text.to_f
	
The final step is sending the data to collectd, with the ruby-collectd gem. Thankfully, the gem has decent documentation, but if you've not done much with collectd you might find the examples frustrating, because they don't actually work! This is because the method call is dynamically converted to the type you want to record (using `method_issing`), and _not__ aribtrary. For example, in the expression:

    Stats.my_counter(:my_sleep).counter = 0

`my_counter` would be the _type_, and `my_sleep` the _name_. However, collectd's `types.db` doesn't know about `my_counter`, so this won't work. Instead, as I just hinted, you need to look in your collectd's `types.db` for something which sounds like what you're trying to measure, and use that as the method name above. In my config, I found:

    power                   value:GAUGE:0:U
	temperature             value:GAUGE:-273.15:U
	
Which looks perfect! So to stream the data to my collectd, I use:

    Collectd.add_server(interval=10)
    stats = Collectd.current_cost(:reader)
    stats.with_full_proc_stats
  
    stats.temperature(:temperature).gauge = xml.elements['//tmpr'].text.to_f
    stats.power(:power).gauge = xml.elements['//ch1/watts'].text.to_f

That covers most of the interesting parts of my monitoring script. Daemons is really easy to use, so I haven't mentioned that here - see the script for the gory details. The final (but still work in progress) script can be found below:
<script src="https://gist.github.com/1925015.js?file=current_cost.rb"></script>

To run it, use:

    ruby current_cost.rb start
	
And the magic of the Daemons library will be invoked. Finally, check your collectd's rrd directory to see if the data is being collected, then use something like the `collection3` frontend, or `rrdtool` to view some graphs!

<div class="thumbnail"><a href="https://skitch.com/mattfoster/8ff7q/collection.cgi-version-3"><img src="https://img.skitch.com/20120227-ku2em9bguc6h4fs2rdj6xkq1sa.preview.jpg" alt="collection.cgi, Version 3" /></a></div>