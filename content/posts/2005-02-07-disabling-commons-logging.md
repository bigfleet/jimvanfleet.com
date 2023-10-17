---
layout: post
title: Disabling Commons Logging
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>I&#8217;ve developed a suite of test cases for my latest application.  In my architecture, I want to make sure that each of the implementations for each of my interfaces passes the test cases as part of the build process.  I accomplish this goal using Spring configuration and a little property file maintainance.</p>


	<p>As a result, however, following the unit test execution was absolutely impossible.  Thanks to <a title="Spring Framework :: View topic - Dealing with XML config maintenance" href="http://forum.springframework.org/viewtopic.php?t=2592&#38;highlight=disable log">this post</a> on the Spring forum, I discovered the key to disabling commons-logging is to set a system property.  It was a slam-dunk after that to <a href="http://blog.ideoplex.com/software/2003/07/11.html">change a system property using Ant</a>.  Fortunately, the JUnit Ant task accepts this property!</p>
