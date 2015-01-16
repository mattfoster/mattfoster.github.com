--- 
title: 'Avoid XSS in Template Toolkit'
categories: 
- perl
- xss
- template
layout: post
date: 2015-01-16
---

[Template Toolkit](http://www.template-toolkit.org/) is an excellent and popular templating language for [perl](https://www.perl.org/). 

Here's a quick tip about how to avoid [cross-site scripting vulnerabilities](http://en.wikipedia.org/wiki/Cross-site_scripting) when using it to write web apps.

Suppose you have a page in your app which takes some user input and displays it, like this:

    <input name="user_supplied_input" value='[% input | html %]'>
    
The input could come from POSTing a form, or from a URL parameter, like: 

    https://example.com/app?user_supplied_input=test
    
You could be forgiven for thinking that because you've used the [HTML filter](http://www.template-toolkit.org/docs/manual/Filters.html#section_html) you user supplied input will be safely encoded, but in this case you'd be wrong!

Generally, I find that Template Toolkit follows the [principle of least astonishment](http://en.wikipedia.org/wiki/Principle_of_least_astonishment), but read this snippet of the docs closely, and you might spot the issue:

> Converts the characters <, >, & and " to &lt;, &gt;,&amp;, and &quot; respectively, protecting them from being interpreted as representing HTML tags or entities.

That's right, it doesn't encode single quote characters! That means that all a malicious user needs to do to perform a cross-site scripting attack is escape out of the attribute using a single quote, and inject whatever they want.

One contrived example might be this:

    https://example.com/app?user_supplied_input='%20onmouseover=alert(1)
    
But a real attacker would obviously take the time to create a more awesome payload, or just use something like [BeEF](http://beefproject.com/). 

To avoid this, just make sure you **use double quotes in HTML tags** when building apps with Template Toolkit. 