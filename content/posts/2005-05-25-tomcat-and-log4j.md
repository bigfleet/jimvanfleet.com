---
layout: post
title: Tomcat and Log4J
tags:
- Tech
status: publish
type: post
published: true
Date: 2005-05-25
---
I am a fan of both Tomcat and Log4J, and [this site](http://minaret.biz/tips/tomcatLogging.html#tomcat_5_0_logging) contains some good information on them both.

I specifically visited to find that placing `log4j.properties` into `common/classes` was the way to go to initialize Log4J inside of Tomcat.
