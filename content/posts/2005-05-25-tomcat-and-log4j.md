---
layout: post
title: Tomcat and Log4J
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>I am a fan of both Tomcat and Log4J, and <a title="Logging for Apache Tomcat and Velocity using Log4j" href="http://minaret.biz/tips/tomcatLogging.html#tomcat_5_0_logging">this site</a> contains some good information on them both.</p>


	<p>I specifically visited to find that placing log4j.properties into common/classes was the way to go to initialize Log4J inside of Tomcat</p>
