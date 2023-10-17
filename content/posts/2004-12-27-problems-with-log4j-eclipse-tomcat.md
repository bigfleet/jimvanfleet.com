---
layout: post
title: Problems with Log4j, Eclipse, Tomcat
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>I&#8217;m in the process of setting up the environment for my new web application.  When I tried to install and use log4j logging in my project, nothing worked!  I use Eclipse and the Sysdeo Tomcat plugin to start Tomcat, and placing my log4j jar in various locations throughout the server proved to have no effect.  The problem was that I had selected the option for Sysdeo Tomcat to provide my Eclipse project&#8217;s library information to the Tomcat classpath.  Commons-logging then had a collision with Log4j.  My solution was to remove commons-logging from my application classpath within Eclipse.  When I deploy this application, there may be more to say about this issue.</p>
