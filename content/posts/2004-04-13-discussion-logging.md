---
layout: post
title: ! 'Discussion: Logging'
tags:
- Development
status: publish
type: post
published: true
Date: 2004-04-13
---
## Why bother with commons-logging?

How does being able to select a logging configuration at startup-time benefit me?  For the writers of <a href="http://www.hibernate.org/">Hibernate</a>, it&#8217;s clear.  They have downstream users with their own logging needs.  For me, I don&#8217;t.  </p>

As long as I <a href="http://devblog.jimvanfleet.com/archives/000008.html">design to an interface</a>, I can remain relatively flexible with regard to logging on my own.  If I need to use a new logging system, or switch to use a future <span class="caps">JDK</span>&#8217;s logging implementation, I can just re-implement the interface.</p>

And it seems like I would be asking for trouble switching to it.  I&#8217;m getting better at resolving classpath issues, but they can be <strong>really</strong> tricky to track down at times anyway.</p>

[Apache Log4J](https://logging.apache.org/log4j/2.x/index.html) works quite well for me.  That&#8217;s what I&#8217;ll be using.</p>
