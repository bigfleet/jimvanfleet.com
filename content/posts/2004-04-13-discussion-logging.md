---
layout: post
title: ! 'Discussion: Logging'
tags: []
status: publish
type: post
published: true
meta: {}
---
<h2>Why bother with commons-logging?</h2>

<p>How does being able to select a logging configuration at startup-time benefit me?  For the writers of <a href="http://www.hibernate.org/">Hibernate</a>, it&#8217;s clear.  They have downstream users with their own logging needs.  For me, I don&#8217;t.  </p>

<p>As long as I <a href="http://devblog.jimvanfleet.com/archives/000008.html">design to an interface</a>, I can remain relatively flexible with regard to logging on my own.  If I need to use a new logging system, or switch to use a future <span class="caps">JDK</span>&#8217;s logging implementation, I can just re-implement the interface.</p>

<p>And it seems like I would be asking for trouble switching to it.  I&#8217;m getting better at resolving classpath issues, but they can be <strong>really</strong> tricky to track down at times anyway.</p>

<p><a href="http://logging.apache.org/log4j/docs/">Apache Log4J</a> works quite well for me.  That&#8217;s what I&#8217;ll be using.</p>
